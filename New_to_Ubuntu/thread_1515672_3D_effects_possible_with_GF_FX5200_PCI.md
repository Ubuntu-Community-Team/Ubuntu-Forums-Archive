---
title: "3D effects possible with GF FX5200 PCI?"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by VoltRabbit on 2010-06-22
I know... a lot of you are wondering WTF PCI?

So I have this old P4 Compaq at work that has been out-moded.  I decided to use it for trying out linux distros whenever I was bored.  I recently installed Unbuntu 9.04 on it
and even more recently was handed a PCI slot GF FX5200 video card.  It works fine with no effects, but if I try to turn on even normal level Visual Effects I get an error stating Desktop Effects could not be enabled.

So, here's the deal:  The box is a company asset that has been dis-joined from the network, so I have no internet access to run updates (its a bare 9.04 install), also the card is installed in 90 degree pci bracket as the computer is a low profile style desktop. When I go to enable the Driver, there are no proprietary drivers found.

And heres the question: Can I use this pci video card to enable any desktop effects?  I just want to know if it should be possible before I actually invest the time in trying to figure it out.

---

### Post by sandyd on 2010-06-22
> **VoltRabbit said:**
> I know... a lot of you are wondering WTF PCI?

So I have this old P4 Compaq at work that has been out-moded.  I decided to use it for trying out linux distros whenever I was bored.  I recently installed Unbuntu 9.04 on it
and even more recently was handed a PCI slot GF FX5200 video card.  It works fine with no effects, but if I try to turn on even normal level Visual Effects I get an error stating Desktop Effects could not be enabled.

So, here's the deal:  The box is a company asset that has been dis-joined from the network, so I have no internet access to run updates (its a bare 9.04 install), also the card is installed in 90 degree pci bracket as the computer is a low profile style desktop. When I go to enable the Driver, there are no proprietary drivers found.

And heres the question: Can I use this pci video card to enable any desktop effects?  I just want to know if it should be possible before I actually invest the time in trying to figure it out.
**32bit**
Download
[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.25/NVIDIA-Linux-x86-173.14.25-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.25/NVIDIA-Linux-x86-173.14.25-pkg1.run)

onto a usb stick.
Drag it onto the computer's desktop.
When you startup ubuntu, and get to the login screen, press Control + ALT + F1
Login and type in
```

sudo killall gdm
sudo killall kdm
cd ~/Desktop
chmod 777 NVIDIA-Linux-x86-173.14.25-pkg1.run
sudo sh NVIDIA-Linux-x86-173.14.25-pkg1.run

```64bit
Download
[http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.25/NVIDIA-Linux-x86_64-173.14.25-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.25/NVIDIA-Linux-x86_64-173.14.25-pkg2.run)

onto a usb stick.
Drag it onto the computer's desktop.
When you startup ubuntu, and get to the login screen, press Control +  ALT + F1
Login and type in
```

sudo killall gdm
sudo killall kdm
cd ~/Desktop
cd ~/Desktop
chmod 777 NVIDIA-Linux-x86_64-173.14.25-pkg2.run
sudo sh NVIDIA-Linux-x86_64-173.14.25-pkg2.run
```or 

using envyng
```

sudo apt-get install envyng-core
sudo envyng -l
```

---

### Post by VoltRabbit on 2010-06-22
Thanks for responding!

I gave it a try but got an error.... something about an x server and needing to exit x. The installation failed.

I will have to follow up tomorrow, but thanks again Carlee!!! :guitar:

---

### Post by sandyd on 2010-06-22
> **VoltRabbit said:**
> Thanks for responding!

I gave it a try but got an error.... something about an x server and needing to exit x. The installation failed.

I will have to follow up tomorrow, but thanks again Carlee!!! :guitar:
oops.
fixing commands...

---

### Post by Perfect Storm on 2010-06-22
Note; If you're installing the drivers manually and updates the kernel - you have to re-install the driver again. If not you'll end up in CLI (command line interface).

---

### Post by Stigmata13 on 2010-06-23
I'm not to sure about that specific card, but I do know that older stuff doesn't tend to be as supported in these newest releases. Your best bet would be to install a version like 8.10 or 8.04 if you really need the effects. I can't guarantee that you would but I do believe you would have a better chance of it working out of the box.

