# Attention!

This hack was useful a long time ago (2006), it is only published to keep memory. Currently it is very easy to program a PIC with an arduino. Who would have thought it?

The images were made in Ms Paint :)

# PICSTART-16C RETRAIN

Programmer PICSTART-16C (released 1994) of Microchip was designed to program microcontrollers PIC16C64 and PIC16C74 using software for the almost extinct DOS, later was possible the programming of some other microcontrollers.

The programmer now is a relic, is governed by the microcontroller PIC17C42 who also is obsolete. But like all products of Microchip, this programmer has components of very good quality, so it is possible to transform this relic, in a useful programmer.

<p align="center"><img src=/images/pspc16-picstart16c.png></p>

<p align="center">Figure 1. – Microchip PICSTART-16C RETRAIN</p>

Programmer PICSTART-16C connects to the computer by serial port using adapter MAX232, the elevation of tension to enter the programming way does by means of the subsystem of regulation LM78S40, in addition these have on socket ZIF of 40 pins.

Socket ZIF is installed in order that only is possible the programming of devices of 40 and 28 pins after the recycling. However, elaborating an adapter ICSP the programming of an extensive variety of devices is possible.

The work of conversion is very simple, and requires few additional components:

* 1 Transistor BC548
* 1 Zener diode 5.1v
* 1 Resistance 1k ohm

The conversion of the programmer would not have sense if it is not have the appropriate software, this software fortunately exists, an option is WinPic800, created and maintained by Francisco Benach.

On the other hand, the use of the software IC-Prog, created and maintained by the equipment of Bonny Gijzen.

##### Conversion – Step 1.

Retire of the card the Q2 transistor (2907A) and in its place insert the transistor BC548 but with inverted position, this show in figures 2 and 3.

<p align="center"><img src=/images/pspc16-base.png></p>
<p align="center">Figure 2. – Original Transistor Q2: 2907A.</p>


<p align="center"><img src=/images/pspc16-BC548.png></p>
<p align="center">Figure 3. – New Q2 transistor: BC548.</p>

This new transistor will provide the capacity to control the tension of programming (13 volts) with logical levels of 0 and 5 volts obtained directly of adapter MAX232, its signal corresponding to TXD.

<p align="center"><img src=/images/pspc16-Q2.png></p>
<p align="center">Figure 3 BIS. – Change of transistor.</p>

##### Conversion – Step 2.

Insert in the programmer the circuit framed with red color of figure 4. This circuit is gotten up to obtain the data line PGDATA. This signal corresponds to DTR.

<p align="center"><img src=/images/pspc16-circuito.png></p>
<p align="center">Figure 4. – Zener Circuit</p>

Several ways exist to integrate this resistance and Zener diode to the programmer, one of them is show in figure 5.

<p align="center"><img src=/images/pspc16-zener.png></p>
<p align="center">Figure 5. – Integration of resistance and Zener diode.</p>


<p align="center"><img src=/images/pspc16-zeneric.png></p>
<p align="center">Figure 5 BIS. – Integration of the circuit.</p>

##### Conversion – Step 3.

Remove the microcontroller PIC17C42 and you make the connections that show with red color in figure 6.

* PIN 03 – PIN 34 – PIN 30
* PIN 38 – PIN 29
* PIN 10 – PIN 17
* PIN 18 – PIN 21 – PIN 22

<p align="center"><img src=/images/pspc16-conexiones.png></p>
<p align="center">Figure 6. – Marked additional Connections with red color.</p>


<p align="center"><img src=/images/pspc16-conexionesic.png></p>
<p align="center">Figure 6 BIS. – Additional Connections.</p>

If you decides to insert back the PIC17C40 to give a good aspect to the programmer, must in addition retire pins 1,3,17,18,21,22,29,30,32,34 and 38 of socket of 40 pins (see figure 7), since if he does not retire these pins and after the modifications insert back the microcontroller (old PIC17C40), the programmer did not work, because the PIC follows active, and therefore it will interfere with the new connections.

<p align="center"><img src=/images/pspc16-pinesout.png></p>
<p align="center">Figure 7. – Pins retired of socket 40.</p>

##### Conversion – Step 4.

Make the cut of the track that unites pin 8 with pin 12 of socket ZIF, this track is in the back part of the card, this show in the box red of figure 8.

<p align="center"><img src=/images/pspc16-corte.png></p>
<p align="center">Figure 8. – Court of the track between 8 pin and pin 12 of socket of the U5 unit.</p>

