---
title: "temperatures"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by albert s on 2010-03-17
I have installed the temperature thingie in my top bar, 
but only my graphics card temp ever changes, how do I know if I have sensors on my chip or not?
it constantly stays at 40c 40c , I assume that is because its dual core (2 read outs)
thanks.

---

### Post by GSF1200S on 2010-03-17
> **albert s said:**
> I have installed the temperature thingie in my top bar, 
but only my graphics card temp ever changes, how do I know if I have sensors on my chip or not?
it constantly stays at 40c 40c , I assume that is because its dual core (2 read outs)
thanks.

To get temperature readings, you usually need to install lm-sensors:
```
sudo apt-get install lm-sensors
```

Then you need to run sensors-detect:
```
sudo sensors-detect
```
It will ask you if you want to add these sensors- tell it yes.

You will need to load the coretemp module:
```
sudo modprobe coretemp
```

Then open a terminal and type:
```
sensors
```
and see what it outputs. After doing this, you should be able to see temps in your panel applet. :)

---

### Post by albert s on 2010-03-17
all seemed to be going good

#I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
w83627ehf
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)yes
mark@mark-desktop:~$ sudo modprobe coretemp
mark@mark-desktop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +60.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +37.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +38.0°C  (high = +74.0°C, crit = +100.0°C)  



but nothing changed in my applet,
what have I done wrong?  :(

---

### Post by audiomick on 2010-03-17
Hi Albert.
I just did that. The changes didn't show up until after I re-booted.
Then, when I did a right-click on the applet and looked at the preferences, I could choose about 10 more sensors than before.

---

### Post by GSF1200S on 2010-03-17
After restarting, you may again have to enter:

```
sudo modprobe coretemp
```

Im so used to Arch I havent gotten around to figuring out how to autoload modules on ubuntu :|

I should have mentioned as said above that you might need to go to preferences (of the applet) and configure it to deal with your sensors.

Good luck :)

---

### Post by audiomick on 2010-03-17
I don't think so. I didn't have to.
I think this bit
```
To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
w83627ehf
coretemp
#----cut here----
```
takes care of it. I think the addition to /etc/modules puts it all in line to get found at start-up. That is what made me think of re-starting, actually.

---

### Post by GSF1200S on 2010-03-17
> **audiomick said:**
> I don't think so. I didn't have to.
I think this bit
```
To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
w83627ehf
coretemp
#----cut here----
```
takes care of it. I think the addition to /etc/modules puts it all in line to get found at start-up. That is what made me think of re-starting, actually.

Strange, as I have a whole slew of sensors that work automatically. But for some reason, I have to manually load coretemp on boot (not that big of a deal obviously). With Arch I just add 'coretemp' to the rc.conf and its good to go. :confused:

---

### Post by albert s on 2010-03-17
thanks all, I found this via another thread.
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

seems to have worked for me, I now have 5 readings, 58,(my GFX card I think) 40(never changes) 37(varies, so a CPU?) 36(as before I assume), 40(never changes)

Im assuming the middle 2 are the CPU as they go up and down a few degrees as I do stuff, the outer 2 at 40 never move so perhaps sensors I dont have(?). and I assume the 1st is my graphics, it has always worked.
any pointers?
thanks.

---

### Post by albert s on 2010-03-17
this is what my preferences are showing

---

### Post by GSF1200S on 2010-03-17
> **albert s said:**
> thanks all, I found this via another thread.
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

seems to have worked for me, I now have 5 readings, 58,(my GFX card I think) 40(never changes) 37(varies, so a CPU?) 36(as before I assume), 40(never changes)

Im assuming the middle 2 are the CPU as they go up and down a few degrees as I do stuff, the outer 2 at 40 never move so perhaps sensors I dont have(?). and I assume the 1st is my graphics, it has always worked.
any pointers?
thanks.

Well trying to pin the temps can be a pain. However, where are you getting these readings youre telling us about?

```
sensors
```
should tell you what each temp is, or at least most of them. Try sensors and paste the output here :)

---

### Post by albert s on 2010-03-17
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +60.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +37.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +37.0°C  (high = +74.0°C, crit = +100.0°C)  



I have also posted a screenshot if it helps.

---

### Post by audiomick on 2010-03-17
@ GSF : just to be sure, what exactly does
```
sudo modprobe coretemp
```
do. What would I see after this that wasn't there before?