---

### Post by VoltRabbit on 2010-06-23
> **carlee said:**
> oops.
fixing commands...

Okay, so I follow these directions but get stuck after the sudo init 1, it takes me to a recovery menu, not a terminal. 

32bit
Download
[http://us.download.nvidia.com/XFree8...14.25-pkg1.run](http://us.download.nvidia.com/XFree8...14.25-pkg1.run)

onto a usb stick.
Drag it onto the computer's desktop.
run

Code:
sudo init 1which will drop you to a terminal.
log in if you have to, and run

Code:
cd ~/Desktop
chmod 777 NVIDIA-Linux-x86-173.14.25-pkg1.run
sudo sh NVIDIA-Linux-x86-173.14.25-pkg1.run


Maybe Im missing something...

---

### Post by VoltRabbit on 2010-06-23
> **Stigmata13 said:**
> I'm not to sure about that specific card, but I do know that older stuff doesn't tend to be as supported in these newest releases. Your best bet would be to install a version like 8.10 or 8.04 if you really need the effects. I can't guarantee that you would but I do believe you would have a better chance of it working out of the box.

I was thinking that too, but I'd like to face the challenge if its possible to fix as is.  If all else fails, Ill try an older version.

---

### Post by VoltRabbit on 2010-06-24
> **VoltRabbit said:**
> Okay, so I follow these directions but get stuck after the sudo init 1, it takes me to a recovery menu, not a terminal. I don't know how to proceed from here

32bit
Download
[http://us.download.nvidia.com/XFree8...14.25-pkg1.run](http://us.download.nvidia.com/XFree8...14.25-pkg1.run)

onto a usb stick.
Drag it onto the computer's desktop.
run

Code:
sudo init 1which will drop you to a terminal.
log in if you have to, and run

Code:
cd ~/Desktop
chmod 777 NVIDIA-Linux-x86-173.14.25-pkg1.run
sudo sh NVIDIA-Linux-x86-173.14.25-pkg1.run


Maybe Im missing something...

Could anyone elaborate on these directions?

---

### Post by sandyd on 2010-06-24
> **VoltRabbit said:**
> Okay, so I follow these directions but get stuck after the sudo init 1, it takes me to a recovery menu, not a terminal. 

32bit
Download
[http://us.download.nvidia.com/XFree8...14.25-pkg1.run](http://us.download.nvidia.com/XFree8...14.25-pkg1.run)

onto a usb stick.
Drag it onto the computer's desktop.
run

Code:
sudo init 1which will drop you to a terminal.
log in if you have to, and run

Code:
cd ~/Desktop
chmod 777 NVIDIA-Linux-x86-173.14.25-pkg1.run
sudo sh NVIDIA-Linux-x86-173.14.25-pkg1.run


Maybe Im missing something...
i don't know what im typing. try the commands again... :-\"

---

### Post by mk1w86 on 2010-06-24
I have the AGP version of the Geforce FX5200 and am able to run compiz (this is on Ubuntu 9.04) so the GPU itself should be capable.  Proprietary drivers for the card were automatically found by the restricted driver manager so there might be a difference between the AGP and PCI versions of the card.  However it seems more likely that it is because the machine is not connected to the internet which is required to download the driver.

---

### Post by VoltRabbit on 2010-06-24
Yay Carlee!!! It worked

I owe you a cup of coffee, Thank You!):P

---

### Post by VoltRabbit on 2010-06-24
> **mk1w86 said:**
> I have the AGP version of the Geforce FX5200 and am able to run compiz (this is on Ubuntu 9.04) so the GPU itself should be capable.  Proprietary drivers for the card were automatically found by the restricted driver manager so there might be a difference between the AGP and PCI versions of the card.  However it seems more likely that it is because the machine is not connected to the internet which is required to download the driver.


Well, thanks to Carlee I have wobbly windows, i'll have to find a way to get this bad boy on the internet to get the packages updated if I want any more fancy effects. At least now the screensavers work, the onboard video is absolute trash.

---

### Post by sandyd on 2010-06-24
> **VoltRabbit said:**
> Yay Carlee!!! It worked

I owe you a cup of coffee, Thank You!):P
your welcome.

remember to redo the steps each time you get a new kernel k?

---

### Post by crasbelize on 2010-07-11
> **carlee said:**
> your welcome.

remember to redo the steps each time you get a new kernel k?

Hey guys....I can't get mine 2 work.

Here is the last part of the log....Please Help.

-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s).
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [   10.692383] registered panic notifier
   [   10.692391] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:04.0 on
   minor 0
   [   10.694948] vga16fb: initializing
   [   10.694954] vga16fb: mapped to 0xc00a0000
   [   10.694959] vga16fb: not registering due to another framebuffer present
   [   10.695530]   alloc irq_desc for 17 on node -1
   [   10.695534]   alloc kstat_irqs on node -1
   [   10.695544] CA0106 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ
   17
   [   10.695577] snd-ca0106: Model 1006 Rev 00000000 Serial 10061102
   [   10.764164] [drm] nouveau 0000:01:04.0: Setting dpms mode 0 on vga
   encoder (output 0)
   [   10.764170] [drm] nouveau 0000:01:04.0: Output VGA-1 is running on CRTC 0
   using output A
   [   10.824284] [drm] nouveau 0000:01:04.0: Setting dpms mode 0 on vga
   encoder (output 1)
   [   10.824291] [drm] nouveau 0000:01:04.0: Output DVI-I-1 is running on CRTC
   1 using output B
   [   10.836110] Console: switching to colour frame buffer device 128x48
   [   20.308007] eth0: no IPv6 routers present
   [  157.115813] nvidia: module license 'NVIDIA' taints kernel.
   [  157.115820] Disabling lock debugging due to kernel taint
   [  157.763715] NVRM: The NVIDIA probe routine was not called for 1
   device(s).
   [  157.763721] NVRM: This can occur when a driver such as rivafb, nvidiafb
   or
   [  157.763723] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
   [  157.763724] NVRM: device(s).
   [  157.763728] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel
   module
   [  157.763729] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
   [  157.763731] NVRM: support), then try loading the NVIDIA kernel module
   again.
   [  157.763734] NVRM: No NVIDIA graphics adapter probed!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by mörgæs on 2010-07-11
