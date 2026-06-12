---
title: "Is my computer in overheat?"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by mellouli on 2011-06-15
I have a hp compact 6830s laptop with ubuntu natty 11.4 i386 installed in 
I noticed that my fan runs all the time and doesn't stop at all only if (and that's extremely rare) when the temperature of cpus is 38 C
in terminal
```
ubuntu@natty:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +49.0°C  (crit = +110.0°C)
temp2:        +45.0°C  (crit = +256.0°C)
temp3:        +50.0°C  (crit = +112.0°C)
temp4:        +53.0°C  (crit = +105.0°C)
temp5:        +30.3°C  (crit = +112.0°C)
temp6:        +50.0°C  (crit = +110.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +47.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +45.0°C  (high = +105.0°C, crit = +105.0°C)

```and

```
ubuntu@natty:~$ top

top - 17:41:50 up  2:26,  3 users,  load average: 0.11, 0.14, 0.14
Tasks: 159 total,   1 running, 156 sleeping,   0 stopped,   2 zombie
Cpu(s): 10.8%us,  4.3%sy,  0.0%ni, 82.7%id,  2.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3062628k total,  2049372k used,  1013256k free,    49936k buffers
Swap:        0k total,        0k used,        0k free,  1524984k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1445 ubuntu    20   0  247m  42m  10m S   10  1.4   7:09.46 compiz             
 1447 ubuntu     9 -11  158m 8092 6704 S    6  0.3   6:30.77 pulseaudio         
  994 root      20   0  105m  67m  38m S    5  2.2  29:48.57 Xorg               
 1660 ubuntu    20   0  578m 176m  23m S    3  5.9  17:58.51 firefox-bin        
 8579 ubuntu    20   0 94700  10m 7028 S    3  0.4   0:07.36 gnome-terminal     
 8885 ubuntu    20   0  303m  92m  58m S    2  3.1   5:28.41 vlc                
 1428 ubuntu    20   0  115m 8964 4636 S    1  0.3   0:11.33 gnome-settings-    
 1466 ubuntu    20   0  134m  27m  11m S    1  0.9   0:21.21 nautilus           
 1709 ubuntu    20   0  180m  25m  12m S    1  0.8  13:42.02 plugin-containe    
  872 root      20   0 18020 1220  532 S    1  0.0   0:05.70 gdm-binary         
 1416 ubuntu    20   0  5308 2300  520 S    1  0.1   0:04.74 dbus-daemon        
 1421 ubuntu    20   0  9632 3088 1092 S    1  0.1   0:02.91 gconfd-2           
 1745 ubuntu    20   0 51200 2664 1688 S    1  0.1   0:05.72 unity-files-dae    
 8878 ubuntu    20   0 19052 8756 7164 S    1  0.3   0:28.05 xsensors           
11090 ubuntu    20   0  6272 1788 1384 S    1  0.1   0:04.71 wget               
   11 root      -2  19     0    0    0 S    0  0.0   0:22.21 rcuc1   
```And i noticed in any version of windows (and after using linux I hate windows so much)
the temperature doesn't surpass 36 c and my laptop is calm
what can I do

---

### Post by pqwoerituytrueiwoq on 2011-06-15
check the temp when you are using classic ubuntu 
[http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/](http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/)
does the fan sound louder when you run windows on it?

---

### Post by StrayEddy on 2011-06-15
Control your fans ;)

[http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu](http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu)

or

[http://www.garryconn.com/linux/how-to-control-cpu-and-case-fan-speeds-on-a-linux-server/](http://www.garryconn.com/linux/how-to-control-cpu-and-case-fan-speeds-on-a-linux-server/)

---

### Post by mellouli on 2011-06-15
> **pqwoerituytrueiwoq said:**
> check the temp when you are using classic ubuntu 
[http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/](http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/)
does the fan sound louder when you run windows on it?
yeah i tried every single one before i even installed LXDE and the same problem :sad:
I have known ubuntu since lucid and the same problem percist i386 or amd64
and the fan sound of windows is as loud as ubuntu but for 5 minutes maximum 8 minutes and then it's quiet

---

### Post by mellouli on 2011-06-15
> **StrayEddy said:**
> Control your fans ;)

[http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu](http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu)

or

