# Connect-an-LCD-to-an-Arduino-without-using-an-I2C-module
To connect an LCD to an Arduino without using an I2C module, you'll need to connect the LCD directly to the Arduino using its parallel interface. Below is a guide to help you achieve this:

**Hardware Required:**
- Arduino board (e.g., Uno, Mega, Nano)
- 16x2 or 20x4 LCD module with an HD44780-compatible controller
- 10kΩ potentiometer (for contrast adjustment)
- Resistors (optional, e.g., 220Ω for the backlight)
- Breadboard and jumper wires

**LCD Pin Description:**
Pin Name	Pin Number	Description
    VSS	1	Ground (GND)
    VDD	2	Power supply (5V)
    VO	3	Contrast adjustment (via a potentiometer)
    RS	4	Register Select (command/data mode)
    RW	5	Read/Write (connect to GND for write mode)
    E	6	Enable signal
    D0–D7	7–14	Data pins
    A	15	Backlight anode (connect to 5V via a resistor)
    K	16	Backlight cathode (connect to GND)

**Steps to Connect:**

**Power and Ground:**
Connect the LCD’s VSS to Arduino’s GND.
Connect the LCD’s VDD to Arduino’s 5V.

**Contrast Adjustment:**
Connect the middle pin of the potentiometer to the LCD’s VO pin.
Connect one side of the potentiometer to 5V and the other to GND.

**Backlight (Optional):**
Connect the LCD’s A (anode) pin to 5V via a 220Ω resistor.
Connect the LCD’s K (cathode) pin to GND.

**Control Pins:**
Connect RS (pin 4 on the LCD) to a digital pin on the Arduino (e.g., D7).
Connect RW (pin 5) directly to GND (for write mode).
Connect E (pin 6) to another digital pin on the Arduino (e.g., D8).

**Data Pins:**
Connect D4, D5, D6, and D7 of the LCD to four digital pins on the Arduino (e.g., D9, D10, D11, D12).
Leave D0–D3 unconnected for 4-bit mode.


**Arduino Code (Using LiquidCrystal Library):**

#include <LiquidCrystal.h>

    // Initialize the library with the numbers of the interface pins
    // (RS, E, D4, D5, D6, D7)

LiquidCrystal lcd(7, 8, 9, 10, 11, 12);

void setup() {

    // Set up the LCD's number of columns and rows:

lcd.begin(16, 2);
  // Print a message to the LCD

lcd.print("Hello, World!");
}

void loop() {
    // Do nothing here
}

**Notes:**
The code initializes the LCD in 4-bit mode. This reduces the number of pins required.
Adjust the potentiometer to set the contrast for the LCD.
If you're using a 20x4 LCD, change lcd.begin(16, 2) to lcd.begin(20, 4).