Oh, and by the way
Kawasaki rules!!;)

---

### Post by albert s on 2010-03-17
> **audiomick said:**
> @ GSF : just to be sure, what exactly does
```
sudo modprobe coretemp
```do. What would I see after this that wasn't there before?


Oh, and by the way
**Kawasaki** rules!!;)


no no no,
YPVS,   :p ;)
 I can do a temp probe on them OK, its just these modern computer trickery boxes that confuse me.

---

### Post by GSF1200S on 2010-03-17
Silly silly people.. Suzuki rules you all ;)

The 'coretemp' module is responsible for returning temperatures of the processor cores, but NOT the cpu temperature itself. So for instance, take my outputs of sensors:

```
[poeticrpm@geekdom ~]$ sensors
atk0110-acpi-0
Adapter: ACPI interface
3.3V Voltage:          +3.28 V  (min =  +2.97 V, max =  +3.63 V)
5V Voltage:            +4.88 V  (min =  +4.50 V, max =  +5.50 V)
12V Voltage:          +12.14 V  (min = +10.20 V, max = +13.80 V)
CPU Voltage:           +0.98 V  (min =  +0.80 V, max =  +1.80 V)
CPU PLL Voltage:       +1.82 V  (min =  +1.50 V, max =  +2.00 V)
QPI/DRAM Core Voltage: +1.32 V  (min =  +0.80 V, max =  +1.50 V)
IOH Voltage:           +1.14 V  (min =  +0.90 V, max =  +1.35 V)
IOH PCIE Voltage:      +1.51 V  (min =  +1.20 V, max =  +1.80 V)
ICH Voltage:           +1.12 V  (min =  +0.90 V, max =  +1.35 V)
ICH PCIE Voltage:      +1.51 V  (min =  +1.20 V, max =  +1.80 V)
DRAM Bus Voltage:      +1.65 V  (min =  +1.40 V, max =  +1.90 V)
CPU FAN Speed:        1366 RPM  (min =  600 RPM)
CHA_FAN1 FAN Speed:   1380 RPM  (min =  600 RPM)
CHA_FAN2 FAN Speed:   1384 RPM  (min =  600 RPM)
CHA_FAN3 FAN Speed:   1318 RPM  (min =  600 RPM)
PWR_FAN FAN Speed:    1011 RPM  (min =  600 RPM)
OPT_FAN1 FAN Speed:    993 RPM  (min =  600 RPM)
OPT_FAN2 FAN Speed:      0 RPM  (min =  600 RPM)
OPT_FAN3 FAN Speed:   1048 RPM  (min =  600 RPM)
CPU Temperature:       +39.0°C  (high = +60.0°C, crit = +65.0°C)  
MB Temperature:        +37.0°C  (high = +45.0°C, crit = +55.0°C)  
SB Temperature:        +51.0°C  (high = +65.0°C, crit = +65.0°C)  
NB Temperature:        +51.0°C  (high = +80.0°C, crit = +80.0°C)  
OPT_FAN1 Temperature:   +0.0°C  (high = +45.0°C, crit = +45.0°C)  
OPT_FAN2 Temperature:   +0.0°C  (high = +45.0°C, crit = +45.0°C)  
OPT_FAN3 Temperature:   +0.0°C  (high = +45.0°C, crit = +45.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +51.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +50.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +49.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +49.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0004
Adapter: ISA adapter
Core 4:      +52.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0005
Adapter: ISA adapter
Core 5:      +52.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0006
Adapter: ISA adapter
Core 6:      +50.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0007
Adapter: ISA adapter
Core 7:      +49.0°C  (high = +80.0°C, crit = +100.0°C) 
```

The first part as you can see is all fan speed and voltages. You then see that the CPU itself is running 39 degrees celsius. At the bottom my coretemp temperatures are printing out. Since Im on a i7 920 with hyperthreading enabled, its returning temps for all 8 cores that the operating system sees.

---

### Post by audiomick on 2010-03-17
> **albert s said:**
> no no no,
[COLOR=Red]YPVS, [/COLOR]  :p ;)
 I can do a temp probe on them OK, its just these modern computer trickery boxes that confuse me.
nasty, loud, smelly, two stroke thingys.


