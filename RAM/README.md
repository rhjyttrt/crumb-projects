# 16x16 Static RAM SRAM Circuit

A custom 16 word by 16 bit parallel Static RAM storage array designed inside the CRUMB Circuit Simulator. This architecture cascades multiple high speed 4 bit RAM chips to establish a unified wide 16 bit data bus managed by a manual synchronous address counter.

## Circuit Architecture

### 1 Memory Core RAM Matrix
* **Storage Array:** Composed of four 74F189 high speed SRAM chips aligned in parallel.
* **Bus Expansion:** Each individual 74F189 chip is configured as 16 addresses by 4 bits of data. Tying all four of their Address lines A0 to A3 and Write Enable lines together in parallel scales the data bus capacity up to a true 16 bit wide memory word.

### 2 Address and Control Logic
* **Address Counter:** A 4 bit synchronous binary counter tracks the active memory cell location cycling from address 0x0 to 0xF.
* **Tactile Inputs:**
  * **Clock Address Button:** Manually increments the counter to step sequentially through memory rows.
  * **Clear Address Button:** Instantly flushes the counter back to address 0x0.
* **Write Enable Toggle:** A physical slide switch manages logic states where LOW writes input states to memory and HIGH locks and protects stored bits.

### 3 Data Input and Inversion Correction
* **Data In:** A bank of 16 individual DIP switches handles the binary word layout to be saved into the current address row.
* **Output Inverters:** The 74F189 architecture inherently outputs inverted data on lines /O0 to /O3. To fix this the raw RAM read signals are routed through three 74HC04 Hex Inverter chips to invert the logic back to its true match before hitting the display.
* **Data Out Display:** A row of 16 color coded LEDs visually tracks stored data outputs in real time as you scan through memory locations.
