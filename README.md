### STM32 TM1637 7-segment LED display library

This a tiny library to write to a TM1637 7-segment LED display from an STM32 MCU. Porting to other MCUs should be simple. Tested on [STM32L-DISCOVERY and 32L152CDISCOVERY](http://www.st.com/web/catalog/tools/FM116/SC959/SS1532/PF250990?sc=internet/evalboard/product/250990.jsp) boards. Based on the code example in the [TM1637 datasheet (Chinese)](http://www.seeedstudio.com/wiki/images/c/c3/TM1637_datasheet.pdf).

#### Usage

Example:

```
    tm1637Init();
    // Optionally set brightness. 0 is off. By default, initialized to full brightness.
    tm1637SetBrightness(3);
    // Display the value "1234" and turn on the `:` that is between digits 2 and 3.
    tm1637DisplayDecimal(1234, 1);
```

The `#define` statements in `stm32_tm1637.c` must be updated to match the actual port and pins to which the display is connected.

The `_tm1637DelayUsec()` has not been tuned to delay for the actual number of microseconds provided in the argument.

The library takes a shortcut in that it does not read back or act on the status values returned by the display. This could be a problem for use cases in which the display is written to only rarely.