<p align="center"><img src=/images/pspc16-corteic.png></p>
<p align="center">Figure 8 BIS. – Court of track.</p>

# Software – WinPic800

Made the modifications, the disposition of lines RS232 will be as it is described in table 1.

<p align="center"><img src=/images/pspc16-signal.png></p>
<p align="center">Table 1. – Disposition of lines.</p>

Install the WinPic800 program, download the file <a href="/hwp/PICSTART-16C.hwp" target="_blank">PICSTART-16C</a>, copy in the /WinPic800/Hardware directory, go to the hardware configuration and select PICSTART-16C as it shows in figure 9.

<p align="center"><img src=/images/pspc16-winpic800.png></p>
<p align="center">Figure 9. – Configuration of software WinPic800.</p>

# Tests – PICSTART-16C RETRAIN

In the same screen that is in figure 8 it finds the function TEST to verify the operation of each one of the lines of the programmer.

Verify that the levels of tension of each line are approximately within the rank of table 2. The lines are arranged as it is in figure 10.

<p align="center"><img src=/images/pspc16-rangos.png></p>
<p align="center">Table 2. – Levels of tension.</p>

The DataIn line is associate directly with line Data so the state of the line can review its operation when modifying Data.
After verifying that the tensions are within the rank of table 2, it inserts some PIC of 40 or 28 pins in socket ZIF as one is in figure 10 and it proves the options to detect device, to read, to program, to verify and to erase.

<p align="center"><img src=/images/pspc16-ZIFpos.png></p>
<p align="center">Figure 10. – Disposition of lines and position of devices.</p>

If everything is satisfactory it has been able to recycle a good programmer. This recycling was verified completely using devices PIC18F452, PIC18F4520, PIC18F4550, PIC18F4520, PIC18F2550, PIC16F77, PIC16F877A, PIC16F876A and with the aid of adapter ICSP also PIC16F84, PIC16F84A, PIC12F675 and PIC12F683 were used.

# ICSP In-Circuit Serial Programming

Due to the connection of socket ZIP, single it is possible to program devices of 40 and 28 pins, but an adapter ICSP can be constructed to make the programming possible of the devices supported by WinPic800. Solde in a base for integrated circuit of 24 pins the interest signals,
but must incorporate a capacitor of 0.1uF between GND and VPP as it is in figure 11.

Or simply it places the conductors in socket ZIP when therefore requires it, but without forgetting the capacitor.

<p align="center"><img src=/images/pspc16-ICSP.png></p>
<p align="center">Figure 11. – Adapter ZIF-ICSP.</p>

By the limitation of current of the programmer, it avoids to connect VDD to the system where is the device to program, the connection can do it as it is in the diagram of figure 12.

<p align="center"><img src=/images/pspc16-diagrama.png></p>
Figure 12. – Diagram of connections ICSP.

# Power supply

Is essential that the power supply is the one that provides Microchip or at least with the electrical characteristics of this, since the programmer does not have regulation of entrance tension.

The programmer requires a source of +9 volts +/- 10% @ 500 mA (max), with positive center of 2.5 mm.

*If he does not count on the original source or equivalent*, he makes the following change to be able to use some other source with more than 9 and less than 20 volts.

A voltage regulator 7809 will be necessary and the form to incorporate it is described next:

##### 1. Remove the rectifying bridge CR1 and makes a small perforation as it is noticeable with red color in figure 13.

<p align="center"><img src=/images/pspc16-perforacion.png></p>
<p align="center">Figure 13. – Position of rectifying bridge CR1 and small perforation.</p>

##### 2. Inserts and weld the regulator 7809 with the position shown in figure 14.

<p align="center"><img src=/images/pspc16-7809.png></p>
<p align="center">Figure 14. – Position of regulator 7809.</p>

<p align="center"><img src=/images/pspc16-7809Dic.png></p>
<p align="center">Figure 14 BIS. – Position and weld of regulator 7809.</p>

##### 3. Make a bridge (a simple wire) between remain orifices, as it is in figure 15.

<p align="center"><img src=/images/pspc16-puente.png></p>
<p align="center">Figure 15. – Bridge between leftover orifices.</p>

<p align="center"><img src=/images/pspc16-7809ic.png></p>
<p align="center">Figure 15 BIS. – Regulating 7809 and bridge.</p>

##### 4. Connects and reviews the levels of tension in the R4 resistance, the tension in this resistance will have to agree with its labels GND and +9V.

##### 5. Enjoy! 


