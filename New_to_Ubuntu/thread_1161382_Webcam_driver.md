---
title: "Webcam driver"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by tdietz87 on 2009-05-16
I have a sony vaio with a built in webcam. I however cannot access ut in linux.  anybody know how to fix this?  I've been searching for a good tut on how to find and install correct drivers, but came up with nothing that can help me

sony vaio vgn-fw351j

---

### Post by guywithcable on 2009-05-16
Can you post the output from
```
lspci
```

---

### Post by Locutus_of_Borg on 2009-05-16
output of 'lsusb' please

though you probably just need the uvcvideo module

```
sudo modprobe uvcvideo
```

then 
```
mplayer tv:// 
```
to test it

---

### Post by tdietz87 on 2009-05-16
> **guywithcable said:**
> Can you post the output from
```
lspci
```

Output:

```

troy@troy-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
05:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 14)
09:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
troy@troy-laptop:~$ 

```

---

### Post by tdietz87 on 2009-05-16
> **Locutus_of_Borg said:**
> output of 'lsusb' please

though you probably just need the uvcvideo module

```
sudo modprobe uvcvideo
```then 
```
mplayer tv:// 
```to test it
```

troy@troy-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 044e:3017 Alps Electric Co., Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:183d Ricoh Co., Ltd 
troy@troy-laptop:~$ 

```

I also tried your suggestion...dont think it worked.

```

troy@troy-laptop:~$ sudo modprobe uvcvideo
[sudo] password for troy: 
troy@troy-laptop:~$ mplayer tv://
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz (Family: 6, Model: 23, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: UVC Camera (05ca:183d)
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
FPS not specified in the header or invalid, use the -fps option.
No stream found.

v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.

Exiting... (End of file)
troy@troy-laptop:~$ 

```


Any ideas guys?

---

### Post by guywithcable on 2009-05-16
Can you show me the output of both
```
dmesg | grep -i -E .*(video|uvc|webcam)+.*
```
and
```
ls -l /dev/video*
```

---

### Post by guywithcable on 2009-05-16
Oh, and to test it, use
```
sudo apt-get install cheese
```
Then open Cheese from Applications->Graphics and try all the devices under Edit->Preferences->Camera.

---

### Post by tdietz87 on 2009-05-16
> **guywithcable said:**
> Can you show me the output of both
```
dmesg | grep -i -E .*(video|uvc|webcam)+.*
```and
```
ls -l /dev/video*
```
```

troy@troy-laptop:~$ dmesg | grep -i -E .*(video|uvc|webcam)+.*
[    1.447334] pci 0000:00:02.0: Boot video device
[    7.992721] sony-laptop: brightness ignored, must be controlled by ACPI video driver
[    8.110965] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2b/input/input6
[    8.114377] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    8.174537] Linux video capture interface: v2.00
[    8.373659] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183d)
[    8.375546] input: UVC Camera (05ca:183d) as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input8
[    8.376113] usbcore: registered new interface driver uvcvideo
[    8.376136] USB Video Class driver (v0.1.0)
troy@troy-laptop:~$ ls -l /dev/video*
crw-rw----+ 1 root video 81, 0 2009-05-16 22:30 /dev/video0
troy@troy-laptop:~$ 

```

---

### Post by tdietz87 on 2009-05-16
> **guywithcable said:**
> Oh, and to test it, use
```
sudo apt-get install cheese
```Then open Cheese from Applications->Graphics and try all the devices under Edit->Preferences->Camera.
okay it is now working in cheese but not  flash.  I am confused as to why linux wont work with neave.com/webcam because it runs all the other flash files flawlessly but when i boot in vista, the webcam works fine at the listed url  


any ideas why?

---

### Post by guywithcable on 2009-05-16
It works for me and I have a UVC webcam. What version of flash are you using? In Firefox, go to Tools->Addons->Plugins->Shockwave Flash.

---

### Post by tdietz87 on 2009-05-16
> **guywithcable said:**
> It works for me and I have a UVC webcam. What version of flash are you using? In Firefox, go to Tools->Addons->Plugins->Shockwave Flash.
hmmm...I have 10.0 which if memory serves me right should be the latest.  I remember when I installing firefox I also followed a few "secure firefox" tuts such as no script and disable google ads.  But when I allow the page in no script and flash plays I feel like its no longer being blocked.  I dont know, I'm new to linux.

---

### Post by guywithcable on 2009-05-16
What do you get when you go here? [http://www.swift-tools.net/Blog/webcamtest.html](http://www.swift-tools.net/Blog/webcamtest.html)

---

### Post by 3rdalbum on 2009-05-16
Flash Player doesn't work with all webcams on Linux; I don't know why.

---

### Post by tdietz87 on 2009-05-17
> **guywithcable said:**
> What do you get when you go here? [http://www.swift-tools.net/Blog/webcamtest.html](http://www.swift-tools.net/Blog/webcamtest.html)
that works.  how strange.  thanks for the link.  When I try neave.com/webcam the videos around load and the center is black and the flash prompts me "warning someones trying to access your camera" and when I try to click allow it won't do anything...hmmm..i dont know.

---

### Post by guywithcable on 2009-05-17
Strange. Maybe you should [make a bug report]("http://www.adobe.com/cfusion/mmform/index.cfm?name=wishform").

---

