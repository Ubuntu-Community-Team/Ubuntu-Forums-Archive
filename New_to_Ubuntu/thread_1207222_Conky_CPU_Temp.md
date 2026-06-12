---
title: "Conky CPU Temp"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by pkjm17 on 2009-07-07
How do you get to display the CPU & system temperature in Conky? What is the file or script you use and the code you put in conky?

---

### Post by sailthesea on 2009-07-07
This should get you a CPU temp reading I don't know how to tie it into conky though if you work it out let me know I'm building mine at the moment:p
 sudo apt-get install lm-sensors

 Or try and sift through the conky post here 
[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

---

### Post by pkjm17 on 2009-07-08
I installed lm-sensors, however I can't get an output in the terminal. This is what it says when I put in 'sensors' 

No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

I did sensors-detect and answered yes to all the questions. Any idea on how to get the sensors to work?

---

### Post by Mark Phelps on 2009-07-09
> **pkjm17 said:**
> Any idea on how to get the sensors to work?
If you did "sudo sensors-detect" and answered all the questions and you still get "no sensors found", that's the end of it!  There's no way to "force" the sensors to work; either they're detected or they're not.  I have a recent tablet PC and can not get any temp or fan readings, regardless of the OS and utilities that have been tried.

---

### Post by pkjm17 on 2009-07-11
GRRRRRR this is frustrating me. Maybe it just won't work, I don't know. Anyway, this is what I've done. Did I do it correctly?

pat@pat-desktop:~$ sudo sensors-detect
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): YES
Probing for PCI bus adapters...
Use driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600 SMBus

We will now try to load each adapter module in turn.
Module `i2c-piix4' already loaded.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-0)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x4a
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x4b
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6650/MAX6651'...                      Success!
    (confidence 3, driver `max6650')
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (YES/no/selectively): YES

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): YES
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      Yes
Found unknown chip with ID 0x8720
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): YES
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  Success!
    (driver `to-be-written')
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `max6650' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter '
    Busdriver `UNKNOWN', I2C address 0x4b
    Chip `Maxim MAX6650/MAX6651' (confidence: 3)

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Chip `AMD K10 thermal sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
max6650
# no driver for AMD K10 thermal sensors yet
#----cut here----

Do you want to add these lines automatically? (yes/NO)yes
pat@pat-desktop:~$ sudo modprobe max6650
pat@pat-desktop:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

---

### Post by bobo38_fr on 2009-07-23
I have the same motherboard with Phenom II 720 BE...

No information for System temperature and Voltage

BUT

I've managed to have my Phenom temperature with k10 temp thanks
- [http://ubuntuforums.org/showthread.php?p=7629005]("http://http//ubuntuforums.org/showthread.php?p=7629005")  #3
- [http://ubuntuforums.org/showthread.php?t=1003916&page=2](http://ubuntuforums.org/showthread.php?t=1003916&page=2)  #13

```
22:48 bobo@ ~% sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +31.4°C 
```So it seems the is a 'way to "force" the sensors to work' for CPU. Hope I have helped you !

I'm now searching for system voltage / fan / temperature... And for my Radeon HD 4850 : [http://ubuntuforums.org/showthread.php?t=952374](http://ubuntuforums.org/showthread.php?t=952374) (people are making really great things, but little issue with 64bits)

Really hard to deal with that kind of things ! Did you manage to have information ? sensors-detect gives me really no solution in standard. I am really interested in voltage and fan control for undervolting test... 

```

22:29 bobo@ ~% sudo sensors-detect
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600 SMBus

We will now try to load each adapter module in turn.
Module `i2c-piix4' already loaded.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      Yes
Found unknown chip with ID 0x8720
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  Success!
    (driver `to-be-written')
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Chip `AMD K10 thermal sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
# no driver for AMD K10 thermal sensors yet
#----cut here----

Do you want to add these lines automatically? (yes/NO)n

```

---

### Post by pkjm17 on 2009-07-25
Hey bobo,

I'm having a little trouble here following the instructions for the k10temp.c from the link you posted (the second one). When I do "make -C /lib/modules/$(uname -r)/build M=$(pwd) modules" I get this 

"make: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
scripts/Makefile.build:41: /home/pat/Makefile: No such file or directory
make[1]: *** No rule to make target `/home/pat/Makefile'.  Stop.
make: *** [_module_/home/pat] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'"

What exactly did you do for yours?

---

### Post by Xerran on 2009-08-08
> **pkjm17 said:**
> GRRRRRR this is frustrating me. Maybe it just won't work, I don't know. Anyway, this is what I've done. Did I do it correctly?

pat@pat-desktop:~$ sudo sensors-detect
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): YES
Probing for PCI bus adapters...
Use driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600 SMBus

We will now try to load each adapter module in turn.
Module `i2c-piix4' already loaded.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-0)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x4a
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x4b
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6650/MAX6651'...                      Success!
    (confidence 3, driver `max6650')
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (YES/no/selectively): YES

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): YES
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      Yes
Found unknown chip with ID 0x8720
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): YES
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  Success!
    (driver `to-be-written')
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `max6650' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter '
    Busdriver `UNKNOWN', I2C address 0x4b
    Chip `Maxim MAX6650/MAX6651' (confidence: 3)

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Chip `AMD K10 thermal sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
max6650
# no driver for AMD K10 thermal sensors yet
#----cut here----

Do you want to add these lines automatically? (yes/NO)yes
pat@pat-desktop:~$ sudo modprobe max6650
pat@pat-desktop:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.


You have the same CPU and motherboard as me and I would like to know how you got on. I would like a conky script that supports temps for quad core cpu's and Radeon gpu's.

---

### Post by bruno9779 on 2009-11-30
There is a fix I have found [here]("http://http://blog.morrigan.ch/?p=9")

> Step for step (I’m not sure if this the newest k10temp version!):

$ wget [http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin](http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin)
$ mkdir k10temp && mv attachment.bin k10temp/k10temp.c

Now create the Makefile with following lines:

    obj-m := k10temp.o
    KDIR := /lib/modules/$(shell uname -r)/build
    PWD := $(shell pwd)
    default:
    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

$ make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
$ cp k10temp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon
$ depmod && modprobe k10temp

Enjoy it!

It workes fine for me.

I have yet to test it when the CPU is under heavy load, and to test the alarms, but sensors-applet is working fine, and the readings are consistent with the CPU load.

One thing only puzzles me: I get one sensor only for a 3 core?

---