[http://www.garryconn.com/linux/how-to-control-cpu-and-case-fan-speeds-on-a-linux-server/](http://www.garryconn.com/linux/how-to-control-cpu-and-case-fan-speeds-on-a-linux-server/)
I tried pwmconfig and that's the result
```
ubuntu@natty:~$ sudo pwmconfig
# pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/local/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

Iknow how to control my fans using 
```
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:00/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:0a/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:01/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:02/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:03/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:04/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:05/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:06/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:07/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:08/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:09/thermal_cooling/cur_state 
```

but them the laptop became hotter and reaches 60 C 
the fan start spinning automatically louder then usual and then as usual 
and stuck in the same speed and doesn't stop at all :(

---

### Post by mellouli on 2011-06-15
what can i do???

---

### Post by Quackers on 2011-06-15
For the moment I would suggest not using Ubuntu, until a fix can be found. You don't want to cook your pc!
Maybe trying some boot options, like noapic, nolapic or acpi=off might help (or others). Read here for how to do that
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Try first running the live cd with boot options and see if things improve.

---

### Post by mellouli on 2011-06-15
> **Quackers said:**
> For the moment I would suggest not using Ubuntu, until a fix can be found. You don't want to cook your pc!
Maybe trying some boot options, like noapic, nolapic or acpi=off might help (or others). Read here for how to do that
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Try first running the live cd with boot options and see if things improve.
that seemed interesting but i didn't understand how to use it and he's talking about nvidia but i have ati radeon hd 3430 I'm a bigginer in ubuntu and i don't wanna stop using it 
please help me

---

### Post by Quackers on 2011-06-15
The link largely talks about the nomodeset option.
You won't need that one, but the noapic, nolapic and acpi=off options are used in the same way.
If you read the whole thread you will see that boot options like these can be used for various purposes. They can be used to boot a live cd or an installed system, but the process is slightly different.

---

### Post by mellouli on 2011-06-15
> **Quackers said:**
> The link largely talks about the nomodeset option.
You won't need that one, but the noapic, nolapic and acpi=off options are used in the same way.
If you read the whole thread you will see that boot options like these can be used for various purposes. They can be used to boot a live cd or an installed system, but the process is slightly different.
when i tried that look what top gave me
```
ubuntu@natty:~$ top

top - 20:41:54 up 1 min,  2 users,  load average: 1.81, 0.77, 0.28
Tasks: 144 total,   1 running, 142 sleeping,   0 stopped,   1 zombie
Cpu(s):  1.5%us, 14.8%sy,  0.0%ni, 83.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3062628k total,   343100k used,  2719528k free,    27808k buffers
Swap:        0k total,        0k used,        0k free,   138836k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
   13 root      20   0     0    0    0 S   27  0.0   0:20.10 kworker/0:1        
 1025 root      20   0 34548  16m 6004 S    3  0.6   0:01.80 Xorg               
 1480 ubuntu    20   0  248m  42m  20m S    2  1.4   0:02.14 compiz             
 1695 ubuntu    20   0 93608  13m  10m S    1  0.5   0:00.49 gnome-terminal     
 1754 ubuntu    20   0  2632 1140  860 R    1  0.0   0:00.04 top                
 1495 ubuntu    20   0  120m  17m  12m S    0  0.6   0:00.67 nautilus           
    1 root      20   0  3012 1832 1276 S    0  0.1   0:01.38 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.16 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/0:0        
    5 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      -2  19     0    0    0 S    0  0.0   0:00.63 rcuc0              
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 rcun0              
    9 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
   10 root      20   0     0    0    0 S    0  0.0   0:00.02 kworker/1:0        
   11 root      -2  19     0    0    0 S    0  0.0   0:00.16 rcuc1 
```
what's that kworker that takes 27 percent of my cpu

---

### Post by Jacobonbuntu on 2011-06-15
....the "normal" temperature of your processor (s) depends on the *type* of processor!!
on the internet you will probably find the normal temerature of yours. Older AMD processors can get pretty hot.

*If *it is too hot, you should probably check your cooler "ribs" (don't know the English word for it) if they are not coverered with dust! I 've had this several times, after cleaning everything was ok.

edit:
oops, that's probably not it, I didn't read the post well...

---

### Post by mellouli on 2011-06-15
> **Jacobonbuntu said:**
> ....the "normal" temperature of your processor (s) depends on the *type* of processor!!
on the internet you will probably find the normal temerature of yours. Older AMD processors can get pretty hot.

*If *it is too hot, you should probably check your cooler "ribs" (don't know the English word for it) if they are not coverered with dust! I 've had this several times, after cleaning everything was ok.

edit:
oops, that's probably not it, I didn't read the post well...
no i have a core 2 duo intel 2.1 ghz and i clean the dust every week 
but like i said in windows the temperature don't go greater than 36 and the fan is quiet:confused:

---

### Post by Jacobonbuntu on 2011-06-15
> **mellouli said:**
> no i have a core 2 duo intel 2.1 ghz and i clean the dust every week 
but like i said in windows the temperature don't go greater than 36 and the fan is quiet:confused:

I once had a problem like this with an onboard videocard (running Windows XP). Fan was always blowing, and my cpu busy for 25% or so. I switched my videocard (for other reasons) and my cpu was "unemployed" since then. 
I am afraid it is no use for you.....

---

### Post by mellouli on 2011-06-15
> **Jacobonbuntu said:**
> I once had a problem like this with an onboard videocard (running Windows XP). Fan was always blowing, and my cpu busy for 25% or so. I switched my videocard (for other reasons) and my cpu was "unemployed" since then. 
I am afraid it is no use for you.....
but my VGA is ATI Radeon hd 3430 
and i have the driver installed in ubuntu
and it works fine with windows xp and the fan cpu is quiet

---

### Post by pqwoerituytrueiwoq on 2011-06-15
maybe windows is set to not run the cpu at full speed

---

### Post by Jacobonbuntu on 2011-06-15
AHA, 
that is a brillant thought, specially as we are dealing with a laptop!

---

### Post by mellouli on 2011-06-15
> **pqwoerituytrueiwoq said:**
> maybe windows is set to not run the cpu at full speed
so what can i do ](*,)

---

### Post by pqwoerituytrueiwoq on 2011-06-15
check the power management settings in windows and see if it is limiting the core speed
if it is below 100% that is why ubuntu runs hotterer
i would edit ondemand and change ondemand to conservative
alt+f2
gksudo gedit /etc/init.d/ondemand

line 27 has
        echo -n ondemand > $CPUFREQ
change it to
        echo -n conservative > $CPUFREQ

---

### Post by mellouli on 2011-06-15
> **pqwoerituytrueiwoq said:**
> check the power management settings in windows and see if it is limiting the core speed
if it is below 100% that is why ubuntu runs hotterer
i would edit ondemand and change ondemand to conservative
alt+f2
gksudo gedit /etc/init.d/ondemand

line 27 has
        echo -n ondemand > $CPUFREQ
change it to
        echo -n conservative > $CPUFREQ
yeah that worked a little
```
ubuntu@natty:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +44.0°C  (crit = +110.0°C)
temp2:        +31.0°C  (crit = +256.0°C)
temp3:        +44.0°C  (crit = +112.0°C)
temp4:        +46.0°C  (crit = +105.0°C)
temp5:        +28.3°C  (crit = +112.0°C)
temp6:        +50.0°C  (crit = +110.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +41.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +40.0°C  (high = +105.0°C, crit = +105.0°C)

```

and that after changing back to gnome classic 
but the fan doen't stop

---

### Post by mellouli on 2011-06-15
i installed powertop look what it gave me it might be important
[IMG]http://a7.sphotos.ak.fbcdn.net/hphotos-ak-snc6/254263_1864456008859_1164769270_31760178_2076227_n.jpg[/IMG]

---

### Post by mellouli on 2011-06-15
this one has more details

```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 5.1%)       Turbo Mode     0.0%
polling           0.0ms ( 0.0%)         2.10 Ghz     0.0%
C1 mwait          0.4ms ( 1.2%)         1.60 Ghz     0.0%
C4 mwait          2.8ms (93.6%)         1200 Mhz   100.0%



Wakeups-from-idle per second : 370.6    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  33.9% (189.2)   [Rescheduling interrupts] <kernel IPI>
  11.8% ( 65.9)   [extra timer interrupt]
  10.8% ( 60.3)   [radeon] <interrupt>
   7.8% ( 43.3)   [ata_piix, ehci_hcd:usb1, ehci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb5, uhci_hcd:usb6, uhci_hcd:usb7, uhci_hcd:usb8] <interrupt>
   7.8% ( 43.3)   USB device  8-1 :  USB OPTICAL MOUSE ()
   5.5% ( 30.7)   [kernel scheduler] Load balancing tick
   3.7% ( 20.8)   firefox-bin
   3.7% ( 20.5)   kworker/0:0
   3.4% ( 18.9)   [iwlagn] <interrupt>
   2.2% ( 12.1)   compiz
   1.9% ( 10.7)   [acpi] <interrupt>
   1.9% ( 10.6)   Xorg
   1.4% (  8.0)   [kernel core] usb_hcd_poll_rh_status (rh_timer_func)
   0.8% (  4.3)   [Function call interrupts] <kernel IPI>
   0.6% (  3.6)   [kernel core] hrtimer_start (tick_sched_timer)
   0.6% (  3.6)   xsensors
   0.6% (  3.4)   [ata_piix] <interrupt>
   0.4% (  2.0)   multiload-apple
   0.3% (  1.4)   sensors-applet
   0.2% (  1.0)   cpufreq-applet
   0.2% (  1.0)   [kernel core] start_rt_bandwidth (sched_rt_period_timer)
   0.1% (  0.5)   udisks-daemon
   0.1% (  0.4)   [TLB shootdowns] <kernel IPI>
   0.1% (  0.3)   gnome-settings-
   0.0% (  0.2)   lxterminal
   0.0% (  0.2)   gnome-panel
   0.0% (  0.2)   update-notifier
   0.0% (  0.1)   PS/2 keyboard/mouse/touchpad interrupt
Suggestion: Enable USB autosuspend for non-input devices by pressing the U key

```

---

### Post by Jacobonbuntu on 2011-06-16
....just for the record...
just checked my laptop, (pentium T2390) , temperature varies from 43-56! your values (your cpu's :)) seems not to be very high.
I also found this, maybe you can experiment with limitating the cpu frequency if you want to stay cool :)

[http://askubuntu.com/questions/30334/list-of-application-indicators](http://askubuntu.com/questions/30334/list-of-application-indicators)
([**[B]CPUFreq)**[/B]]("https://launchpad.net/indicator-cpufreq")

---

### Post by mellouli on 2011-06-16
> **Jacobonbuntu said:**
> ....just for the record...
just checked my laptop, (pentium T2390) , temperature varies from 43-56! your values (your cpu's :)) seems not to be very high.
I also found this, maybe you can experiment with limitating the cpu frequency if you want to stay cool :)

[http://askubuntu.com/questions/30334/list-of-application-indicators](http://askubuntu.com/questions/30334/list-of-application-indicators)
([**[B]CPUFreq)**[/B]]("https://launchpad.net/indicator-cpufreq")
Maybe the temperature of my laptop isn't high but why the fan doesn't stop automatically :confused::confused:

---

### Post by Jacobonbuntu on 2011-06-16
I checked...
My fan almost never slows down when I use my laptop (Natty), the same with my son's laptop (running Windows 7... )
I am not sure, I can imagine it does not feel comfortable, but I think it doesn't harm. The difference in your case with Windows is strange. 
Apart from that, usually in the bios is defined that the computer shuts down at a certain temperature to prevent damage, if the fan is broken for example. You can probably change the values, but I guess the default values will be a good choice...

---

### Post by mellouli on 2011-06-16
> **Jacobonbuntu said:**
> I checked...
My fan almost never slows down when I use my laptop (Natty), the same with my son's laptop (running Windows 7... )
I am not sure, I can imagine it does not feel comfortable, but I think it doesn't harm. The difference in your case with Windows is strange. 
Apart from that, usually in the bios is defined that the computer shuts down at a certain temperature to prevent damage, if the fan is broken for example. You can probably change the values, but I guess the default values will be a good choice...
But there is an other problem the battery life become too short when the fan doesn't stop that's why I wanna a solution:(

---

### Post by jtarin on 2011-06-16
What drivers have you installed for your video card? fglrx or proprietary?

---

### Post by |{urse on 2011-06-17
38c is an absolutely ok temp.

---

### Post by Jacobonbuntu on 2011-06-17
> **mellouli said:**
> But there is an other problem the battery life become too short when the fan doesn't stop that's why I wanna a solution:(


maybe it is a good thing to make sure your system is not occupied with some odd processes; an overheated system *can *only be overheated by doing a lot of work. I use the system monitor indicator:
[https://launchpad.net/indicator-sysmonitor/+download](https://launchpad.net/indicator-sysmonitor/+download) 
if your system is not occupied if you don't actually work on it, we can assume everything is ok. (in my case 01-05%)
In that case I would just reduce the processor-speed when running on batteries.

If your system *is *occupied when unused, I am curious what happens if you switch from fglrx to proprietary video card driver (or vice versa) as jtarin suggests. In my experience video cards are the first suspect in compatibility issues with Linux.

---

### Post by mellouli on 2011-06-17
> **jtarin said:**
> What drivers have you installed for your video card? fglrx or proprietary?
I tried to install fglrx but after installing it shows me a message fglrx could not be installed or upgraded report that problem and the driver was ati 11.6 x86
and while installing it shows me dmks failed or something like that 
i followed the indicated instructors in this site but nothing worked
:(:(:(:(

[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

and that's why I'm using xorg-edgers repository the open source driver
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by sammiev on 2011-06-17
My dual cores run at about 38c while my i5 runs about 44c to 52c. My fan is usually slow to off but can speed about to med or high on high processor speeds for a length of time. GL :)

---

### Post by jtarin on 2011-06-17
> **mellouli said:**
> I tried to install fglrx but after installing it shows me a message fglrx could not be installed or upgraded report that problem and the driver was ati 11.6 x86
and while installing it shows me dmks failed or something like that 
i followed the indicated instructors in this site but nothing worked
:(:(:(:(

[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

and that's why I'm using xorg-edgers repository the open source driver
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)Run the command ```
lspci
``` and post the results.

---

### Post by pqwoerituytrueiwoq on 2011-06-17
> **jtarin said:**
> Run the command ```
lspci
``` and post the results.
how about ```
sudo hwinfo --all > ~/Desktop/hwinfo.txt
``` also
the output will not fit in terminal window without using the less command so i made it dump it to a file on the desktop that you can attach (may need to be compressed)
that should tell us everything from bios version to your dvd drive

---

### Post by mellouli on 2011-06-17
> **jtarin said:**
> Run the command ```
lspci
``` and post the results.
here it is

```
ubuntu@natty:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 95c2
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
86:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8072 PCI-E Gigabit Ethernet Controller

```

---

### Post by mellouli on 2011-06-17
> **pqwoerituytrueiwoq said:**
> how about ```
sudo hwinfo --all > ~/Desktop/hwinfo.txt
``` also
the output will not fit in terminal window without using the less command so i made it dump it to a file on the desktop that you can attach (may need to be compressed)
that should tell us everything from bios version to your dvd drive
there it is
```
01: None 00.0: 10105 BIOS
  [Created at bios.190]
  Unique ID: rdCR.lZF+r4EgHp4
  Hardware Class: bios
  BIOS Keyboard LED Status:
    Scroll Lock: off
    Num Lock: off
    Caps Lock: off
  Parallel Port 0: 0x378
  Base Memory: 639 kB
  PnP BIOS: @D@3C00
  SMBIOS Version: 2.4
  BIOS Info: #10
    Vendor: "Hewlett-Packard"
    Version: "68PZD Ver. F.13"
    Date: "12/06/2010"
    Start Address: 0xf0000
    ROM Size: 2048 kB
    Features: 0x0783000000003c099980
      PCI supported
      PCMCIA supported
      BIOS flashable
      BIOS shadowing allowed
      CD boot supported
      Selectable boot supported
      EDD spec supported
      Print Screen supported
      8042 Keyboard Services supported
      Serial Services supported
      Printer Services supported
      ACPI supported
      USB Legacy supported
      Smart Battery supported
      BIOS Boot Spec supported
      F12 Network boot supported
  System Info: #11
    Manufacturer: "Hewlett-Packard"
    Product: "HP Compaq 6830s"
    Version: "F.13"
    Serial: "CNU9122PCY"
    UUID: undefined, but settable
    Wake-up: 0x06 (Power Switch)
  Board Info: #12
    Manufacturer: "Hewlett-Packard"
    Product: "30E9"
    Version: "KBC Version 95.1D"
    Serial: "CNU9122PCY"
    Type: 0x01 (Other)
    Features: 0x09
      Hosting Board
      Replaceable
    Chassis: #13
  Chassis Info: #13
    Manufacturer: "Hewlett-Packard"
    Serial: "CNU9122PCY"
    Type: 0x0a (Notebook)
    Bootup State: 0x03 (Safe)
    Power Supply State: 0x03 (Safe)
    Thermal State: 0x01 (Other)
    Security Status: 0x01 (Other)
  Processor Info: #0
    Socket: "Intel(R) Genuine processor"
    Socket Type: 0x04 (ZIF Socket)
    Socket Status: Populated
    Type: 0x03 (CPU)
    Family: 0x01 (Other)
    Manufacturer: "Intel(R) Corporation"
    Version: "Intel(R) Core(TM)2 Duo CPU     T6570  @ 2.10GHz"
    Asset Tag: "Intel(R) Genuine processor"
    Processor ID: 0xbfebfbff0001067a
    Status: 0x01 (Enabled)
    Voltage: 1.6 V
    External Clock: 200 MHz
    Max. Speed: 2100 MHz
    Current Speed: 1300 MHz
    L1 Cache: #3
    L2 Cache: #1
  Cache Info: #1
    Designation: "Internal Cache"
    Level: L2
    State: Enabled
    Mode: 0x01 (Write Back)
    Location: 0x00 (Internal, Not Socketed)
    ECC: 0x05 (Single-bit)
    Type: 0x05 (Unified)
    Associativity: 0x07 (8-way Set-Associative)
    Max. Size: 2048 kB
    Current Size: 2048 kB
    Supported SRAM Types: 0x0040 (Asynchronous)
    Current SRAM Type: 0x0040 (Asynchronous)
  Cache Info: #3
    Designation: "Internal Cache"
    Level: L1
    State: Enabled
    Mode: 0x01 (Write Back)
    Location: 0x00 (Internal, Not Socketed)
    ECC: 0x05 (Single-bit)
    Type: 0x04 (Data)
    Associativity: 0x07 (8-way Set-Associative)
    Max. Size: 32 kB
    Current Size: 32 kB
    Supported SRAM Types: 0x0040 (Asynchronous)
    Current SRAM Type: 0x0040 (Asynchronous)
  Cache Info: #2
    Designation: "Internal Cache"
    Level: L1
    State: Enabled
    Mode: 0x01 (Write Back)
    Location: 0x00 (Internal, Not Socketed)
    ECC: 0x05 (Single-bit)
    Type: 0x03 (Instruction)
    Associativity: 0x07 (8-way Set-Associative)
    Max. Size: 32 kB
    Current Size: 32 kB
    Supported SRAM Types: 0x0040 (Asynchronous)
    Current SRAM Type: 0x0040 (Asynchronous)
  System Slot: #16
    Designation: "PCI SLOT1"
    Type: 0x06 (PCI)
    Bus Width: 0x05 (32 bit)
    Status: 0x03 (Available)
    Length: 0x04 (Long)
    Slot ID: 1
    Characteristics: 0x0504 (3.3 V, PME#)
  OEM Strings: #15
    ABS 70/71 79 7A 7B 7C
    CSM v01.30
    www.hp.com
  Physical Memory Array: #4
    Use: 0x03 (System memory)
    Location: 0x03 (Motherboard)
    Slots: 2
    Max. Size: 8 GB
    ECC: 0x03 (None)
  Memory Device: #5
    Location: "Top"
    Bank: "BANK 0"
    Manufacturer: "7F7F7F8300000000"
    Serial: "00000000"
    Asset Tag: "Unknown"
    Memory Array: #4
    Form Factor: 0x0d (SODIMM)
    Type: 0x13 (Other)
    Type Detail: 0x0080 (Synchronous)
    Data Width: 64 bits
    Size: 2 GB
    Speed: 667 MHz
  Memory Device: #7
    Location: "Bottom"
    Bank: "BANK 2"
    Manufacturer: "Hynix"
    Serial: "00001060"
    Asset Tag: "Unknown"
    Part Number: "HYMP125S64CP8-S6"
    Memory Array: #4
    Form Factor: 0x0d (SODIMM)
    Type: 0x13 (Other)
    Type Detail: 0x0080 (Synchronous)
    Data Width: 64 bits
    Size: 2 GB
    Speed: 667 MHz
  Memory Array Mapping: #9
    Memory Array: #4
    Partition Width: 2
    Start Address: 0x0000000000000000
    End Address: 0x0000000100000000
  Memory Device Mapping: #6
    Memory Device: #5
    Array Mapping: #9
    Row: 1
    Interleave Pos: 1
    Interleaved Depth: 1
    Start Address: 0x00000000
    End Address: 0x80000000
  Memory Device Mapping: #8
    Memory Device: #7
    Array Mapping: #9
    Row: 1
    Interleave Pos: 2
    Interleaved Depth: 1
    Start Address: 0x00000000
    End Address: 0x80000000
  Type 22 Record: #17
    Data 00: 16 1a 11 00 01 02 03 04 05 02 30 11 40 38 06 ff
    Data 10: ab 04 54 3a 07 01 00 00 00 00
    String 1: "Primary"
    String 2: "STL-SOG6F"
    String 3: "3A54"
    String 4: "04AB"
    String 5: "DD08063"
    String 6: "1.1"
    String 7: "LION"
  Type 32 Record: #14
    Data 00: 20 14 0e 00 00 00 00 00 00 00 00 00 00 00 00 00
    Data 10: 00 00 00 00
  Type 129 Record: #18
    Data 00: 81 08 12 00 01 01 02 00
    String 1: "Intel_ASF"
    String 2: "Intel_ASF_001"
  Type 130 Record: #19
    Data 00: 82 14 13 00 24 41 4d 54 01 00 00 00 00 a5 0b 02
    Data 10: 00 00 00 00
  Config Status: cfg=new, avail=yes, need=no, active=unknown

02: None 00.0: 10107 System
  [Created at sys.63]
  Unique ID: rdCR.n_7QNeEnh23
  Hardware Class: system
  Model: "System"
  Driver Info #0:
    Driver Status: thermal,fan are not active
    Driver Activation Cmd: "modprobe thermal; modprobe fan"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

03: None 00.0: 10104 FPU
  [Created at misc.192]
  Unique ID: rdCR.EMpH5pjcahD
  Hardware Class: unknown
  Model: "FPU"
  I/O Ports: 0xf0-0xff (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

04: None 00.0: 0801 DMA controller (8237)
  [Created at misc.206]
  Unique ID: rdCR.f5u1ucRm+H9
  Hardware Class: unknown
  Model: "DMA controller"
  I/O Ports: 0x00-0xcf7 (rw)
  I/O Ports: 0xc0-0xdf (rw)
  I/O Ports: 0x80-0x8f (rw)
  DMA: 4
  Config Status: cfg=new, avail=yes, need=no, active=unknown

05: None 00.0: 0800 PIC (8259)
  [Created at misc.219]
  Unique ID: rdCR.8uRK7LxiIA2
  Hardware Class: unknown
  Model: "PIC"
  I/O Ports: 0x20-0x21 (rw)
  I/O Ports: 0xa0-0xa1 (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

06: None 00.0: 0802 Timer (8254)
  [Created at misc.230]
  Unique ID: rdCR.AJKleuxpiP0
  Hardware Class: unknown
  Model: "Timer"
  IRQ: 0 (1085429 events)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

07: None 00.0: 0900 Keyboard controller
  [Created at misc.251]
  Unique ID: rdCR.9N+EecqykME
  Hardware Class: unknown
  Model: "Keyboard controller"
  I/O Port: 0x60 (rw)
  I/O Port: 0x64 (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

08: None 00.0: 0701 Parallel controller (SPP)
  [Created at misc.262]
  Unique ID: YMnp.ecK7NLYWZ5D
  Hardware Class: unknown
  Model: "Parallel controller"
  Device File: /dev/lp0
  I/O Ports: 0x378-0x37a (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

09: None 00.0: 10400 PS/2 Controller
  [Created at misc.304]
  Unique ID: rdCR.DziBbWO85o5
  Hardware Class: unknown
  Model: "PS/2 Controller"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

12: None 00.0: 10102 Main Memory
  [Created at memory.61]
  Unique ID: rdCR.CxwsZFjVASF
  Hardware Class: memory
  Model: "Main Memory"
  Memory Range: 0x00000000-0xbaef2fff (rw)
  Memory Size: 3 GB
  Config Status: cfg=new, avail=yes, need=no, active=unknown

13: PCI 00.0: 0600 Host bridge
  [Created at pci.318]
  Unique ID: qLht.ssqrsnbd70F
  SysFS ID: /devices/pci0000:00/0000:00:00.0
  SysFS BusID: 0000:00:00.0
  Hardware Class: bridge
  Model: "Intel Mobile 4 Series Chipset Memory Controller Hub"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2a40 "Mobile 4 Series Chipset Memory Controller Hub"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30e9 
  Revision: 0x07
  Module Alias: "pci:v00008086d00002A40sv0000103Csd000030E9bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

14: PCI 01.0: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  Unique ID: vSkL.R7YROTkYTtB
  SysFS ID: /devices/pci0000:00/0000:00:01.0
  SysFS BusID: 0000:00:01.0
  Hardware Class: bridge
  Model: "Intel Mobile 4 Series Chipset PCI Express Graphics Port"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2a41 "Mobile 4 Series Chipset PCI Express Graphics Port"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30e9 
  Revision: 0x07
  Driver: "pcieport"
  IRQ: 40 (no events)
  Module Alias: "pci:v00008086d00002A41sv0000103Csd000030E9bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is not active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

15: PCI 1a.0: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  Unique ID: pwJ7.90z7LDeS0N3
  SysFS ID: /devices/pci0000:00/0000:00:1a.0
  SysFS BusID: 0000:00:1a.0
  Hardware Class: usb controller
  Model: "Intel 82801I (ICH9 Family) USB UHCI Controller #4"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2937 "82801I (ICH9 Family) USB UHCI Controller #4"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30e9 
  Revision: 0x03
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0x80a0-0x80bf (rw)
  IRQ: 16 (130 events)
  Module Alias: "pci:v00008086d00002937sv0000103Csd000030E9bc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

16: PCI 1a.1: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  Unique ID: gFpy.gQvtpnl9Yl3
  SysFS ID: /devices/pci0000:00/0000:00:1a.1
  SysFS BusID: 0000:00:1a.1
  Hardware Class: usb controller
  Model: "Intel 82801I (ICH9 Family) USB UHCI Controller #5"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2938 "82801I (ICH9 Family) USB UHCI Controller #5"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30e9 
  Revision: 0x03
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0x8080-0x809f (rw)
  IRQ: 17 (no events)
  Module Alias: "pci:v00008086d00002938sv0000103Csd000030E9bc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

17: PCI 1a.2: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  Unique ID: XaIo.BrrdIMts384
  SysFS ID: /devices/pci0000:00/0000:00:1a.2
  SysFS BusID: 0000:00:1a.2
  Hardware Class: usb controller
  Model: "Intel 82801I (ICH9 Family) USB UHCI Controller #6"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2939 "82801I (ICH9 Family) USB UHCI Controller #6"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30e9 
  Revision: 0x03
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0x8060-0x807f (rw)
  IRQ: 18 (51969 events)
  Module Alias: "pci:v00008086d00002939sv0000103Csd000030E9bc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

18: PCI 1a.7: 0c03 USB Controller (EHCI)
  [Created at pci.318]
  Unique ID: sClz.E5H318jkA7A
  SysFS ID: /devices/pci0000:00/0000:00:1a.7
  SysFS BusID: 0000:00:1a.7
  Hardware Class: usb controller
  Model: "Intel 82801I (ICH9 Family) USB2 EHCI Controller #2"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x293c "82801I (ICH9 Family) USB2 EHCI Controller #2"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30e9 
  Revision: 0x03
  Driver: "ehci_hcd"
  Driver Modules: "ehci_hcd"
  Memory Range: 0xd8504400-0xd85047ff (rw,non-prefetchable)
  IRQ: 19 (27 events)
  Module Alias: "pci:v00008086d0000293Csv0000103Csd000030E9bc0Csc03i20"
  Driver Info #0:
    Driver Status: ehci-hcd is not active
    Driver Activation Cmd: "modprobe ehci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

19: PCI 1b.0: 0403 Audio device
  [Created at pci.318]
  Unique ID: u1Nb.wXIM0qkt4J2
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801I (ICH9 Family) HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x293e "82801I (ICH9 Family) HD Audio Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x3605 
  Revision: 0x03
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xd8500000-0xd8503fff (rw,non-prefetchable)
  IRQ: 49 (2383 events)
  Module Alias: "pci:v00008086d0000293Esv0000103Csd00003605bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

20: PCI 1c.0: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  Unique ID: z8Q3.6XhEowSpRr2
  SysFS ID: /devices/pci0000:00/0000:00:1c.0
  SysFS BusID: 0000:00:1c.0
  Hardware Class: bridge
  Model: "Intel 82801I (ICH9 Family) PCI Express Port 1"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2940 "82801I (ICH9 Family) PCI Express Port 1"
  Revision: 0x03
  Driver: "pcieport"
  IRQ: 41 (no events)
  Module Alias: "pci:v00008086d00002940sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is not active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

21: PCI 1c.1: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  Unique ID: qTvu.8Makl3iDVc3
  SysFS ID: /devices/pci0000:00/0000:00:1c.1
  SysFS BusID: 0000:00:1c.1
  Hardware Class: bridge
  Model: "Intel 82801I (ICH9 Family) PCI Express Port 2"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2942 "82801I (ICH9 Family) PCI Express Port 2"
  Revision: 0x03
  Driver: "pcieport"
  IRQ: 42 (no events)
  Module Alias: "pci:v00008086d00002942sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is not active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

22: PCI 1c.2: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  Unique ID: hoOk.ABTEjCxdYN4
  SysFS ID: /devices/pci0000:00/0000:00:1c.2
  SysFS BusID: 0000:00:1c.2
  Hardware Class: bridge
  Model: "Intel 82801I (ICH9 Family) PCI Express Port 3"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2944 "82801I (ICH9 Family) PCI Express Port 3"
  Revision: 0x03
  Driver: "pcieport"
  IRQ: 43 (no events)
  Module Alias: "pci:v00008086d00002944sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is not active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

23: PCI 1c.4: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  Unique ID: QSNP.ErEEeUPSfv5
  SysFS ID: /devices/pci0000:00/0000:00:1c.4
  SysFS BusID: 0000:00:1c.4
  Hardware Class: bridge
  Model: "Intel 82801I (ICH9 Family) PCI Express Port 5"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2948 "82801I (ICH9 Family) PCI Express Port 5"
  Revision: 0x03
  Driver: "pcieport"
  IRQ: 44 (no events)
  Module Alias: "pci:v00008086d00002948sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is not active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

24: PCI 1c.5: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  Unique ID: HnsE.Gg7kbdesig6
  SysFS ID: /devices/pci0000:00/0000:00:1c.5
  SysFS BusID: 0000:00:1c.5
  Hardware Class: bridge
  Model: "Intel 82801I (ICH9 Family) PCI Express Port 6"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x294a "82801I (ICH9 Family) PCI Express Port 6"
  Revision: 0x03
  Driver: "pcieport"
  IRQ: 45 (no events)
  Module Alias: "pci:v00008086d0000294Asv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is not active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

25: PCI 1d.0: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  Unique ID: 1GTX.cm7uuZx6Re3
  SysFS ID: /devices/pci0000:00/0000:00:1d.0
  SysFS BusID: 0000:00:1d.0
  Hardware Class: usb controller
  Model: "Intel 82801I (ICH9 Family) USB UHCI Controller #1"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2934 "82801I (ICH9 Family) USB UHCI Controller #1"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30e9 
  Revision: 0x03
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0x8040-0x805f (rw)
  IRQ: 20 (2 events)
  Module Alias: "pci:v00008086d00002934sv0000103Csd000030E9bc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

26: PCI 1d.1: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  Unique ID: vayM.7B4eN83qy04
  SysFS ID: /devices/pci0000:00/0000:00:1d.1
  SysFS BusID: 0000:00:1d.1
  Hardware Class: usb controller
  Model: "Intel 82801I (ICH9 Family) USB UHCI Controller #2"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2935 "82801I (ICH9 Family) USB UHCI Controller #2"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30e9 
  Revision: 0x03
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0x8020-0x803f (rw)
  IRQ: 22 (no events)
  Module Alias: "pci:v00008086d00002935sv0000103Csd000030E9bc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

27: PCI 1d.2: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  Unique ID: mvRC.eb0OsiAXUP4
  SysFS ID: /devices/pci0000:00/0000:00:1d.2
  SysFS BusID: 0000:00:1d.2
  Hardware Class: usb controller
  Model: "Intel 82801I (ICH9 Family) USB UHCI Controller #3"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2936 "82801I (ICH9 Family) USB UHCI Controller #3"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30e9 
  Revision: 0x03
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0x8000-0x801f (rw)
  IRQ: 18 (51969 events)
  Module Alias: "pci:v00008086d00002936sv0000103Csd000030E9bc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

28: PCI 1d.7: 0c03 USB Controller (EHCI)
  [Created at pci.318]
  Unique ID: 5YuN.CGOZ3+TK7M9
  SysFS ID: /devices/pci0000:00/0000:00:1d.7
  SysFS BusID: 0000:00:1d.7
  Hardware Class: usb controller
  Model: "Intel 82801I (ICH9 Family) USB2 EHCI Controller #1"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x293a "82801I (ICH9 Family) USB2 EHCI Controller #1"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30e9 
  Revision: 0x03
  Driver: "ehci_hcd"
  Driver Modules: "ehci_hcd"
  Memory Range: 0xd8504000-0xd85043ff (rw,non-prefetchable)
  IRQ: 20 (2 events)
  Module Alias: "pci:v00008086d0000293Asv0000103Csd000030E9bc0Csc03i20"
  Driver Info #0:
    Driver Status: ehci-hcd is not active
    Driver Activation Cmd: "modprobe ehci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

29: PCI 1e.0: 0604 PCI bridge (Subtractive decode)
  [Created at pci.318]
  Unique ID: 6NW+.IGWbx9KFJQ9
  SysFS ID: /devices/pci0000:00/0000:00:1e.0
  SysFS BusID: 0000:00:1e.0
  Hardware Class: bridge
  Model: "Intel 82801 Mobile PCI Bridge"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2448 "82801 Mobile PCI Bridge"
  Revision: 0x93
  Module Alias: "pci:v00008086d00002448sv00000000sd00000000bc06sc04i01"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

30: PCI 1f.0: 0601 ISA bridge
  [Created at pci.318]
  Unique ID: BUZT.ZFRlJ_MU9u1
  SysFS ID: /devices/pci0000:00/0000:00:1f.0
  SysFS BusID: 0000:00:1f.0
  Hardware Class: bridge
  Model: "Intel ICH9M LPC Interface Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2919 "ICH9M LPC Interface Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30e9 
  Revision: 0x03
  Module Alias: "pci:v00008086d00002919sv0000103Csd000030E9bc06sc01i00"
  Driver Info #0:
    Driver Status: iTCO_wdt is not active
    Driver Activation Cmd: "modprobe iTCO_wdt"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

31: PCI 1f.2: 0101 IDE interface
  [Created at pci.318]
  Unique ID: w7Y8.Nyppg9lrOB5
  SysFS ID: /devices/pci0000:00/0000:00:1f.2
  SysFS BusID: 0000:00:1f.2
  Hardware Class: storage
  Model: "Intel ICH9M/M-E 2 port SATA IDE Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2928 "ICH9M/M-E 2 port SATA IDE Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30e9 
  Revision: 0x03
  Driver: "ata_piix"
  Driver Modules: "ata_piix"
  I/O Ports: 0x1f0-0x1f7 (rw)
  I/O Port: 0x3f6 (rw)
  I/O Ports: 0x170-0x177 (rw)
  I/O Port: 0x376 (rw)
  I/O Ports: 0x80f0-0x80ff (rw)
  I/O Ports: 0x80e0-0x80ef (rw)
  IRQ: 21 (no events)
  Module Alias: "pci:v00008086d00002928sv0000103Csd000030E9bc01sc01i8a"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

32: PCI 1f.5: 0101 IDE interface
  [Created at pci.318]
  Unique ID: W60f.t4kjneGNJW3
  SysFS ID: /devices/pci0000:00/0000:00:1f.5
  SysFS BusID: 0000:00:1f.5
  Hardware Class: storage
  Model: "Intel ICH9M/M-E 2 port SATA IDE Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x292d "ICH9M/M-E 2 port SATA IDE Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30e9 
  Revision: 0x03
  Driver: "ata_piix"
  Driver Modules: "ata_piix"
  I/O Ports: 0x8108-0x810f (rw)
  I/O Ports: 0x8124-0x8127 (rw)
  I/O Ports: 0x8100-0x8107 (rw)
  I/O Ports: 0x8120-0x8123 (rw)
  I/O Ports: 0x80d0-0x80df (rw)
  I/O Ports: 0x80c0-0x80cf (rw)
  IRQ: 18 (51969 events)
  Module Alias: "pci:v00008086d0000292Dsv0000103Csd000030E9bc01sc01i85"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

33: PCI 100.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  Unique ID: VCu0.zd38egnLD6B
  Parent ID: vSkL.R7YROTkYTtB
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "ATI VGA compatible controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x95c2 
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30e9 
  Driver: "radeon"
  Driver Modules: "drm"
  Memory Range: 0xc0000000-0xcfffffff (ro,non-prefetchable)
  I/O Ports: 0x7000-0x7fff (rw)
  Memory Range: 0xd8400000-0xd840ffff (rw,non-prefetchable)
  Memory Range: 0xd8420000-0xd843ffff (ro,non-prefetchable,disabled)
  IRQ: 48 (177093 events)
  Module Alias: "pci:v00001002d000095C2sv0000103Csd000030E9bc03sc00i00"
  Driver Info #0:
    Driver Status: radeon is active
    Driver Activation Cmd: "modprobe radeon"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (PCI bridge)

34: PCI 300.0: 0282 WLAN controller
  [Created at pci.318]
  Unique ID: y9sn.GbTjk0YbA70
  Parent ID: qTvu.8Makl3iDVc3
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Intel PRO/Wireless 5100 AGN [Shiloh] Network Connection"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x4237 "PRO/Wireless 5100 AGN [Shiloh] Network Connection"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x1211 
  Driver: "iwlagn"
  Driver Modules: "iwlagn"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xd8200000-0xd8201fff (rw,non-prefetchable)
  IRQ: 47 (341872 events)
  HW Address: 00:22:fa:41:86:64
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 36 40 44 48 52 56 60 64 100 104 108 112 116 120 124 128 132 136 140
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 5.18 5.2 5.22 5.24 5.26 5.28 5.3 5.32 5.5 5.52 5.54 5.56 5.58 5.6 5.62 5.64 5.66 5.68 5.7
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v00008086d00004237sv00008086sd00001211bc02sc80i00"
  Driver Info #0:
    Driver Status: iwlagn is active
    Driver Activation Cmd: "modprobe iwlagn"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #21 (PCI bridge)

35: PCI 8600.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.sA9iTwyxNq9
  Parent ID: HnsE.Gg7kbdesig6
  SysFS ID: /devices/pci0000:00/0000:00:1c.5/0000:86:00.0
  SysFS BusID: 0000:86:00.0
  Hardware Class: network
  Model: "Marvell Ethernet controller"
  Vendor: pci 0x11ab "Marvell Technology Group Ltd."
  Device: pci 0x436c 
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30e9 
  Driver: "sky2"
  Driver Modules: "sky2"
  Device File: eth0
  Memory Range: 0xd0100000-0xd0103fff (rw,non-prefetchable)
  I/O Ports: 0x2000-0x2fff (rw)
  Memory Range: 0xd8600000-0xd861ffff (ro,non-prefetchable,disabled)
  IRQ: 46 (1 event)
  HW Address: 00:24:81:54:1a:9f
  Link detected: no
  Module Alias: "pci:v000011ABd0000436Csv0000103Csd000030E9bc02sc00i00"
  Driver Info #0:
    Driver Status: sky2 is active
    Driver Activation Cmd: "modprobe sky2"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #24 (PCI bridge)

36: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: z9pp.+GmdJItMGB9
  SysFS ID: /devices/pnp0/00:00
  SysFS BusID: 00:00
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0a08 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

37: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: QL3u.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:01
  SysFS BusID: 00:01
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

38: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: tWJy.ld94kxNGZf5
  SysFS ID: /devices/pnp0/00:02
  SysFS BusID: 00:02
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0200 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

39: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: KiZ0.jDhFyyFrbg5
  SysFS ID: /devices/pnp0/00:03
  SysFS BusID: 00:03
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: INT 
  SubDevice: eisa 0x0800 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

40: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: ntp4.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:04
  SysFS BusID: 00:04
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

41: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: E349.fG36JLVNse9
  SysFS ID: /devices/pnp0/00:05
  SysFS BusID: 00:05
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0103 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

42: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: hEKD.DE8RM9cWQQ8
  SysFS ID: /devices/pnp0/00:06
  SysFS BusID: 00:06
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c04 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

43: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: NhVi.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:07
  SysFS BusID: 00:07
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

44: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: qslm.WYwRElrJa93
  SysFS ID: /devices/pnp0/00:08
  SysFS BusID: 00:08
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0b00 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

45: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: H20r.xhndlW9HXJ7
  SysFS ID: /devices/pnp0/00:09
  SysFS BusID: 00:09
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0303 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

46: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: iT2w.DXDbhsRcPO7
  SysFS ID: /devices/pnp0/00:0a
  SysFS BusID: 00:0a
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: SYN 
  SubDevice: eisa 0x014b 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

47: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  Unique ID: 9fI_.B95vU_X3dpD
  SysFS ID: /devices/pnp0/00:0b
  SysFS BusID: 00:0b
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: HPQ 
  SubDevice: eisa 0x0004 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

48: IDE 00.0: 10600 Disk
  [Created at block.243]
  Unique ID: 3OOL.XhsCrWLP9j2
  Parent ID: w7Y8.Nyppg9lrOB5
  SysFS ID: /class/block/sda
  SysFS BusID: 0:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
  Hardware Class: disk
  Model: "Hitachi HTS54322"
  Vendor: "Hitachi"
  Device: "HTS54322"
  Revision: "FBEO"
  Serial ID: "090314FBCE00LKE3ADBB"
  Driver: "ata_piix", "sd"
  Driver Modules: "ata_piix"
  Device File: /dev/sda
  Device Files: /dev/sda, /dev/disk/by-id/ata-Hitachi_HTS543225L9A300_090314FBCE00LKE3ADBB, /dev/disk/by-id/scsi-SATA_Hitachi_HTS5432090314FBCE00LKE3ADBB, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0, /dev/disk/by-id/wwn-0x5000cca566ddb328
  Device Number: block 8:0-8:15
  BIOS id: 0x80
  Geometry (Logical): CHS 30401/255/63
  Size: 488397168 sectors a 512 bytes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #31 (IDE interface)

49: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: bdUI.SE1wIdpsiiC
  Parent ID: 3OOL.XhsCrWLP9j2
  SysFS ID: /class/block/sda/sda1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda1
  Device Files: /dev/sda1, /dev/disk/by-id/ata-Hitachi_HTS543225L9A300_090314FBCE00LKE3ADBB-part1, /dev/disk/by-id/scsi-SATA_Hitachi_HTS5432090314FBCE00LKE3ADBB-part1, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1, /dev/disk/by-uuid/8E9039AE90399DA1, /dev/disk/by-id/wwn-0x5000cca566ddb328-part1
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #48 (Disk)

50: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: 2pkM.SE1wIdpsiiC
  Parent ID: 3OOL.XhsCrWLP9j2
  SysFS ID: /class/block/sda/sda2
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda2
  Device Files: /dev/sda2, /dev/disk/by-id/ata-Hitachi_HTS543225L9A300_090314FBCE00LKE3ADBB-part2, /dev/disk/by-id/scsi-SATA_Hitachi_HTS5432090314FBCE00LKE3ADBB-part2, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2, /dev/disk/by-uuid/FC70-0B33, /dev/disk/by-id/wwn-0x5000cca566ddb328-part2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #48 (Disk)

51: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: W__Q.SE1wIdpsiiC
  Parent ID: 3OOL.XhsCrWLP9j2
  SysFS ID: /class/block/sda/sda3
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda3
  Device Files: /dev/sda3, /dev/disk/by-id/ata-Hitachi_HTS543225L9A300_090314FBCE00LKE3ADBB-part3, /dev/disk/by-id/scsi-SATA_Hitachi_HTS5432090314FBCE00LKE3ADBB-part3, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part3, /dev/disk/by-id/wwn-0x5000cca566ddb328-part3
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #48 (Disk)

52: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: QLVZ.SE1wIdpsiiC
  Parent ID: 3OOL.XhsCrWLP9j2
  SysFS ID: /class/block/sda/sda5
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda5
  Device Files: /dev/sda5, /dev/disk/by-id/ata-Hitachi_HTS543225L9A300_090314FBCE00LKE3ADBB-part5, /dev/disk/by-id/scsi-SATA_Hitachi_HTS5432090314FBCE00LKE3ADBB-part5, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part5, /dev/disk/by-uuid/efd22f22-834c-46be-a378-985e0d94c726, /dev/disk/by-id/wwn-0x5000cca566ddb328-part5
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #48 (Disk)

53: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: tWld.SE1wIdpsiiC
  Parent ID: 3OOL.XhsCrWLP9j2
  SysFS ID: /class/block/sda/sda6
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda6
  Device Files: /dev/sda6, /dev/disk/by-id/ata-Hitachi_HTS543225L9A300_090314FBCE00LKE3ADBB-part6, /dev/disk/by-id/scsi-SATA_Hitachi_HTS5432090314FBCE00LKE3ADBB-part6, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part6, /dev/disk/by-uuid/31672adb-1c33-4d3b-b340-0732a0655e99, /dev/disk/by-id/wwn-0x5000cca566ddb328-part6, /dev/root
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #48 (Disk)

54: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: Zzw6.SE1wIdpsiiC
  Parent ID: 3OOL.XhsCrWLP9j2
  SysFS ID: /class/block/sda/sda7
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda7
  Device Files: /dev/sda7, /dev/disk/by-id/ata-Hitachi_HTS543225L9A300_090314FBCE00LKE3ADBB-part7, /dev/disk/by-id/scsi-SATA_Hitachi_HTS5432090314FBCE00LKE3ADBB-part7, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part7, /dev/disk/by-uuid/6f101a7e-6458-4b23-a94e-723adfa6d42e, /dev/disk/by-id/wwn-0x5000cca566ddb328-part7
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #48 (Disk)

55: SCSI 100.0: 10602 CD-ROM (DVD)
  [Created at block.247]
  Unique ID: KD9E.YcyXXvOrs5E
  Parent ID: w7Y8.Nyppg9lrOB5
  SysFS ID: /class/block/sr0
  SysFS BusID: 1:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
  Hardware Class: cdrom
  Model: "Optiarc DVD RW AD-7561S"
  Vendor: "Optiarc"
  Device: "DVD RW AD-7561S"
  Revision: "AH03"
  Driver: "ata_piix", "sr"
  Driver Modules: "ata_piix"
  Device File: /dev/sr0 (/dev/sg1)
  Device Files: /dev/sr0, /dev/scd0, /dev/disk/by-id/ata-Optiarc_DVD_RW_AD-7561S_30651450_4049159Q111, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw
  Device Number: block 11:0 (char 21:1)
  Features: DVD
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #31 (IDE interface)
  Drive Speed: 24

56: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: k4bc.cO89g+iefn1
  Parent ID: sClz.E5H318jkA7A
  SysFS ID: /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.39-0-generic ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.39-0-generic ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1a.7"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
  Driver Info #0:
    Driver Status: option is not active
    Driver Activation Cmd: "modprobe option"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (USB Controller)

57: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: pBe4.9T1GDCLyFd9
  Parent ID: 5YuN.CGOZ3+TK7M9
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
  SysFS BusID: 2-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.39-0-generic ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.39-0-generic ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1d.7"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
  Driver Info #0:
    Driver Status: option is not active
    Driver Activation Cmd: "modprobe option"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #28 (USB Controller)

58: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: uIhY.MxUuepIFPaE
  Parent ID: pwJ7.90z7LDeS0N3
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
  SysFS BusID: 3-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.39-0-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.39-0-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1a.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (USB Controller)

59: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: zPk0.7gZT0a5zLs5
  Parent ID: gFpy.gQvtpnl9Yl3
  SysFS ID: /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
  SysFS BusID: 4-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.39-0-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.39-0-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1a.1"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #16 (USB Controller)

60: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: 2XnU.uOe2OKugI8D
  Parent ID: XaIo.BrrdIMts384
  SysFS ID: /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
  SysFS BusID: 5-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.39-0-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.39-0-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1a.2"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (USB Controller)

61: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: 7eqy.v+N+B0xY+P6
  Parent ID: 1GTX.cm7uuZx6Re3
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
  SysFS BusID: 6-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.39-0-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.39-0-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1d.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #25 (USB Controller)

62: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: BSFT.gkSaZmjGyhD
  Parent ID: vayM.7B4eN83qy04
  SysFS ID: /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
  SysFS BusID: 7-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.39-0-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.39-0-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1d.1"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #26 (USB Controller)

63: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: FZIx.RTX9xWW_uz4
  Parent ID: mvRC.eb0OsiAXUP4
  SysFS ID: /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
  SysFS BusID: 8-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.39-0-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.39-0-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1d.2"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #27 (USB Controller)

64: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: wkjR.nabxKFUyBl4
  Parent ID: k4bc.cO89g+iefn1
  SysFS ID: /devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5:1.0
  SysFS BusID: 1-5:1.0
  Hardware Class: unknown
  Model: "Chicony Electronics CKF7063"
  Hotplug: USB
  Vendor: usb 0x04f2 "Chicony Electronics Co., Ltd"
  Device: usb 0xb083 "CKF7063"
  Revision: "33.19"
  Serial ID: "SN0001"
  Driver: "uvcvideo"
  Driver Modules: "uvcvideo"
  Device File: /dev/input/event6
  Device Files: /dev/input/event6, /dev/input/by-id/usb-Chicony_Electronics_Co.__Ltd._CKF7063_SN0001-event-if00, /dev/input/by-path/pci-0000:00:1a.7-usb-0:5:1.0-event
  Device Number: char 13:70
  Speed: 480 Mbps
  Module Alias: "usb:v04F2pB083d3319dcEFdsc02dp01ic0Eisc01ip00"
  Driver Info #0:
    Driver Status: uvcvideo is active
    Driver Activation Cmd: "modprobe uvcvideo"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #56 (Hub)

66: USB 00.0: 11500 Bluetooth Device
  [Created at usb.122]
  Unique ID: KRJj.Rx769wQkUX9
  Parent ID: uIhY.MxUuepIFPaE
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0
  SysFS BusID: 3-1:1.0
  Hardware Class: bluetooth
  Model: "HP Integrated Module"
  Hotplug: USB
  Vendor: usb 0x03f0 "HP"
  Device: usb 0x171d "HP Integrated Module"
  Revision: "1.00"
  Driver: "btusb"
  Driver Modules: "btusb"
  Speed: 12 Mbps
  Module Alias: "usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01"
  Driver Info #0:
    Driver Status: btusb is active
    Driver Activation Cmd: "modprobe btusb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #58 (Hub)

70: USB 00.0: 10503 USB Mouse
  [Created at usb.122]
  Unique ID: hhw5.m7C82g3gZbB
  Parent ID: FZIx.RTX9xWW_uz4
  SysFS ID: /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0
  SysFS BusID: 8-1:1.0
  Hardware Class: mouse
  Model: "USB OPTICAL MOUSE"
  Hotplug: USB
  Vendor: usb 0x15d9 
  Device: usb 0x0a4c "USB OPTICAL MOUSE"
  Revision: "1.00"
  Compatible to: int 0x0210 0x0013
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event4, /dev/input/by-id/usb-15d9_USB_OPTICAL_MOUSE-event-mouse, /dev/input/by-path/pci-0000:00:1d.2-usb-0:1:1.0-event-mouse, /dev/input/by-id/usb-15d9_USB_OPTICAL_MOUSE-mouse, /dev/input/by-path/pci-0000:00:1d.2-usb-0:1:1.0-mouse
  Device Number: char 13:63 (char 13:32)
  Speed: 1.5 Mbps
  Module Alias: "usb:v15D9p0A4Cd0100dc00dsc00dp00ic03isc01ip02"
  Driver Info #0:
    Buttons: 3
    Wheels: 1
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #63 (Hub)

71: PS/2 00.0: 10800 Keyboard
  [Created at input.161]
  Unique ID: 9ui9.+49ps10DtUF
  Hardware Class: keyboard
  Model: "AT Translated Set 2 keyboard"
  Vendor: 0x0001 
  Device: 0x0001 "AT Translated Set 2 keyboard"
  Compatible to: int 0x0211 0x0001
  Device File: /dev/input/event3
  Device Files: /dev/input/event3, /dev/input/by-path/platform-i8042-serio-0-event-kbd
  Device Number: char 13:67
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown

72: PS/2 00.0: 10500 PS/2 Mouse
  [Created at input.183]
  Unique ID: AH6Q.ZHI3OT7LsxA
  Hardware Class: mouse
  Model: "SynPS/2 Synaptics TouchPad"
  Vendor: 0x0002 
  Device: 0x0007 "SynPS/2 Synaptics TouchPad"
  Compatible to: int 0x0210 0x0002
  Device File: /dev/input/mice (/dev/input/mouse1)
  Device Files: /dev/input/mice, /dev/input/mouse1, /dev/input/event9, /dev/input/by-path/platform-i8042-serio-4-event-mouse, /dev/input/by-path/platform-i8042-serio-4-mouse
  Device Number: char 13:63 (char 13:33)
  Driver Info #0:
    Buttons: 2
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

73: None 00.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 6.23.10 "Intel(R) Core(TM)2 Duo CPU     T6570  @ 2.10GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,nx,lm,constant_tsc,arch_perfmon,pebs,bts,aperfmperf,pni,dtes64,monitor,ds_cpl,vmx,est,tm2,ssse3,cx16,xtpr,pdcm,sse4_1,xsave,lahf_lm,ida,dts
  Clock: 1200 MHz
  BogoMips: 4189.21
  Cache: 2048 kb
  Units/Processor: 2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

74: None 01.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: wkFv.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 6.23.10 "Intel(R) Core(TM)2 Duo CPU     T6570  @ 2.10GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,nx,lm,constant_tsc,arch_perfmon,pebs,bts,aperfmperf,pni,dtes64,monitor,ds_cpl,vmx,est,tm2,ssse3,cx16,xtpr,pdcm,sse4_1,xsave,lahf_lm,ida,dts
  Clock: 1200 MHz
  BogoMips: 4189.45
  Cache: 2048 kb
  Units/Processor: 2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

75: None 00.0: 10700 Loopback
  [Created at net.124]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

76: None 00.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.sA9iTwyxNq9
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.5/0000:86:00.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "sky2"
  Driver Modules: "sky2"
  Device File: eth0
  HW Address: 00:24:81:54:1a:9f
  Link detected: no
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #35 (Ethernet controller)

77: None 00.0: 1070a WLAN
  [Created at net.124]
  Unique ID: AYEt.QXn1l67RSa1
  Parent ID: y9sn.GbTjk0YbA70
  SysFS ID: /class/net/wlan0
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.1/0000:03:00.0
  Hardware Class: network interface
  Model: "WLAN network interface"
  Driver: "iwlagn"
  Driver Modules: "iwlagn"
  Device File: wlan0
  HW Address: 00:22:fa:41:86:64
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #34 (WLAN controller)
```

---

### Post by jtarin on 2011-06-17
He,he....it's a [ATI Mobility RadeonTM HD 3430]("http://www.hp.com/hpinfo/newsroom/press_kits/2008/connecting/ds_bn_6530s.pdf")......but I find no update for the proprietary. Maybe someone else knows.

---

### Post by mellouli on 2011-06-17
> **jtarin said:**
> He,he....it's a [ATI Mobility RadeonTM HD 3430]("http://www.hp.com/hpinfo/newsroom/press_kits/2008/connecting/ds_bn_6530s.pdf")......but I find no update for the proprietary. Maybe someone else knows.
yeah i know that .I hope to find someone who knows how to solve this problem

---

### Post by Quackers on 2011-06-17
The fan that you hear running may be your graphics card fan, not the cpu fan.
I have no experience with the ATI drivers, but I would look into removing all ATI/fglrx drivers and see if the fan speed reduces. I appreciate that there will be a loss in video performance, but it may give you an answer.

---

### Post by jtarin on 2011-06-17
> **Quackers said:**
> The fan that you hear running may be your graphics card fan, not the cpu fan.
I have no experience with the ATI drivers, but I would look into removing all ATI/fglrx drivers and see if the fan speed reduces. I appreciate that there will be a loss in video performance, but it may give you an answer.That was the direction I was headed...graphics fan/overheating due to faulty driver.;)

---

### Post by Quackers on 2011-06-17
That sounds reasonable to me :-)
I'm just not sure about what needs to be done other than removing the driver. Maybe remove xorg.conf too? - not sure with fglrx

---

### Post by jtarin on 2011-06-17
> **Quackers said:**
> That sounds reasonable to me :-)
I'm just not sure about what needs to be done other than removing the driver. Maybe remove xorg.conf too? - not sure with fglrx
Possibly, but as he is running 11.04 I would hazard a guess... older box and newest distro:(
As the "[Magic 8 ball]("http://8ball.ofb.net/")" says, "Outlook not so good".

---

### Post by mellouli on 2011-06-18
> **Quackers said:**
> That sounds reasonable to me :-)
I'm just not sure about what needs to be done other than removing the driver. Maybe remove xorg.conf too? - not sure with fglrx
so can someone who knows help me?

---

### Post by jtarin on 2011-06-18
> **mellouli said:**
> so can someone who knows help me?
You have installed 11.04.....this not a LTS release, in fact it is a great departure from the Ubuntu we have grown accustomed too. Not much is known about the difficulties of running it, compared to the previous versions. I would advise you to install something like 10.04 and as you learn, upgrade a step at a time or do your homework or this one.

---

### Post by mellouli on 2011-06-18
> **jtarin said:**
> You have installed 11.04.....this not a LTS release, in fact it is a great departure from the Ubuntu we have grown accustomed too. Not much is known about the difficulties of running it, compared to the previous versions. I would advise you to install something like 10.04 and as you learn, upgrade a step at a time or do your homework or this one.
I also had the same problem with ubuntu 10.4 lts
so what's the difference

---

### Post by jtarin on 2011-06-18
> **mellouli said:**
> I also had the same problem with ubuntu 10.4 lts
so what's the difference
You say you had the same experience with 10.04.....will I guess in your case there is no difference.

---

### Post by mellouli on 2011-06-18
> **jtarin said:**
> You say you had the same experience with 10.04.....will I guess in your case there is no difference.
yeah i hope with every new version off ubuntu to fix that problem but nothing happened
i tried to install opensuse but there is kworkers problem and the cpu is overload
with fedora the samz thing and when i installed the ati driver it became very slow and the cpu overload
However, Ihave a hp 4510s probook and everything worked fine with it but hp compact 6830s nothing worked only windows when I installed the proper driver of ati not from the instruction from official site but from the officiel site of hp everything worked fine since then
but hp doesn't provide ati drivers for linux this sucks
and ubuntu doesn't fix this bug

---

### Post by Quackers on 2011-06-18
How did you install the video driver in the pc with the fan running all the time?
Via additional Drivers? If so run Additional drivers again and de-activate the driver.
Or go through synaptic package manager and remove everything regarding fglrx.

On a different point, how can Ubuntu "fix this bug" if it's a fglrx driver problem? They don't write the graphics driver.

---

### Post by mellouli on 2011-06-18
> **Quackers said:**
> How did you install the video driver in the pc with the fan running all the time?
Via additional Drivers? If so run Additional drivers again and de-activate the driver.
Or go through synaptic package manager and remove everything regarding fglrx.

On a different point, how can Ubuntu "fix this bug" if it's a fglrx driver problem? They don't write the graphics driver.
  I installed both of 

[LIST]
[*] **"Ubuntu-X"** : This PPA offers the latest stable releases of video driver-related components. Follow the instructions at: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
[*] **Xorg-edgers**: This bleeding-edge PPA offers video  driver-related components straight from their code (git) repositories.  Follow the instructions at: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
[/LIST]
the ubuntu-x is faster with compiz effects but has the kworker problem only if i suspend the computer and run it again

Xorg-edgers is slow with compiz effects but doesn't show the kworker overload cpu

---

### Post by mellouli on 2011-06-18
> **Quackers said:**
> How did you install the video driver in the pc with the fan running all the time?
Via additional Drivers? If so run Additional drivers again and de-activate the driver.
Or go through synaptic package manager and remove everything regarding fglrx.

On a different point, how can Ubuntu "fix this bug" if it's a fglrx driver problem? They don't write the graphics driver.
i installed fglrx like you said and the same ptoblem

---

### Post by mellouli on 2011-06-18
bump

---

### Post by jtarin on 2011-06-18
[Your not the only one with FGLRX and kworker problems.]("http://www.google.com/search?client=ubuntu&channel=fs&q=kworker&ie=utf-8&oe=utf-8")

---

### Post by mellouli on 2011-06-18
> **jtarin said:**
> [Your not the only one with FGLRX and kworker problems.]("http://www.google.com/search?client=ubuntu&channel=fs&q=kworker&ie=utf-8&oe=utf-8")
i know that and that's the reason of writing this thread 
and i searched the whole web and  every bug but never found what i'm looking for:(:(:(:(:(

---

### Post by jtarin on 2011-06-18
When I started with Linux/Unix over 13 years ago there was only one video card at the time that would work 100% of the time .....the S3. Every computer I had for about 2-3 years I had to swap out the video card. The Linux Hardware Compatibility List is the first place I go when contemplating buying new hardware or computer. I don't like surprises in my OS either if I can avoid them. Things just need to fit sometime.

---

### Post by mellouli on 2011-06-18
> **jtarin said:**
> When I started with Linux/Unix over 13 years ago there was only one video card at the time that would work 100% of the time .....the S3. Every computer I had for about 2-3 years I had to swap out the video card. The Linux Hardware Compatibility List is the first place I go when contemplating buying new hardware or computer. I don't like surprises in my OS either if I can avoid them. Things just need to fit sometime.
so you're saying ati is not compatible with linux
I'll say no because i have an other laptop with ati card too but the problem was the battery in lasts only 2 hours but 6 hours in windows:(:(:(
but windows isn't a solution because it's the problem of every single thing in any laptop

---

### Post by mellouli on 2011-06-19
I did that
downgraded to lucid 10.4.2
found that that the fan stopped running when i left the laptop for 15 mins 
i created a script to stop the fan and it's like that
```
while true 
do
value=`cat $cat /sys/class/thermal/thermal_zone0/temp`
if [ $value -le "50000" ]
then
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:00/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:0a/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:01/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:02/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:03/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:04/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:05/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:06/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:07/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:08/thermal_cooling/cur_state
echo 0 >/sys/bus/acpi/drivers/fan/PNP0C0B:09/thermal_cooling/cur_state
echo "$value It's cool man!"
else
echo "$value Not cool at all"
echo 1 >/sys/bus/acpi/drivers/fan/PNP0C0B:00/thermal_cooling/cur_state
sleep 30s
fi
sleep 10s
done
```

and sensors show

```
ubuntu@lucid:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +47.0°C  (crit = +110.0°C)                  
temp2:       +43.0°C  (crit = +256.0°C)                  
temp3:       +49.0°C  (crit = +112.0°C)                  
temp4:       +51.0°C  (crit = +105.0°C)                  
temp5:       +31.9°C  (crit = +112.0°C)                  
temp6:       +20.0°C  (crit = +110.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +45.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +44.0°C  (high = +105.0°C, crit = +105.0°C)  

```an I not cookin my laptop,

---

### Post by mellouli on 2011-06-19
At least tell me what i did is right or wrong

---

### Post by jtarin on 2011-06-19
If it works....it's looks good. Good work.

---

### Post by mellouli on 2011-06-19
> **jtarin said:**
> If it works....it's looks good. Good work.
yeah it worked good with lucid and the fan is more quieter and it runs at maximum for 1 min in full speed like I wrote in the script
what i'm now is the temperature good or not
and i set the fan alway on from the bios and it's a quest mode without that option it's always 55 
but now most of the time is like that

```
ubuntu@lucid:~/compiz$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +49.0°C  (crit = +110.0°C)                  
temp2:       +52.0°C  (crit = +256.0°C)                  
temp3:       +52.0°C  (crit = +112.0°C)                  
temp4:       +51.0°C  (crit = +105.0°C)                  
temp5:       +30.3°C  (crit = +112.0°C)                  
temp6:       +20.0°C  (crit = +110.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +48.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +47.0°C  (high = +105.0°C, crit = +105.0°C)  

```

---

### Post by sammiev on 2011-06-19
My i5 runs at about 46c while running win7 before fan turns on and seems to stay under 56c at all times. ( fan may run at about 25% at upper temps. )
With linux the fan turns on between 49 and 52c and seems to stay under 60c under heavy loads and again likely running at about 25% to 50% fan speed. GL :)

---

### Post by mellouli on 2011-06-19
> **sammiev said:**
> My i5 runs at about 46c while running win7 before fan turns on and seems to stay under 56c at all times. ( fan may run at about 25% at upper temps. )
With linux the fan turns on between 49 and 52c and seems to stay under 60c under heavy loads and again likely running at about 25% to 50% fan speed. GL :)
that's more reasonable for my case it tuned on fo 45 and off on 38 with was not acceptable and made it run all the time with the script iwrote it turn on in full speed on 50 and stops after 30 sec and stops when the temperature is less than 50 
thank u the information

---

### Post by jtarin on 2011-06-19
> **mellouli said:**
> I did that
downgraded to lucid 10.4.2
found that that the fan stopped running when i left the laptop for 15 mins 
i created a script to stop the fan and it's like that
an I not cookin my laptop,
Isn't it great to have control like that over your system? Not like other OS's where you have no idea what they are controlling.:P
Mark this thread as solved. It will help someone else. You might think about writing a tutorial on this procedure of writing the script and entering it.......[Here.]("http://ubuntuforums.org/forumdisplay.php?f=100")

---

### Post by mellouli on 2011-06-19
> **jtarin said:**
> Isn't it great to have control like that over your system? Not like other OS's where you have no idea what they are controlling.:P
yeah that what I love the most about linux

---

### Post by jtarin on 2011-06-19
> **mellouli said:**
> yeah that what I love the most about linuxI edited my last post...take a look.:p

---

### Post by mellouli on 2011-06-19
thanks a lot

---

### Post by mellouli on 2011-06-19
Heyyyyyyyyyy I found a solution even better 
runnig the ubuntu notebook edition in lucid is the best and my laptop is quiet without any script even better than lxde
I shared to let u all know
I love working in Open source
Look at the temperature now never reached before in linux  on my laptop
```
root@lucid:/home/ubuntu# sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +110.0°C)                  
temp2:       +44.0°C  (crit = +256.0°C)                  
temp3:       +41.0°C  (crit = +112.0°C)                  
temp4:       +43.0°C  (crit = +105.0°C)                  
temp5:       +30.2°C  (crit = +112.0°C)                  
temp6:      +20.0°C  (crit = +110.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +38.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +37.0°C  (high = +105.0°C, crit = +105.0°C)  

root@lucid:/home/ubuntu# 
```

---

### Post by Quackers on 2011-06-19
That's good news :-)
Well done :-)

---

### Post by pqwoerituytrueiwoq on 2011-06-19
my guess is it is cooler cause it uses metacity and not compiz and all its prettiness

---

### Post by mellouli on 2011-06-20
> **pqwoerituytrueiwoq said:**
> my guess is it is cooler cause it uses metacity and not compiz and all its prettiness
look today it's even cooler than windows I'm excited 
:P:P:P:P:P:P
```
root@lucid:/home/ubuntu# sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +34.0°C  (crit = +110.0°C)                  
temp2:       +30.0°C  (crit = +256.0°C)                  
temp3:       +36.0°C  (crit = +112.0°C)                  
temp4:       +36.0°C  (crit = +105.0°C)                  
temp5:       +26.8°C  (crit = +112.0°C)                  
temp6:       +20.0°C  (crit = +110.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +32.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +32.0°C  (high = +105.0°C, crit = +105.0°C)  


```I heard that ubuntu in the next versions will use metacity instead of compiz

is there any other interfaces with metacity?

---

