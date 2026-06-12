---
title: "cpu temp"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by tedygram311 on 2011-03-23
I am trying to figure out my cpus temperature.  I have followed guide  after guide with nothing except for a strange problem (below).  I know  that I can get it because I have gotten it on windows and I run arch on a  VM and have gotten it with that.  I recently had to reformat and  therefore lost that way of reading it.  Please help, this has baffled  many around me.


```

theodore@theodore-laptop:~$ lsmod|grep k10temp
k10temp                 2308  0 

theodore@theodore-laptop:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
theodore@theodore-laptop:~$ sudo sensors-detect
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: Hewlett-Packard HP Pavilion dv5 Notebook PC (laptop)
# Board: HP 30F2

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           Success!
    (driver `k10temp')
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600/SB700/SB800 SMBus
Module i2c-dev loaded successfully.

Now follows a summary of the probes I have just done.
Just press ENTER to continue: y

Driver `k10temp':
  * Chip `AMD Family 11h thermal sensors' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
k10temp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)n

Unloading i2c-dev... OK


```

---

### Post by tgm4883 on 2011-03-23
> To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
k10temp
#----cut here----

:EDIT:

Sorry, didn't see the first part there. I'd try reloading the module

```

modprobe -r k10temp
modprobe k10temp

```

---

### Post by Frogs Hair on 2011-03-23
Hi,
 
Try answering yes to each of  the questions as stated in the box  and run .```
sensors
```

---

### Post by tedygram311 on 2011-03-23
did both, no success.

---

### Post by Frogs Hair on 2011-03-23
I have read on other threads  that some newer hardware sensors don't work very well with lm-sensors. yours may be one of those cases. 

In case you haven't installed lm-sensors ```
sudo apt-get install lm-sensors
```

---

### Post by tedygram311 on 2011-03-23
I have installed it and it is totally updated

---

### Post by Hippytaff on 2011-03-23
Have you tried installing acpi and doing ```
acpi -t
```

---

### Post by tedygram311 on 2011-03-23
yup the only output I get is for my battery

```

$ acpi
Battery 0: Charging, 62%, rate information unavailable

```

---

### Post by Hippytaff on 2011-03-23
you have to use the[COLOR=Red] -t[/COLOR] flag ```
acpi [COLOR=Red]-t[/COLOR]
``````
$ acpi -t
Thermal 0: ok, 46.0 degrees C
Thermal 1: ok, 47.0 degrees C

```

---

### Post by tedygram311 on 2011-03-24
there is no output when I do that.  Yesterday I ran a fedora live cd and was able to get my temps so I know that it is possible with linux now.

---

### Post by Hippytaff on 2011-03-24
Try ```
acpi -V
``` Capital V. It should output everything

---

### Post by tedygram311 on 2011-03-24
New update: I updated kernels and I got it to work.

---

### Post by Frogs Hair on 2011-03-24
> **tedygram311 said:**
> New update: I updated kernels and I got it to work.
 
Strange !  glad your good to go.

---

### Post by tedygram311 on 2011-03-25
well the newer kernels messed everything up.  They were from mainline and therefore unsupported.  I would really prefer to get this done in the kernel I have now, because it is supported and I like it.  This is the output for acpi -u

```

$ acpi -v
acpi 1.4

Copyright (C) 2001 Grahame Bowland.
              2008 Michael Meskes.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

---

### Post by Hippytaff on 2011-03-25
you need a Capital V

---

### Post by matt_symes on 2011-03-25
Hi

@tedygram311. Just to let you know Ubuntu is case sensitive so...

This -> is different from
tHis -> is different from
ThiS -> .....
THIS -> .....

Therefore ```
acpi -v
``` is different from ```
acpi -V
```

Kind regards

---

### Post by tedygram311 on 2011-03-28
Thank you for the correction.  When I put that in ....
```

$ acpi -V
Battery 0: Charging, 26%, rate information unavailable
Battery 0: design capacity 6000 mAh, last full capacity 4576 mAh = 76%
Adapter 0: on-line
Cooling 0: LCD 0 of 10
Cooling 1: Processor 0 of 3
Cooling 2: Processor 0 of 10

```

---

