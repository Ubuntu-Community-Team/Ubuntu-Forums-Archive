---
title: "help setting up lm-sensors"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by NewbuntuUser777 on 2011-06-28
I'm a bit new to lm-sensors and having a hard time getting it working.

I installed most recent version of lm-sensors, and ran most recent version of sensors-detect.

It finds coretemp

```
 
Intel digital thermal sensor...                             Success!
    (driver `coretemp')

```

And nuvoton

```

Found `Nuvoton NCT6776F Super IO Sensors'                   Success!
    (address 0x290, driver `w83627ehf')

```

Awesome!  So I tell sensors detect to generate /etc/sysconfig/lm_sensors

Then I run sensors, "No sensors found!"


Anyone know what the next step is?

Thanks!

---

### Post by Ozymandias_117 on 2011-06-28
```
sudo modprobe coretemp
sudo modprobe nuvoton
```

To make them get added during boot, add coretemp and nuvoton to /etc/modules

---

### Post by NewbuntuUser777 on 2011-06-29
The nuvoton driver can't be found.  I find a standalone driver on 
the lm-sensors website but I'm not sure how to install.

I downloaded the files here, 
[http://roeck-us.net/linux/drivers/w83627ehf/](http://roeck-us.net/linux/drivers/w83627ehf/)

I tried to "make install" them but I get errors,

```

cp: cannot stat `w83627ehf.ko': No such file or directory

```

I looked at the make file and it's looking for a .ko file.

```

modules_install:
	cp $(DRIVER).ko $(KERNEL_MODULES)/kernel/$(MOD_SUBDIR)
	depmod -a -F $(SYSTEM_MAP) $(TARGET)

```


This is a beginner question I guess.  How do I get a .ko file?

Any help?

(Oh, and big thanks to Ozymandias_117!)

---

### Post by b@sh_n3rd on 2011-06-29
As it's probably self evident to you, the kernel driver for that piece of hardware is missing. It seems that kernel 2.6.39 (the latest stable release) actually includes the driver now, but it's a little tricky to install another kernel in Ubuntu. Instead, you can try the instructions here:

[https://wiki.archlinux.org/index.php/Lm_sensors#Asus_P8P67.2C_Intel_dh67cf_motherboard](https://wiki.archlinux.org/index.php/Lm_sensors#Asus_P8P67.2C_Intel_dh67cf_motherboard)

...to try and install the driver. If that doesn't work, you might consider installing kernel2.6.39 beside the stock kernel if no alternative pops up...but I doubt you'd have to do that :) Pray this helps :)

**EDIT:** Here's an older thread: [http://ubuntuforums.org/showthread.php?t=424302](http://ubuntuforums.org/showthread.php?t=424302)
dunno if that'll say much but I just thought I'd link it. The link I pasted first should be of more use to you in terms of a permanent solution, imo.

---

### Post by NewbuntuUser777 on 2011-06-29
Thanks to all.  I was having trouble installing the driver, but I got it sorted.

When I ran make on the w83627ehf makefile, I got the error:

```

fatal error: linux/autoconf.h: No such file or directory
```

So then I found the following link
[http://forums.virtualbox.org/viewtopic.php?f=7&t=38584](http://forums.virtualbox.org/viewtopic.php?f=7&t=38584)

which suggested symlinking the file as so:
```

ln -s /usr/src/linux-headers-`uname -r`/include/generated/autoconf.h /usr/src/linux-headers-`uname -r`/include/linux/autoconf.h

```

Ran the following:
```

make
make install
modprobe w83627ehf
sensors 

```


```

nct6776-isa-0290
Adapter: ISA adapter
in0:           +0.95 V  (min =  +0.00 V, max =  +1.74 V)
in1:           +1.87 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in2:           +3.42 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in3:           +3.41 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in4:           +0.09 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:           +1.69 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in7:           +3.47 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in8:           +3.28 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
fan1:         1012 RPM  (min =    0 RPM)  ALARM
fan2:            0 RPM  (min =    0 RPM)  ALARM
SYSTIN:        +28.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:        +28.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN:        +49.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0:  +32.5°C  
cpu0_vid:     +2.050 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +33.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +31.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:       +33.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:       +31.0°C  (high = +80.0°C, crit = +98.0°C)

```


SUCCESS!!!

---