It is good that it worked, but I tend to disagree on the advice on using an obsolete Ubuntu. First of all, it is a security hazard. Second, only in very rare cases support for hardware is taken out of a new version. The main rule is that support is added, not removed.

Regarding the FX 5200, Ubuntu is moving towards open source drivers rather than closed, but one way or the other there is full support. 

I have a 9.10 running with the same graphics card, and everything worked out of the box. No manual compilations. Also tried a 10.04 live CD, and it also worked well.

Also it is very important to get internet access in order to download updates, and by far the best is to have wired access while installing. Regardless of which version you try, there are hundreds of updates waiting for you.

```
hwinfo --gfx
```gives

```

23: PCI 100.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_322
  Unique ID: VCu0.yj_UnUOuXl7
  Parent ID: vSkL.ITQqGs0XM26
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "nVidia GeForce FX 5200 (0x0322)"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0322 "GeForce FX 5200 (0x0322)"
  SubVendor: pci 0x10de "nVidia Corporation"
  SubDevice: pci 0x0192 
  Revision: 0xa1
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xfd000000-0xfdffffff (rw,non-prefetchable)
  Memory Range: 0xf0000000-0xf7ffffff (rw,prefetchable)
  Memory Range: 0xfea00000-0xfea1ffff (ro,prefetchable,disabled)
  IRQ: 16 (80507 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v000010DEd00000322sv000010DEsd00000192bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: nv
  Driver Info #1:
    XFree86 v4 Server Module: nvidia
    3D Support: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #10 (PCI bridge)

Primary display adapter: #23

```

---

### Post by mörgæs on 2010-07-11
Crasbelize, whith Ubuntu are you using, and could you please post the output of 
```
 hwinfo --gfx
```

---

### Post by crasbelize on 2010-07-11
> **mörgæs said:**
> Crasbelize, whith Ubuntu are you using, and could you please post the output of 
```
 hwinfo --gfx
```


I am using the latest version 10.04....including all the updates. 



Here is the output of that command: 

