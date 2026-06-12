---
title: "Please help me to change my screen resolution into 1152x864 or higher"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by nirangad on 2009-11-18
I am new to Ubuntu. I've just installed Ubuntu 9.1 and stuck in 1024x768 screen resolution. In System > Preferences > Display shows 1024x768 as the maximum screen resolution that i can get :(

Following is what i got from lspci:

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

And im having a NEC 16'' CRT monitor.

Before installing Ubuntu 9.1, i tried using 9.04. It allows me to change screen resolution into 1152x864. Also the Windows XP allows me to select higher screen resolutions...

I tried almost everything that i found in similar threads :( :'(. I found out that there is no xorg.conf in [FONT=monospace][I]/etc/X11/.

[/I][/FONT]Please help me with this problem.

---

### Post by nirangad on 2009-11-20
:(

---

### Post by Tomone on 2009-11-21
I'm not sure about the screen resolution thing, but as far as the xorg.conf file not being there, it's because it's not always necessary (at least for most people). Only for some setups/hardware is an xorg.conf file needed. If I had to guess as to what's keeping you from choosing the correct resolution, I'd guess that it's a driver problem, but that's just a guess.

---

### Post by jacobs444 on 2009-11-21
what size monitor do you have?

---

### Post by ST3ALTHPSYCH0 on 2009-11-21
The machine will use an xorg.conf file if it's there, but most monitors are auto detected (but when they're not things suck). If you want to take the time to create your xorg.conf file manually [here's](http://ubuntuforums.org/showthread.php?t=1319491&page=4;%20postcount=38) a great tutorial in post #38. I was lazy and downloaded a copy of 8.04LTS to use a tool they had built in to that version. [Here's](http://ubuntuforums.org/showthread.php?p=8280317#post8280317) my how-to for that.
Good luck.

---

### Post by nirangad on 2009-11-21
Hi all,
So sorry for taking too much time to reply...

To Tomone:
Thank you for your reply.. 
If it is a driver problem, can you please help me to fix it? I don't know what to do about that.. :(

To jacobsbollocks:
I'm having a 17 inch CRT monitor (Flat screen). Do you think the problem is with the monitor? but Ubuntu 9.04 and Windows Xp allows me to select higher the resolution
Thanks a lot for replying :)

To ST3ALTHPSYCH0:
Thanks a lot for the links you gave me.. :) I will try to follow those instructions and get back to you if I couldn't fix it even after that.. Thanks a lot..

---

### Post by Tomone on 2009-11-21
I've looked it up a little and I think that Stealthpsycho has it right with xorg.conf. (I had immediately thought "drivers" at first because my dad recently had a resolution problem with his Vista machine and it turned out to be a driver problem)

---

### Post by sgosnell on 2009-11-21
Have you gone to System/Preferences/Display, and clicked on Detect Monitors?  That should find the proper monitor and display capabilities, but it doesn't always work.

---

### Post by nirangad on 2009-11-22
Hi all,

Thanks a lot for spending your valuable time on helping me... I really appreciate that.. :)
I found a way to fix my resolution problem by going through [http://ubuntuforums.org/showthread.php?t=1319491&page=4;%20postcount=38](http://ubuntuforums.org/showthread.php?t=1319491&page=4;%20postcount=38) and [http://ubuntuforums.org/showthread.php?p=8280317#post8280317](http://ubuntuforums.org/showthread.php?p=8280317#post8280317) links :)

I'll tell you what I did to solve it in steps

I stopped the X 
```
 sudo /etc/init.d/gdm stop
```Then i created a new xorg.conf by
```
sudo X -configure
```Then i restarted the X
```
sudo /etc/init.d/gdm start
```I want to change the resolution into 1152x864. So i opened a terminal and typed,
```
~$ cvt 1152 864 60
```(60 is frequency in Hz)
I got following lines as the result,
```
# 1152x864 59.96 Hz (CVT 1.00M3) hsync: 53.78 kHz; pclk: 81.75 MHz
Modeline "1152x864_60.00"   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync
```I pasted the "Modeline" line in the Monitor section
```
Section "Monitor"
    Identifier   "Monitor0"
    Modeline "1152x864_60.00"   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection
```After that I restarted the X
```
sudo /etc/init.d/gdm restart
```Then i went to System > Preferences > Display 
The option for changing the resolution into 1152x864 is there...!!!!!! :)

Thanks to you guys now I'm using the resolution I wanted... :)
Thanks again.... :)

---

