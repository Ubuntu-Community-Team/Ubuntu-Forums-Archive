---
title: "No Sound - Gstreamer"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by Firepower-EX on 2009-11-13
```
GStreamer was unable to detect any sound devices. Some sound system specific GStreamer packages may be missing. It may also be a permissions problem.
```

This was the message displayed. I just googled it, but I am not very sure what to do. Any ideas?

Sound used to work under Ubuntu, but once I switched to xubuntu, it does not.

Any ideas?

---

### Post by coldReactive on 2009-11-13
In terminal: sudo apt-get install hardinfo

Then go to: Applications > System Tools > System Profiler and Benchmark > PCI Devices (on the left)

and tell us what your sound/audio devices are.

---

### Post by Firepower-EX on 2009-11-13
k just solved it by installing ubuntu-restricted-extras.

thanks!

edit: wait it doesnt work. instaling hardinfo

-PCI Devices-
Host bridge        : Intel Corporation 82855PM Processor to I/O Controller 
PCI bridge        : Intel Corporation 82855PM Processor to AGP Controller 
USB Controller        : Intel Corporation 82801DB/DBL/DBM 
USB Controller        : Intel Corporation 82801DB/DBL/DBM 
USB Controller        : Intel Corporation 82801DB/DBL/DBM 
USB Controller        : Intel Corporation 82801DB/DBM 
PCI bridge        : Intel Corporation 82801 Mobile PCI Bridge 
ISA bridge        : Intel Corporation 82801DBM 
IDE interface        : Intel Corporation 82801DBM 
Multimedia audio controller        : Intel Corporation 82801DB/DBL/DBM 
Modem        : Intel Corporation 82801DB/DBL/DBM 
VGA compatible controller        : nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] 
Ethernet controller        : Intel Corporation 82801DB PRO/100 VE 
CardBus bridge        : Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support 
CardBus bridge        : Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support 
System peripheral        : Toshiba America Info Systems SD TypA Controller

---

### Post by coldReactive on 2009-11-13
> **Firepower-EX said:**
> k just solved it by installing ubuntu-restricted-extras.

thanks!

Tell us anyway so that people with similar hardware as you know what to do.

---

### Post by Firepower-EX on 2009-11-13
oops. thought i i solved it with that package, cause it installed pulse audio, but it did not solve it.

any ideas?


output from hardinfo:

-Computer-
Processor        : Intel(R) Pentium(R) M processor 1500MHz
Memory        : 509MB (299MB used)
Operating System        : Ubuntu 9.10
User Name        : ilk (Ilk)
Date/Time        : Friday 13,November,2009 02:54:05 PM SGT
-Display-
Resolution        : 1024x768 pixels
OpenGL Renderer        : GeForce FX Go5200 32M/64M/AGP/SSE2
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : ICH4 - Intel 82801DB-ICH4
-Input Devices-
 Power Button
 Power Button
 Lid Switch
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 Video Bus
 Logitech USB-PS/2 Optical Mouse
 DualPoint Stick
 AlpsPS/2 ALPS DualPoint TouchPad
-Printers-
No printers found
-SCSI Disks-
ATA TOSHIBA MK4026GA
TEAC DW-224E-A

---

### Post by Soul-Sing on 2009-11-13
try this:
```
sudo apt-get install linux-ubuntu-modules-`uname -r`
```

---

### Post by thekingsw on 2009-11-13
I have same problem. This is my hardinfo:

-PCI Devices-
Host bridge		: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface 
PCI bridge		: Intel Corporation 82865G/PE/P PCI to AGP Controller 
System peripheral		: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface 
USB Controller		: Intel Corporation 82801DB/DBL/DBM 
USB Controller		: Intel Corporation 82801DB/DBL/DBM 
USB Controller		: Intel Corporation 82801DB/DBL/DBM 
USB Controller		: Intel Corporation 82801DB/DBM 
PCI bridge		: Intel Corporation 82801 PCI Bridge 
ISA bridge		: Intel Corporation 82801DB/DBL 
IDE interface		: Intel Corporation 82801DB 
SMBus		: Intel Corporation 82801DB/DBL/DBM 
Multimedia audio controller		: Intel Corporation 82801DB/DBL/DBM 
VGA compatible controller		: ATI Technologies Inc Radeon RV250 If [Radeon 9000] 
Ethernet controller		: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 


I also run:
   sudo apt-get install linux-ubuntu-modules-`uname -r` 
but it gave me this :
   Couldn't find package linux-ubuntu-modules-2.6.31-14-generic

I can't hear any sound from my computer. It seems lack of some package.
Help me!

---

### Post by orengolan on 2009-11-22
I installed xubuntu 9.10 and had sound but I lost it. 
I think it happened after installing ubuntu-restricted-extras and more stuff.

I removed it and installed xubuntu-restriced-extras but I still have the same issue as described by Firepower-EX.

when I type alsamixer i get:
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```

Here is some info about my system:
lspci |grep audio
```
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
```

aplay -l
```
aplay: device_list:223: no soundcards found...
```

sudo lshw -C multimedia
 ```
 *-multimedia            
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0
       resources: irq:17 ioport:d800(size=256) ioport:dc00(size=64) memory:f7fff800-f7fff9ff memory:f7fff400-f7fff4ff
```

any tips would be great!

---

### Post by XubuRoxMySox on 2009-11-22
Y'know it's weird... Exaile wouldn't play MP3s even though I had xubuntu restricted-extras installed... but when I installed _u_buntu restricted-extras, allofasudden it worked. Have no idea why. But try it! It might work for you too...

-Robin

---

### Post by QuestForKnowledge on 2010-03-05
> **Firepower-EX said:**
> ```
GStreamer was unable to detect any sound devices. Some sound system specific GStreamer packages may be missing. It may also be a permissions problem.
```

This was the message displayed. I just googled it, but I am not very sure what to do. Any ideas?

Sound used to work under Ubuntu, but once I switched to xubuntu, it does not.

Any ideas?

Sometimes Restarting your system will work....Better give it a try first...

---

### Post by weekend warrior on 2010-11-25
Check and make sure you have the GStreamer plugin for ALSA installed, current version is gstreamer0.10-alsa

---

### Post by whytek on 2011-04-29
Hey, I know it's a few months old.. but I just hit this problem after letting an old Xubuntu 9.04 installation in a vbox get all its updates. (Can't actually 100% confirm that sound was working before the updates, I'm pretty sure it was)

Anyway, it was permissions thing. The audio devices is /dev are owned by root, group audio. I added my user to the audio group with 

# usermod -aG audio user as root.

You can also do this via System -> Users and Groups -> Properites -> User Privileges -> Use audio devices. 

Thought it might be worth posting here as this thread came up in google.

---

### Post by matt3839 on 2011-12-03
> **whytek said:**
> Hey, I know it's a few months old.. but I just hit this problem after letting an old Xubuntu 9.04 installation in a vbox get all its updates. (Can't actually 100% confirm that sound was working before the updates, I'm pretty sure it was)

Anyway, it was permissions thing. The audio devices is /dev are owned by root, group audio. I added my user to the audio group with 

# usermod -aG audio user as root.

You can also do this via System -> Users and Groups -> Properites -> User Privileges -> Use audio devices. 

Thought it might be worth posting here as this thread came up in google.

Just thought I'd add that this also works perfectly on vanilla Xfce, and is presumably necessary because Xubuntu's default settings handle audio when installing the full DE.

---

### Post by oldos2er on 2011-12-03
And with that, we'll close. Anyone having this issue please start a new thread.

---