claud@claud-desktop:~$ hwinfo --gfx
09: PCI 02.0: 0380 Display controller                           
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_2562
  Unique ID: _Znp._BixbwRm0b2
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel i845"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2562 "i845"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0160 
  Revision: 0x01
  Memory Range: 0xd0000000-0xd7ffffff (rw,prefetchable,disabled)
  Memory Range: 0xfeb80000-0xfebfffff (rw,non-prefetchable,disabled)
  IRQ: 11 (no events)
  Module Alias: "pci:v00008086d00002562sv00001028sd00000160bc03sc80i00"
  Driver Info #0:
    XFree86 v4 Server Module: intel
  Driver Info #1:
    XFree86 v4 Server Module: intel
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown

18: PCI 104.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_322
  Unique ID: pe4v.OulUmtqJF76
  Parent ID: 6NW+.5o60iem1mwE
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:01:04.0
  SysFS BusID: 0000:01:04.0
  Hardware Class: graphics card
  Model: "nVidia GeForce FX 5200 (0x0322)"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0322 "GeForce FX 5200 (0x0322)"
  SubVendor: pci 0x196e 
  SubDevice: pci 0x01ad 
  Revision: 0xa1
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xfd000000-0xfdffffff (rw,non-prefetchable)
  Memory Range: 0xe0000000-0xefffffff (rw,prefetchable)
  Memory Range: 0xd8000000-0xd801ffff (ro,prefetchable,disabled)
  IRQ: 16 (46644 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v000010DEd00000322sv0000196Esd000001ADbc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: nv
  Driver Info #1:
    XFree86 v4 Server Module: nvidia
    3D Support: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (PCI bridge)

Primary display adapter: #18

---

### Post by mörgæs on 2010-07-11
What exactly is the problem? The drivers seem to be installed correctly.

---

### Post by crasbelize on 2010-07-12
> **mörgæs said:**
> What exactly is the problem? The drivers seem to be installed correctly.

all I had to do was install the latest version of compiz.

my only problem now is getting compiz to autostart.

---

### Post by diablo75 on 2010-07-12
I used to have a GeForce 5500 and 5600 Mobile and Compiz ran great on both of them, but older cards sometimes end up getting black listed.  I don't think the 5200 is quite THAT old, so you should be able to make use of it.

---

### Post by crasbelize on 2010-07-14
> **mörgæs said:**
> What exactly is the problem? The drivers seem to be installed correctly.

Ok...I still can't seem to get this thing 2 work the way I want it to.

I am using Ubuntu 10.04....I just finish re-installing it for the 4th time.
I feel good about all my installation....everything was install via Synaptic Package Manager and Ubuntu Software Center.

I installed awn-manager (Avant Window Navigator) & compizconfig settings manager.
Under APPEARANCE PREFERENCES > VISUAL EFFECTS....a fourth option appeared...it is the CUSTOM option:   

my fx5200 PCI card is install via HARDWARE DRIVERS and the version is 173.


PROBLEM: 3D just won't enable.....when I click on it......it says SEARCHING FOR AVAILABLE DRIVERS (why is it searching if the driver is already installed?).  Then I get a DESKTOP EFFECTS COULD NOT BE ENABLED.

I did have fusion installed and 3d was enable but it wouldn't autostart...and I don't want fusion nor emerald ...only compiz and 3d enable....Ubuntu 9 worked fine what is different in 10.04
 


Here is the output of HWINFO --GFX:

claud@claud-desktop:~$ hwinfo --gfx
09: PCI 02.0: 0380 Display controller                           
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_2562
  Unique ID: _Znp._BixbwRm0b2
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel i845"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2562 "i845"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0160 
  Revision: 0x01
  Memory Range: 0xd0000000-0xd7ffffff (rw,prefetchable,disabled)
  Memory Range: 0xfeb80000-0xfebfffff (rw,non-prefetchable,disabled)
  IRQ: 11 (no events)
  Module Alias: "pci:v00008086d00002562sv00001028sd00000160bc03sc80i00"
  Driver Info #0:
    XFree86 v4 Server Module: intel
  Driver Info #1:
    XFree86 v4 Server Module: intel
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown

18: PCI 104.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_322
  Unique ID: pe4v.OulUmtqJF76
  Parent ID: 6NW+.5o60iem1mwE
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:01:04.0
  SysFS BusID: 0000:01:04.0
  Hardware Class: graphics card
  Model: "nVidia GeForce FX 5200 (0x0322)"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0322 "GeForce FX 5200 (0x0322)"
  SubVendor: pci 0x196e 
  SubDevice: pci 0x01ad 
  Revision: 0xa1
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xfd000000-0xfdffffff (rw,non-prefetchable)
  Memory Range: 0xe0000000-0xefffffff (rw,prefetchable)
  Memory Range: 0xd8000000-0xd801ffff (ro,prefetchable,disabled)
  IRQ: 16 (96365 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v000010DEd00000322sv0000196Esd000001ADbc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: nv
  Driver Info #1:
    XFree86 v4 Server Module: nvidia
    3D Support: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (PCI bridge)

Primary display adapter: #18

---

### Post by mörgæs on 2010-07-14
This is only guessing:

Could this be because the Intel 845 screen card is making trouble? I know that you are trying to use the Nvidia card, but this is the only explanation I can think of.

Using Intel 845 in Ubuntu 10.04 takes some manual work:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)


In 9.10 there is no such problem for the Intel cards. If everything else fails, you can use this version almost a year from now.

---

### Post by fooman on 2010-07-14
> **crasbelize said:**
> my fx5200 PCI card is install via HARDWARE DRIVERS and the version is 173.


is that the only driver available via hardware drivers?  ...or the only one it will let you install?  i do not own a 5200,  so don't know what options they offer you.

if there are other drivers there...try a newer one.  use the "current version" one if it is there.

---

### Post by crasbelize on 2010-07-14
> **fooman said:**
> is that the only driver available via hardware drivers?  ...or the only one it will let you install?  i do not own a 5200,  so don't know what options they offer you.

if there are other drivers there...try a newer one.  use the "current version" one if it is there.

the only other version is 96....and i have tried that one...with the same result.

the version recommended is 173....which is the one I used.

---

### Post by crasbelize on 2010-07-14
> **mörgæs said:**
> This is only guessing:

Could this be because the Intel 845 screen card is making trouble? I know that you are trying to use the Nvidia card, but this is the only explanation I can think of.

Using Intel 845 in Ubuntu 10.04 takes some manual work:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)


