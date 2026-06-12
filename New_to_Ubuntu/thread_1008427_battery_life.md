---
title: "battery life"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by jannevanhecke on 2008-12-11
i have a hp pavilion 6550eb and i installed ubuntu.
My battery life is only about 45 minutes and in windows it was 2 hours.
Ubuntu says my battery is broken.
Can anyone help?

---

### Post by jannevanhecke on 2008-12-11
nobody?

---

### Post by Kareeser on 2008-12-11
Is it only detecting the wrong time? As in, after 45 minutes, does the laptop indeed die?

We'll need more info... could be anything, from the processor not dialing down while on battery... etc

---

### Post by jannevanhecke on 2008-12-11
yes the laptop dies after 45 minutes. What more info doe you want?

---

### Post by uarale on 2008-12-11
post the outcome of the following command:
$ cat /proc/acpi/battery/BAT1/info

that's the info about your battery status.

---

### Post by jannevanhecke on 2008-12-11
janne@janne-laptop:~$ $ cat /proc/acpi/battery/BAT1/info
bash: $: command not found
janne@janne-laptop:~$ cat /proc/acpi/battery/BAT1/info
cat: /proc/acpi/battery/BAT1/info: No such file or directory

---

### Post by karlr42 on 2008-12-11
```
cat /proc/acpi/battery/BAT0/info
```
The output will show us what the designed capacity of the battery is versus it's charge last time it was fully charged.
Don't know why the previous poster said BAT1, you always count from zero in computing.

---

### Post by uarale on 2008-12-11
Don't know why it's BAT1 on my machine,not BAT0.

Anyway, jannevanhecke, when you type to $ cat /proc/acpi/battery/BAT try to press [TAB] and it will auto complete the right number.

---

### Post by LowSky on 2008-12-11
> **uarale said:**
> Don't know why it's BAT1 on my machine,not BAT0.


Some machines can accept two batteries at the same time, My dell Inspiron 8100 is an example of this, the is BAT1 and 0, BAT1 is actually used as defualt layout, BAT0 uses the same spot as my my floppy drive it kinda cool to have that kind of swapable space. It just depends on the layout of the computer. Your BIOS may actually name it BAT1 from the get go.

---

### Post by jannevanhecke on 2008-12-11
present:                 yes
design capacity:         6000 mAh
last full capacity:      1536 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 82 mAh
design capacity low:     50 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

---

### Post by linux_tech on 2008-12-11
Some suggestions to conserve battery:

Make sure laptop-mode is started:
```
sudo laptop-mode start
``` 

Decrease display brightness
Turn wireless switch to off if your not using a wireless connection
Stop unnecessary processes, turn off any applications not being used
Remove your battery when working with AC power 

This article will show you some for power management settings ideas such as installing powertop to conserve battery power.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_battery_life&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_battery_life&num=1)

---

### Post by karlr42 on 2008-12-11
> **jannevanhecke said:**
> 
design capacity: 6000 mAh
**last full capacity: 1536 mAh**
Based on that I'd have to say your battery is on the way out. Probably time to get a new one.

---

### Post by jannevanhecke on 2008-12-11
but it only began when i switched to ubuntu, my attery life was much longer on windows

---

### Post by jannevanhecke on 2008-12-11
janne@janne-laptop:~$ sudo laptop-mode start
[sudo] password for janne: 
sudo: laptop-mode: command not found

---

### Post by uarale on 2008-12-11
you need to install the package ubuntu-laptop-mode
$ sudo apt-get install ubuntu-laptop-mode

-------------------

Sorry, i was wrong. ubuntu has laptop-mode-tools installed by default. all you need to do is opening the file /etc/default/acpi-support, then change the value of ENALBE_LAPTOP_MODE to true. You may need to restart the computer.
Check the laptop mode: $ cat /proc/sys/vm/laptop_mode, if the value is 0 then the laptop_mode is disabled.

---

### Post by jannevanhecke on 2008-12-11
i just installed it but still get;

janne@janne-laptop:~$ sudo laptop-mode start
sudo: laptop-mode: command not found

---

### Post by uarale on 2008-12-11
No, in Ubuntu you can't run that command. Maybe it can be used in other distros.
Read this: [http://www.cyberciti.biz/faq/linux-laptop-power-saving/](http://www.cyberciti.biz/faq/linux-laptop-power-saving/)

If you've just installed ubuntu-laptop-mode, the package laptop-mode-tools must be removed!
Now you reinstall it: $ sudo apt-get install laptop-mode-tools

---

### Post by linux_tech on 2008-12-11
In Synaptic, add for installation the following packages: acpi, acpid, acpi-support, laptop-mode-detect, and laptop-mode-tools

then in terminal type

sudo gedit /etc/default/acpi-support

Set the line ENABLE_LAPTOP_MODE=true

Save, exit

---

### Post by gjoellee on 2008-12-11
you should try wattOS, which is based on Ubuntu and has a goal of making an energy efficient desktop which is light and fully functional.

[http://www.planetwatt.com/](http://www.planetwatt.com/)

---

### Post by uchari on 2008-12-27
```
uchari@uchari1:~$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         6000 mAh
last full capacity:      unknown
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 250 mAh
design capacity low:     150 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

```
this means that my battery died? because it doesn't last too much... no more than 30min...
can I force charging it?

---

