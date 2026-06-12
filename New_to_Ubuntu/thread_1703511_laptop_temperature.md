---
title: "laptop temperature?"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by SebSmith on 2011-03-09
linux novice.

how do i check the temperature on my laptop? comp in sig

---

### Post by maqtanim on 2011-03-09
In the terminal write the following command
```
**acpi -t**
```

---

### Post by SebSmith on 2011-03-09
> **maqtanim said:**
> In the terminal write the following command
```
**acpi -t**
```

nothing happens when i do that..

---

### Post by maqtanim on 2011-03-09
My bad. :P

First install the following package:
```
sudo apt-get install lm-sensors
```
Then run the following command
```
sudo sensors-detect
```
Write Y to all the questions, and then, to check the laptop temperature, type
```
sensors
```
or
```
acpi -t
```

---

### Post by dFlyer on 2011-03-09
Try sensors -f

---

### Post by maqtanim on 2011-03-09
By the way, If you want a graphical representation of the Temperature, then first Install the sensors-applet package
```
sudo apt-get install sensors-applet
```
Then right-click on the top/bottom panel and select "**Add to Panel**". Add the "**Hardware Sensors Monitor**" applet. Thus the temperature meter will be set into the panel. You can configure what it displays by right-clicking the applet and selecting "**Preferences**". 