In 9.10 there is no such problem for the Intel cards. If everything else fails, you can use this version almost a year from now.


well i love this new version.....and I would rather install fusion --icon and ran it manually ever time I log in if i have to.....because it works fine with fusion installed.

---

### Post by 3rdalbum on 2010-07-14
Try:

```
compiz --replace
```

---

### Post by crasbelize on 2010-07-14
> **3rdalbum said:**
> Try:

```
compiz --replace
```

ok this makes my whole system freezze up.  Then I have to do a hard reboot.

so what's the next move?  

Thanks so much for any help that comes my way....I really like ubuntu for my daily usage.

---

### Post by crasbelize on 2010-07-15
> **crasbelize said:**
> ok this makes my whole system freezze up.  Then I have to do a hard reboot.

so what's the next move?  

Thanks so much for any help that comes my way....I really like ubuntu for my daily usage.



Ok....I installed Compiz Fusion Icon.  And it works....

BUT: here is the problem.


[LIST=1]
[*]it will not autoload.
[*]it has to be manually load and then reloaded.
[/LIST]
QUESTION:  How do I get this thing to auto load...and then reload it's self?

O and the common method that is flying around doesn't work......Please Help!

---

### Post by Perfect Storm on 2010-07-15
What will not autoload? Compiz or fusion-icon?

If fusiob-icon, you can set it to autoload via 'Startup Applications'

If it's compiz you need to use gconf-editor to change the default windows manager.

---

### Post by fooman on 2010-07-15
don't know if it will help,  but in compizconfig settings manager > effects > window decorations

in the "command" space, type:

```
/usr/bin/compiz-decorator
```

see if that helps.

---

### Post by crasbelize on 2010-07-19
> **fooman said:**
> don't know if it will help,  but in compizconfig settings manager > effects > window decorations

in the "command" space, type:

```
/usr/bin/compiz-decorator
```see if that helps.


that's already in there.  

Thanks.

---

