# Data Logger (and using cool sensors!)

*A lab report by Vini Tripathii*

## In The Report

Include your responses to the bold questions on your own fork of [this lab report template](https://github.com/FAR-Lab/IDD-Fa18-Lab2). Include snippets of code that explain what you did. Deliverables are due next Tuesday. Post your lab reports as README.md pages on your GitHub, and post a link to that on your main class hub page.

For this lab, we will be experimenting with a variety of sensors, sending the data to the Arduino serial monitor, writing data to the EEPROM of the Arduino, and then playing the data back.

## Part A.  Writing to the Serial Monitor
 
**a. Based on the readings from the serial monitor, what is the range of the analog values being read?** 0 to 1023
 
**b. How many bits of resolution does the analog to digital converter (ADC) on the Arduino have?** 10 bits (2^10 = 1024)

## Part B. RGB LED

**How might you use this with only the parts in your kit? Show us your solution.** Video:

## Part C. Voltage Varying Sensors 
 
### 1. FSR, Flex Sensor, Photo cell, Softpot

**a. What voltage values do you see from your force sensor?** Ranges from 0 (no force) to 1023(5V -- output for large amounts of force).

**b. What kind of relationship does the voltage have as a function of the force applied? (e.g., linear?)** The relationship is logarithimic as a small change in force corresponds to a large change in voltage (increase).

**c. Can you change the LED fading code values so that you get the full range of output voltages from the LED when using your FSR?** video 1 -- using force sensor to fade LED:
video 2 -- using force sensor to change LED color (it was hard to control the force to show the different colors):
The key function was map(value, fromLow, fromHigh, toLow, toHigh), map allows you to change the value range.

**d. What resistance do you need to have in series to get a reasonable range of voltages from each sensor?** I used two 10K resistors for a total of 20K 

**e. What kind of relationship does the resistance have as a function of stimulus? (e.g., linear?)** Both are logarithimic though the in the photocell's case a linear approximation would also work well.

### 2. Accelerometer
 
**a. Include your accelerometer read-out code in your write-up.**

## Graphic Display

**Take a picture of your screen working insert it here!**

## Part D. Logging values to the EEPROM and reading them back
 
### 1. Reading and writing values to the Arduino EEPROM

**a. Does it matter what actions are assigned to which state? Why?** Yes, because if the "clear" action is state 1, the memory will be cleared on our way to read/write to memory.

**b. Why is the code here all in the setup() functions and not in the loop() functions?** Since only one operation (R/W/C) is performed at each switch state it would be inefficient to have everything in loop().

**c. How many byte-sized data samples can you store on the Atmega328?** 1024 bytes

**d. How would you get analog data from the Arduino analog pins to be byte-sized? How about analog data from the I2C devices?** Since the analog input ranges from 0 to 1023, and each byte of the EEPROM has a range of 0 to 255, divide by 4 or use the map function. For the I2C, data is sent in 8-bit bytes, and can be managed accordly. 

**e. Alternately, how would we store the data if it were bigger than a byte? (hint: take a look at the [EEPROMPut](https://www.arduino.cc/en/Reference/EEPROMPut) example)** If the data is too big for a single byte then multiple bytes should be used. The EEPROM procedures would have to be used several times


**Upload your modified code that takes in analog values from your sensors and prints them back out to the Arduino Serial Monitor.**

### 2. Design your logger
 
**a. Insert here a copy of your final state diagram.**

### 3. Create your data logger!
 
**a. Record and upload a short demo video of your logger in action.**
