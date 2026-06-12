---
title: "Help Installing 180.22 Nvidia Drivers"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Jerr on 2009-01-14
I am having so much trouble installing the drivers.  I have tried 3 times now and all it does is put me into low resolution mode type of deal and then I re install ubuntu..

Anyone have a concrete way of installing it?

Here is my lspci:

[SIZE="1"]00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
[/SIZE]

---

### Post by Jerr on 2009-01-14
Bump!

---

### Post by rajeev1204 on 2009-01-14
Which version of ubuntu are you using?

If ubuntu 8.10, you should install the driver version 177 or 173 from 

menu>system>administration>hardware drivers


Its easier to install.

---

### Post by Jerr on 2009-01-14
Thanks for the response!

I am using 8.10; I have a 8600gt. I tried using the 173's yet it makes my gfx look terrible and when I drag a window, it will lag and create mutiple windows.

---

### Post by Zakhafr on 2009-01-14
If you run the script from nVidia it's pretty simple.

But unfortunately, then Synaptic will not be aware you ran a script and will still give you updates. Updates will crash your video driver install.

So if you don't manage to install through nVidia script, just pray some one builds a package for Intrepid.

Alternately, you could also try this repository : [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180]("https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180")

It has got 180.18

I ask Thomas C (on nvNews) if he would consider updating his excellent work to 180.22 but got no response so far.

---

### Post by blue13130 on 2009-01-14
You can try these steps but it may screw up your machine and cause you to have to reinstall!

1. Download and save the nvidia 180.22 driver from their website

2. switch to terminal and stop GDM
press Ctrl+Alt+F1 to switch to terminal and login in with your username
type 'sudo /etc/init.d/gdm stop' this will stop the GDM server and stop X

3. remove all current nvidia drivers
type 'sudo apt-get remove --purge nvidia* linux-restricted-modules*'

4. run the downloaded driver installation
type 'sudo sh /path/to/downloaded/driver/NVIDIA-Linux-x86-180.22-pkg1.run' 
Follow the onscreen prompts

5. test installed driver
type 'startx' this will start X and see if the driver is working and resolution is correct

6. reboot
if the resolution is working well then you can cross your fingers and reboot!

If this works you will have to repeat steps 2,4-6 whenever the kernel is upgraded.  If you want to upgrade your driver when a new one is released you will have to repeat steps 1,2,4-6.

Hope this helps!
I am using Nvidia 180.22 in Ubuntu 8.04.1 with kernel 2.6.24-23 and this is my method of installing and maintaining my nvidia drivers.

---