A large number of Linux users prefer to use Conky for showing various info of their computers in the background. Take a look of some examples:
[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

But Conky setup required times. If you have time in your hand, you can try the following Conky setup in your computer:
[http://www.omgubuntu.co.uk/2011/03/follow-this-customization-guide-for-a-slick-ubuntu-desktop/](http://www.omgubuntu.co.uk/2011/03/follow-this-customization-guide-for-a-slick-ubuntu-desktop/)

---

### Post by SebSmith on 2011-03-09
none of this works. it says wrong kernal loaded or none loaded, this is common on laptops. it is probably controlled by acpi

acpi -t

returns nothing. just next line awaiting new command follows..

---

### Post by ghostborg on 2011-03-09
For me, the applets did not start working until I restarted my computer.

---

### Post by SebSmith on 2011-03-09
for whatever reason the applet displays "no sensors found!"

i did everything as instructed. what do i do? :(

---

### Post by Rasa1111 on 2011-03-09
I dont know if you use AWN or not..
But there is a nice temperature gauge applet for AWN.

(see the very bottom of my AWN dock/panel)
Currently @ 57 C

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=185602&stc=1&d=1299720430[/IMG]

and if you click it, it will give readouts from other sensors as well.

---

### Post by jcolyn on 2011-03-09
> **maqtanim said:**
> In the terminal write the following command
```
**acpi -t**
```

acpi has to be installed first.

```
sudo apt-get install acpi
```

---

### Post by SebSmith on 2011-03-09
> **jcolyn said:**
> acpi has to be installed first.

```
sudo apt-get install acpi
```


i do have it installed. i even reinstalled it and still not working

---

### Post by libssd on 2011-03-09
> **SebSmith said:**
> linux novice.

how do i check the temperature on my laptop? comp in sig

The solutions described don't work with all hardware. Although I have installed the software, I always get a reading of 26.8 degrees C, which is absurd.

---

### Post by jcolyn on 2011-03-09
> **SebSmith said:**
> i do have it installed. i even reinstalled it and still not working

If you have not already done so install lm-sensors. ```
sudo apt-get install lm-sensors
```

Next in a terminal enter ```
sudo sensors-detect
```

enter yes (not "y") to each question except for the one that instructs you to hit enter. Close the terminal and reboot the computer.

Once back up in the terminal enter ```
sensors
``` note sudo is not needed for this command.. It should then give a readout of all sensors detected..

---

### Post by jcolyn on 2011-03-09
> **libssd said:**
> The solutions described don't work with all hardware. Although I have installed the software, I always get a reading of 38 degrees C, which is absurd.

38 degrees C is normal. Most cpu's should run between 30-40 degrees C when idle and will only increase when a load is put on it..

Normal loads usually won't increase the temp more than 10-15 C..

---

### Post by SebSmith on 2011-03-09
> **jcolyn said:**
> If you have not already done so install lm-sensors. ```
sudo apt-get install lm-sensors
```Next in a terminal enter ```
sudo sensors-detect
```enter yes (not "y") to each question except for the one that instructs you to hit enter. Close the terminal and reboot the computer.

Once back up in the terminal enter ```
sensors
``` note sudo is not needed for this command.. It should then give a readout of all sensors detected..

here is what i got:

# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: Hewlett-Packard HP ENVY 14 Notebook PC (laptop)
# Board: Hewlett-Packard 1437

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0x8502
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Found unknown SMBus adapter 8086:3b30 at 0000:00:1f.3.
Sorry, no supported PCI bus adapters found.

Sorry, no sensors were detected.
This is relatively common on laptops, where thermal management is
handled by ACPI rather than the OS.

---

### Post by libssd on 2011-03-09
> **jcolyn said:**
> 38 degrees C is normal. Most cpu's should run between 30-40 degrees C when idle and will only increase when a load is put on it..

Normal loads usually won't increase the temp more than 10-15 C..

I mis-typed, and have corrected the error: 26.8C/81F. The machine has been running for several days, and the bottom of the case is noticeably above body temperature.

**Update**: 55 minutes of continuous use later, and the temperature sensor still says 81 °F.

**Update**: 10 hours later, after sleeping overnight, with the house temperature turned down, it's still reporting 81 °F.

Now I remember why I uninstalled this software after installing it last year.

Hardware: Acer AA1 D150 netbook.

---

### Post by jcolyn on 2011-03-09
> **SebSmith said:**
> 
Sorry, no sensors were detected.
This is relatively common on laptops, where thermal management is
handled by ACPI rather than the OS.

I won't be able to help you since I don't use acpi.

Newer laptop tend to favor acpi over sensors.

---

### Post by SebSmith on 2011-03-09
well then how do i monitor my comp temperature with acpi?

---

### Post by SebSmith on 2011-03-09
nobody uses acpi?

---

### Post by maqtanim on 2011-03-10
You can try what [Rasa1111]("http://ubuntuforums.org/member.php?u=1029120") suggests (Comment no. 10) ... AWN should install all the necessary packages for you.

---

### Post by piquat on 2011-03-10
> **SebSmith said:**
> nobody uses acpi?

I just loaded it up.  Seems to display at least something for my laptop (Inspiron 1501):

```
acpi -V
Battery 0: Full, 100%
Battery 0: design capacity 8600 mAh, last full capacity 5838 mAh = 67%
Adapter 0: on-line
Thermal 0: ok, 48.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 110.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 85.0 degrees C
Cooling 0: LCD 0 of 7
Cooling 1: Processor 0 of 3
Cooling 2: Processor 0 of 10
```-V (capitol V) basically displays everything ('man acpi' for options)

Do you get anything out of
```
acpi -V
```

---

### Post by SebSmith on 2011-03-10
> **piquat said:**
> I just loaded it up.  Seems to display at least something for my laptop (Inspiron 1501):

```
acpi -V
Battery 0: Full, 100%
Battery 0: design capacity 8600 mAh, last full capacity 5838 mAh = 67%
Adapter 0: on-line
Thermal 0: ok, 48.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 110.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 85.0 degrees C
Cooling 0: LCD 0 of 7
Cooling 1: Processor 0 of 3
Cooling 2: Processor 0 of 10
```-V (capitol V) basically displays everything ('man acpi' for options)

Do you get anything out of
```
acpi -V
```


Battery 0: Charging, 76%, 00:20:29 until charged
Battery 0: design capacity 3822 mAh, last full capacity 3822 mAh = 100%
Adapter 0: on-line
Cooling 0: LCD 9 of 10
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10
Cooling 5: Processor 0 of 10
Cooling 6: Processor 0 of 10
Cooling 7: Processor 0 of 10
Cooling 8: Processor 0 of 10
Cooling 9: Fan 1 of 1

---

### Post by Rasa1111 on 2011-03-10
dang.

 Maybe pickup a nice chill mate for it,
just to be on the safe side? lol

I just picked up a sweet 'Targus' chill mat.. for 'new' laptop
and the laptop stays cool to the touch,
even using all resources. 
The internal fan doesnt even have to kick on most of the time. :D lol

I checked out the "vendetta online" game,
and that produced *a lot* of heat! :lol:
Movies/large videos as well.
but not now.

temp stays around 40-50/60ish C. 
 Better safe than melted CPU right? lol

---

### Post by SebSmith on 2011-03-10
is it possible my laptop doesnt have the capability of monitoring heat? how is this possible? i thought it was a safety feature so that if the laptop gets to critical heat it shuts itself down

---

### Post by libssd on 2011-03-10
> **SebSmith said:**
> is it possible my laptop doesnt have the capability of monitoring heat? how is this possible? i thought it was a safety feature so that if the laptop gets to critical heat it shuts itself down
Not likely. Does the fan come on or change pitch? If so, then a sensor is monitoring the operating temperature. It does on mine, even though the monitoring software always reports an operating temperature of 81 degrees.

---

### Post by SebSmith on 2011-03-10
yea and i even have 2 fans on this thing... why cant i monitor the temp?

---

### Post by SebSmith on 2011-03-27
im still unable to get a read on the temperature. any ideas?

---

### Post by SebSmith on 2011-03-27
ive been googling and im still not finding a solution

---

