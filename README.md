# U8g2_for_Adafruit_GFX

Download: [https://github.com/olikraus/U8g2_for_Adafruit_GFX/archive/master.zip](https://github.com/olikraus/U8g2_for_Adafruit_GFX/archive/master.zip)

## What is U8g2_for_Adafruit_GFX?
 - Arduino Library
 - Adds a the [U8g2](https://github.com/olikraus/u8g2) text drawing engine to all Adafruit GFX based Arduino librarys.
 - All [U8g2 fonts](https://github.com/olikraus/u8g2/wiki/fntlistall) can be used 
 - Support for UTF-8 and Unicode
 - Support for Arduino print() command and F() Macro

U8g2 is a graphics library for monochrome displays. U8g2 supports many
displays, some of them are also supported by Adafruit GFX based libraries.
Others are supported by Adafruit GFX libraries, but are not supported by U8g2.
`U8g2_for_Adafruit_GFX` connects to an existing Adafruit Library and addes support for
U8g2 fonts to all Adafruit GFX based libraries.

## How to use U8g2_for_Adafruit_GFX?

This is a complete example for `U8g2_for_Adafruit_GFX` connected to Adafruit SSD1306 
library:

```
#include <Adafruit_SSD1306.h>
#include <U8g2_for_Adafruit_GFX.h>

Adafruit_SSD1306 display(/*MOSI*/ 11, /*CLK*/ 13, /*DC*/ 9, /*RESET*/ 8, /*CS*/ 10);
U8G2_FOR_ADAFRUIT_GFX u8g2_for_adafruit_gfx;

void setup() {
  display.begin(SSD1306_SWITCHCAPVCC);
  u8g2_for_adafruit_gfx.begin(display);                 // connect u8g2 procedures to Adafruit GFX
}

void loop() {  
  display.clearDisplay();                               // clear the graphcis buffer  
  u8g2_for_adafruit_gfx.setFontMode(1);                 // use u8g2 transparent mode (this is default)
  u8g2_for_adafruit_gfx.setFontDirection(0);            // left to right (this is default)
  u8g2_for_adafruit_gfx.setForegroundColor(WHITE);      // apply Adafruit GFX color
  u8g2_for_adafruit_gfx.setFont(u8g2_font_helvR14_tf);  // select u8g2 font from here: https://github.com/olikraus/u8g2/wiki/fntlistall
  u8g2_for_adafruit_gfx.setCursor(0,20);                // start writing at this position
  u8g2_for_adafruit_gfx.print(F("Hello World"));
  u8g2_for_adafruit_gfx.setCursor(0,40);                // start writing at this position
  u8g2_for_adafruit_gfx.print(F("Umlaut ÄÖÜ"));            // UTF-8 string with german umlaut chars
  display.display();                                    // make everything visible
  delay(2000);
} 
```

  