Well, ok, they're fun too....;)
I like these
[http://en.wikipedia.org/wiki/Kawasaki_KH250/500/750](http://en.wikipedia.org/wiki/Kawasaki_KH250/500/750)

@GSF : yes, got that without anything more than a re-boot.

---

### Post by GSF1200S on 2010-03-17
> **albert s said:**
> sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +60.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +37.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +37.0°C  (high = +74.0°C, crit = +100.0°C)  



I have also posted a screenshot if it helps.

Im gonna guess that temp1 is your hard drive temperature, but I could be wrong. You could install hddtemp:
```
sudo apt-get install hddtemp
```

And see what it gives you as output. However, you ARE getting sensor output there, so its working :) You just need to edit the preferences on whatever widget youre using to ensure that it works with lm-sensors.

---

### Post by audiomick on 2010-03-17
@ GSF : what about one of these:
[ATTACH]150446[/ATTACH]

---

### Post by albert s on 2010-03-17
thanks gsf

mark@mark-desktop:~$ sudo apt-get install hddtemp
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hddtemp is already the newest version.
hddtemp set to manually installed.
The following packages were automatically installed and are no longer required:
  libtevent0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


if you look at my screenshot you may get an idea of the five readings I have,
2 and 5 never change from 40c, I have just rebooted and still the same,
Im not overly concerned, it seems like my CPU is OK anyhow, and I am going to add an extra fan to blow air in as soon as I get the chance, I have one spare from an old PC I had.

though it looks like this is veering off topic a little,  lol.

---

### Post by GSF1200S on 2010-03-17
> **audiomick said:**
> @ GSF : what about one of these:
[ATTACH]150446[/ATTACH]

Nice scooter :) Honestly, I like just about anything on 2 wheels in its own way. I have a leaning towards sport-touring bikes and dirtbikes, but ive had a blast on cruisers too.

Life is better on 2 wheels.. but we should prolly stay on topic ;)

---

### Post by GSF1200S on 2010-03-17
> **albert s said:**
> thanks gsf

mark@mark-desktop:~$ sudo apt-get install hddtemp
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hddtemp is already the newest version.
hddtemp set to manually installed.
The following packages were automatically installed and are no longer required:
  libtevent0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


if you look at my screenshot you may get an idea of the five readings I have,
2 and 5 never change from 40c, I have just rebooted and still the same,
Im not overly concerned, it seems like my CPU is OK anyhow, and I am going to add an extra fan to blow air in as soon as I get the chance, I have one spare from an old PC I had.

though it looks like this is veering off topic a little,  lol.

You already have hddtemp installed. You can tell by:
```
hddtemp is already the newest version.
```

Anyways, it seems logical to me that temp1 and cpu are the same thing, as temp1 doesnt seem to be anything else (like hard drive) and that seems to match the preferences dialog. I can tell by the up/down buttons on the right of the preferences that temp1 and cpu are the ones always reading 40. I dont know why you arent getting hddtemp on there. What is your ubuntu partition named in fdisk?
```
sudo fdisk -l
```

For example, one of my hard drives is /dev/sda. So, I can run:
```
sudo hddtemp /dev/sda1
```
and return:
```
/dev/sda1: ST32000542AS: 33°C

```

How about you?

---

### Post by audiomick on 2010-03-17
@ Albert : Yes, looks ok to me too. This is what I get
```
mick@ubuntu-desktop:~$ sensors
f71882fg-isa-0a00
Adapter: ISA adapter
3.3V:        +3.41 V
Vcore:       +1.06 V  (max =  +2.04 V)   
Vdimm:       +1.74 V
Vchip:       +1.28 V
+5V:         +5.08 V
12V:        +14.37 V
5VSB:        +4.79 V
3VSB:        +3.41 V
Battery:     +3.34 V
CPU:        1242 RPM
System:        0 RPM  ALARM
Power:         0 RPM  ALARM
Aux:           0 RPM  ALARM
CPU:         +37.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
System:      +37.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +37.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +38.0°C  (high = +80.0°C, crit = +100.0°C)  
```And the applet shows the graphics card and the two drives as well with 50 - 57°C for the graphics and 32°C and 36°C for the drives. The values for the drives don't change much. Maybe that is what your 40°C is? When you point the mouse at the icon in the task bar, does a name show up?

edit: you don't need to put a "1" on the end.
```
mick@ubuntu-desktop:~$ sudo hddtemp /dev/[COLOR=Red]sda[/COLOR]
/dev/sda: SAMSUNG HD082GJ: 32°C
```

/dev/sda is the drive
/dev/sda1 is the first partition on the drive.

---

### Post by albert s on 2010-03-17
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9250cd27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825        1958     1076355   82  Linux swap / Solaris
/dev/sda3            1959        9729    62420557+  83  Linux

then

mark@mark-desktop:~$ sudo hddtemp /dev/sda1
/dev/sda1: ST3802110AS: 40°C

the icons read as follows,
GPU
temp1
Core0
Core1
CPU

temp1 and CPU NEVER change, GPU is normally in the high 50's(a little high perhaps),
and the Core s  are around 32-37.

---

### Post by audiomick on 2010-03-17
I reckon temp 1 is more likely to be a drive or something
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  ([COLOR=Red]crit = +60.0°C[/COLOR])                  
```I think 60°C as the critical temp. is a bit low for a CPU. What do you think? And as I said, my drive temps are very stable, although I haven't been able to observe what happens when I do a large write operation.

edit: GPU is the graphics processor. As I said, mine runs around 55°C. That is a bit higher than I would have expected, but I don't find it alarming.

---

### Post by albert s on 2010-03-17
thanks audiomick, sets my mind at ease somewhat,
just, now that I have (to me at least) a good system I dont want to end up cooking it.
so can you tell me the difference between cores and CPU then? I thought the cores were a part of the CPU, Im confused now.

---

### Post by audiomick on 2010-03-17
Here is some reading (no, I haven't read it all the way through myself...;))
[http://en.wikipedia.org/wiki/Cpu](http://en.wikipedia.org/wiki/Cpu)
[http://en.wikipedia.org/wiki/Multi-core](http://en.wikipedia.org/wiki/Multi-core)

You could think of it like this:
Take a box and put a man with an abacus inside. The box is the CPU and the man with the abacus is the core.

Now take a box and put two men with an abacus each inside. The box is still a CPU, but now it has two cores.

You are right, the cores are part of the CPU.

EDIT: I should add that my real knowledge of the subject isn't much deeper than the analogy I just made...;)

---

### Post by GSF1200S on 2010-03-17
> **audiomick said:**
> @ Albert : Yes, looks ok to me too. This is what I get
```
mick@ubuntu-desktop:~$ sensors
f71882fg-isa-0a00
Adapter: ISA adapter
3.3V:        +3.41 V
Vcore:       +1.06 V  (max =  +2.04 V)   
Vdimm:       +1.74 V
Vchip:       +1.28 V
+5V:         +5.08 V
12V:        +14.37 V
5VSB:        +4.79 V
3VSB:        +3.41 V
Battery:     +3.34 V
CPU:        1242 RPM
System:        0 RPM  ALARM
Power:         0 RPM  ALARM
Aux:           0 RPM  ALARM
CPU:         +37.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
System:      +37.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +37.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +38.0°C  (high = +80.0°C, crit = +100.0°C)  
```And the applet shows the graphics card and the two drives as well with 50 - 57°C for the graphics and 32°C and 36°C for the drives. The values for the drives don't change much. Maybe that is what your 40°C is? When you point the mouse at the icon in the task bar, does a name show up?

edit: you don't need to put a "1" on the end.
```
mick@ubuntu-desktop:~$ sudo hddtemp /dev/[COLOR=Red]sda[/COLOR]
/dev/sda: SAMSUNG HD082GJ: 32°C
```

/dev/sda is the drive
/dev/sda1 is the first partition on the drive.

Yeah, I know- I was trying to illustrate that by using both in my example. Its better to just say it :). Although at this point I should share that different disks are denoted by a change in the name (For others knowledge):
/dev/sda
is a different drive then
/dev/sdb

For example, I have windows (which I never use) installed on /dev/sdb1 and ubuntu on /dev/sdb2. However, my /home is mounted on a different (set of) drive(s) /dev/sdc, while I have a backup on /dev/sda.

---

### Post by albert s on 2010-03-17
ok, thanks all you guys, GSF and audiomick.
its near my bed time now, but I'll let you know how I get on tomorrow.  :)

---

### Post by albert s on 2010-03-19
my reply

mark@mark-desktop:~$ sudo hddtemp /dev/sda
/dev/sda: ST380011A: 30°C
mark@mark-desktop:~$ 



but my screenshot still showing 40c.
also I added another little 2" fan sucking cool air in, and now my graphics ncard doesnt seem to get above 55c. dunno if this is good or not, should it be blowing air out?

---

