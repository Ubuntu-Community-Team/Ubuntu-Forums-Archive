---
title: "[SOLVED] Webcam in laptop"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by hmich176 on 2008-12-17
Hi, I'm running Ubuntu 8.04 on an HP Pavilion dv6120.  This version comes with a webcam.  I was wondering how I could get it to work on Ubuntu.  

Thanks for the help!

---

### Post by hmich176 on 2008-12-17
[http://ubuntuforums.org/showthread.php?t=829203](http://ubuntuforums.org/showthread.php?t=829203)

I found the thread above.  But, I still need help.  I don't know what program to use to begin with!

I've also found that Skype does not recognize that I have a webcam.  Any help would be great!

---

### Post by deputy on 2008-12-17
what exactly do you want to use your webcam for? Try xawtv to test your webcam and see if it works first.

---

### Post by hmich176 on 2008-12-17
> **deputy said:**
> what exactly do you want to use your webcam for? Try xawtv to test your webcam and see if it works first.

My friend is moving to Allentown; she has a webcam and Skype, so we'd like to talk over that. 


I'll try XawTV.  Tried to open it, but nothing happened.

---

### Post by adobrakic on 2008-12-17
> **deputy said:**
> what exactly do you want to use your webcam for? Try xawtv to test your webcam and see if it works first.

I'm sorry, but I really don't think what he wants to use the cam for is anyone else's business.

Anyway, going through [this](http://www.google.com/search?hl=en&safe=off&q=HP+Pavilion+dv6000+webcam+ubuntu&btnG=Search) might help, hmich176.

---

### Post by deputy on 2008-12-17
It's actually a suite of video programs to watch tv on linux. But you can use it to test and see if you can watch video from your webcam. To get it type this in a terminal:

```
sudo apt-get install xawtv
```

To test your webcam run this in a terminal:

```
xawtv /dev/video0
```

You should then see a window pop up and if your webcam is working you should be able to see from it. I have a pavilion dv6768, and mine works in Skype just fine. If you want to test in Skype first download it and install it. You can go their website or you can download UbuntuTweak. It's a gui program that lets you tweak a lot of your computer settings without having to use the terminal. [http://ubuntu-tweak.com](http://ubuntu-tweak.com) . It's really useful for first time Linux users.

---

### Post by xarte on 2008-12-17
I use camorama with my Logitech webcam. You'll find it in the 'add software' option, just search for it. Turn on camorama, then turn on Skype once Camorama is working.

I have found it rather erratic - sometimes having problems with a very dark picture. I think the last kernel update fixed that.

---

### Post by hmich176 on 2008-12-17
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-19-generic)
xinerama 0: 1280x800+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

That's what I got when I ran xawtv.

---

### Post by deputy on 2008-12-17
Can you post the results of:

```
lspci -v
```

---

### Post by deputy on 2008-12-17
Also the results of:

```
lsusb
```

---

### Post by hmich176 on 2008-12-17
> **deputy said:**
> Can you post the results of:

```
lspci -v
```
Here:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d8100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at d8200000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: bus master, fast devsel, latency 0
	Memory at d8180000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d8240000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d6000000-d7ffffff
	Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d4000000-d5ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at d8444000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d8000000-d80fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 221
	I/O ports at 18d0 [size=8]
	I/O ports at 18c4 [size=4]
	I/O ports at 18c8 [size=8]
	I/O ports at 18c0 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at d8444400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: medium devsel, IRQ 4
	I/O ports at 18e0 [size=32]

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 135b
	Flags: bus master, fast devsel, latency 0, IRQ 220
	Memory at d6000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at d8001000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

05:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at d8001800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

05:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: medium devsel, IRQ 3
	Memory at d8001c00 (32-bit, non-prefetchable) [disabled] [size=256]
	Capabilities: <access denied>

05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: medium devsel, IRQ 3
	Memory at d8002000 (32-bit, non-prefetchable) [disabled] [size=256]
	Capabilities: <access denied>

05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: medium devsel, IRQ 3
	Memory at d8002400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 30bb
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at d8000000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 4000 [size=64]
	Capabilities: <access denied>
```

---

### Post by hmich176 on 2008-12-17
> **deputy said:**
> Also the results of:

```
lsusb
```

Bus 005 Device 011: ID 05ca:1870 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 007: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by deputy on 2008-12-17
Ok, you have a Ricoh webcam. I found this website: [http://www.laptops-drivers.com/hp-laptop/how-to-integrated-pavilion-dv6000-with-ubuntu.html](http://www.laptops-drivers.com/hp-laptop/how-to-integrated-pavilion-dv6000-with-ubuntu.html) that has the instructions for installing the drivers for your webcam, basically you need to install svn:

```
sudo apt-get install subversion
```

And then do the following:

```
svn co http://svn.mediati.org/svn/r5u870/trunk ~/r5u870
cd ~/r5u870
sudo make
sudo make install
sudo modprobe r5u870
```

Afterward try xawtv again.

---

### Post by hmich176 on 2008-12-17
> **deputy said:**
> Ok, you have a Ricoh webcam. I found this website: [http://www.laptops-drivers.com/hp-laptop/how-to-integrated-pavilion-dv6000-with-ubuntu.html](http://www.laptops-drivers.com/hp-laptop/how-to-integrated-pavilion-dv6000-with-ubuntu.html) that has the instructions for installing the drivers for your webcam, basically you need to install svn:

```
sudo apt-get install subversion
```

And then do the following:

```
svn co http://svn.mediati.org/svn/r5u870/trunk ~/r5u870
cd ~/r5u870
sudo make
sudo make install
sudo modprobe r5u870
```

Afterward try xawtv again.

When I tried that, I got this:
```
~/r5u870$ sudo make
make -C /lib/modules/2.6.24-22-generic/build M=/home/harry/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-22-generic'
  CC [M]  /home/harry/r5u870/usbcam/usbcam_fops.o
/home/harry/r5u870/usbcam/usbcam_fops.c:24:30: error: media/v4l2-ioctl.h: No such file or directory
/home/harry/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_ioctl’:
/home/harry/r5u870/usbcam/usbcam_fops.c:1162: warning: unused variable ‘udp’
/home/harry/r5u870/usbcam/usbcam_fops.c: At top level:
/home/harry/r5u870/usbcam/usbcam_fops.c:1214: error: variable ‘this_cam_ops’ has initializer but incomplete type
/home/harry/r5u870/usbcam/usbcam_fops.c:1215: error: unknown field ‘vidioc_querycap’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1215: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1215: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1216: error: unknown field ‘vidioc_enum_fmt_vid_cap’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1216: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1216: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1217: error: unknown field ‘vidioc_g_fmt_vid_cap’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1217: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1217: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1218: error: unknown field ‘vidioc_s_fmt_vid_cap’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1218: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1218: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1219: error: unknown field ‘vidioc_try_fmt_vid_cap’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1219: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1219: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1220: error: unknown field ‘vidioc_reqbufs’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1220: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1220: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1221: error: unknown field ‘vidioc_querybuf’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1221: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1221: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1222: error: unknown field ‘vidioc_qbuf’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1222: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1222: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1223: error: unknown field ‘vidioc_dqbuf’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1223: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1223: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1224: error: unknown field ‘vidiocgmbuf’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1224: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1224: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1225: error: unknown field ‘vidioc_enum_input’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1225: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1225: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1226: error: unknown field ‘vidioc_streamon’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1226: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1226: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1227: error: unknown field ‘vidioc_streamoff’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1227: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1227: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1228: error: unknown field ‘vidioc_g_input’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1228: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1228: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1229: error: unknown field ‘vidioc_s_input’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1229: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1229: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1230: error: unknown field ‘vidioc_queryctrl’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1230: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1230: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1231: error: unknown field ‘vidioc_g_ctrl’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1231: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1231: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1232: error: unknown field ‘vidioc_s_ctrl’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1232: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1232: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1233: error: unknown field ‘vidioc_querymenu’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1233: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1233: warning: (near initialization for ‘this_cam_ops’)
/home/harry/r5u870/usbcam/usbcam_fops.c:1238: error: unknown field ‘vfl_type’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1240: error: unknown field ‘ioctl_ops’ specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1240: warning: initialization makes integer from pointer without a cast
make[3]: *** [/home/harry/r5u870/usbcam/usbcam_fops.o] Error 1
make[2]: *** [/home/harry/r5u870/usbcam] Error 2
make[1]: *** [_module_/home/harry/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
make: *** [all] Error 2

```

---

### Post by Maheriano on 2008-12-17
Install Cheese, that got mine working.

---

### Post by deputy on 2008-12-17
Do you have the build-essential package and linux headers installed?

```
sudo apt-get install build-essential build-dep linux-headers-$(uname -r)
```

Then try make again.

---

### Post by hmich176 on 2008-12-17
> **Maheriano said:**
> Install Cheese, that got mine working.

I installed it.  Where do I find it at?

---

### Post by deputy on 2008-12-17
Probably you have to run it from the command line. Otherwise under Sound & Video in the Ubuntu menu

---

### Post by hmich176 on 2008-12-17
> **deputy said:**
> Probably you have to run it from the command line. Otherwise under Sound & Video in the Ubuntu menu

Sorry - not very skilled in the code - at least, not yet.  

What code should I use to run from the command line?

---

### Post by hmich176 on 2008-12-17
> **hmich176 said:**
> Sorry - not very skilled in the code - at least, not yet.  

What code should I use to run from the command line?

Nevermind that post.  I got it to work.

However, the camera didn't work.  There was the multicolored bars, and then a bunch of snow in the lower right corner.

I got this code: 
```
(cheese:10040): GStreamer-CRITICAL **: gst_element_send_event: assertion `GST_IS_ELEMENT (element)' failed

```

---

### Post by llamakc on 2008-12-17
> **hmich176 said:**
> Sorry - not very skilled in the code - at least, not yet.  

What code should I use to run from the command line?

cheese

---

### Post by deputy on 2008-12-17
If installing the Ricoh drivers didn't work then you can try the uvc drivers:

```
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
make
sudo make install
sudo modprobe uvcvideo
```

Another question, exactly what model of laptop you have? I know it's a dv6000 series but for example mines a dv6768se. Do you know what your is?

---

### Post by hmich176 on 2008-12-17
When I type in cheese in the terminal, I get this: 
(gnome-video-thumbnailer:11645): GStreamer-CRITICAL **: gst_event_new_new_segment_full: assertion `start != -1' failed

(gnome-video-thumbnailer:11645): GStreamer-CRITICAL **: gst_event_new_new_segment_full: assertion `start != -1' failed

gnome-video-thumbnailer couldn't process file: 'file:///home/harry/.gnome2/cheese/media/0002.ogg'
Reason: Took too much time to process.

** (cheese:11643): WARNING **: could not load /home/harry/.gnome2/cheese/media/0002.ogg (video/x-theora+ogg)

---

### Post by deputy on 2008-12-17
It looks like no matter what program you use your webcam won't be working until you build and install drivers for it. I know Ubuntu 8.10 had these built it and I didn't have a problem using my webcam in skype. Have you searched through google or the forums for similar problems?

---

### Post by hmich176 on 2008-12-17
Tried, but didn't find much.  

Do you think I should upgrade to 8.10?

---

### Post by deputy on 2008-12-17
Hmm, one more thing can you post the output of:

```
sudo lshw
```

Upgrading can or not fix the problem. This command will give you more details about your hardware. We might be looking at the wrong drivers.

---

### Post by hmich176 on 2008-12-17
> **deputy said:**
> Hmm, one more thing can you post the output of:

```
sudo lshw
```

Upgrading can or not fix the problem. This command will give you more details about your hardware. We might be looking at the wrong drivers.

Gotcha!  
```
harry-laptop              
    description: Notebook
    product: HP Pavilion dv6000 (RG360UA#ABA)
    vendor: Hewlett-Packard
    version: Rev 1
    serial: CNF6451B7Y
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=434E4636-3435-3142-3759-00163697BDDA
  *-core
       description: Motherboard
       product: 30BB
       vendor: Quanta
       physical id: 0
       version: 66.21
       serial: None
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.08 (11/06/2006)
          size: 99KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           T2250  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U2E1
          size: 1733MHz
          capacity: 1733MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor est tm2 xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             physical id: 0
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM Synchronous 533 MHz (1.9 ns)
             physical id: 1
             slot: DIMM 2
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1733MHz
          capacity: 1733MHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 02
                serial: 00:18:de:76:23:1d
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=192.168.1.7 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 5
                bus info: pci@0000:05:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 5.1
                bus info: pci@0000:05:05.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-system:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 5.2
                bus info: pci@0000:05:05.2
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=ricoh-mmc latency=0 module=ricoh_mmc
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 5.3
                bus info: pci@0000:05:05.3
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
           *-generic UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 5.4
                bus info: pci@0000:05:05.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
           *-network
                description: Ethernet interface
                product: PRO/100 VE Network Connection
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:05:08.0
                logical name: eth0
                version: 02
                serial: 00:16:36:97:bd:da
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-4084N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KQ09
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: FUJITSU MHV2120B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 892C
                serial: NW9XT6A2KH5B
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=282d282d
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 0010770e-34f4-4be1-a638-6b8a8ab06264
                   size: 108GiB
                   capacity: 108GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-01-29 12:42:09 filesystem=ext3 modified=2008-12-17 16:31:34 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-12-03 15:06:43 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2933MiB
                   capacity: 2933MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2933MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```

Can someone at least tell me what this means: 
```
(gnome-video-thumbnailer:6759): GStreamer-CRITICAL **: gst_event_new_new_segment_full: assertion `start != -1' failed
```

---

### Post by hmich176 on 2008-12-18
I found [this thread]("http://ubuntuforums.org/showthread.php?t=617748"), but it offered no solutions.  

I really want to get this webcam working!

My laptop is a dv6120.

---

### Post by Maheriano on 2008-12-18
Are you running your webcam in a resolution/framerate not supported by it? That's what it looks like to me. Try messing with the options in Cheese and see if you can get the video to start. If not then check which chipset your webcam uses and see if that's supported in Ubuntu at all.

---

### Post by hmich176 on 2008-12-18
When it opened, the terminal gave me this message:
```
gnome-video-thumbnailer couldn't process file: 'file:///home/harry/.gnome2/cheese/media/0002.ogg'
Reason: Took too much time to process.

** (cheese:2239): WARNING **: could not load /home/harry/.gnome2/cheese/media/0002.ogg (video/x-theora+ogg)

```

How do I mess with the options in Cheese?  There doesn't seem to be any place for me to do that in the program.

---

### Post by deputy on 2008-12-18
Doesn't seem like Ubuntu is even recognizing your webcam from the looks of the lshw results. It should have been listed under the *-usb, but I don't see any mention of it in there. I think your best bet is to buy an external one. Have you checked out this [wiki]("https://help.ubuntu.com/community/Webcam")? Try the EasyCam script and see if it can find any drivers for your webcam.

---

### Post by hmich176 on 2008-12-18
Buying one really isn't an option at the moment. I'd like to try to get this working first. It seems like there's more that's going on that the webcam not being recognized by Ubuntu.

---

### Post by deputy on 2008-12-18
I understand, have you ever had the webcam working? Did you have windows before or something? Have you tried the EasyCam program from that wiki I posted?

---

### Post by rustutzman on 2008-12-18
Do you have the Windows driver (.inf) file for the camera? Open that file in text editor and paste that info here. It should list the sensor type. Once you have that you might get better direction for getting it working.

There are a couple of independent projects working with various sensors to get them working.

I think you might really want to consider the upgrade to 8.10 too. My experience has been that it helped with some hardware that was temperamental in 8.04.

aMSN works pretty good with a lot of cams in 8.10.

Russ

---

### Post by hmich176 on 2008-12-18
Tried EasyCam, and during the process I hit a wall.  Here's the code:
```
/home/harry/gspca-b9ad46be2923/v4l/tvp514x.c: In function 'ioctl_s_power':
/home/harry/gspca-b9ad46be2923/v4l/tvp514x.c:1238: error: dereferencing pointer to incomplete type
/home/harry/gspca-b9ad46be2923/v4l/tvp514x.c: At top level:
/home/harry/gspca-b9ad46be2923/v4l/tvp514x.c:1524: error: array type has incomplete element type
/home/harry/gspca-b9ad46be2923/v4l/tvp514x.c:1539: warning: initialization from incompatible pointer type
/home/harry/gspca-b9ad46be2923/v4l/tvp514x.c:1541: error: unknown field 'id_table' specified in initializer
make[3]: *** [/home/harry/gspca-b9ad46be2923/v4l/tvp514x.o] Error 1
make[2]: *** [_module_/home/harry/gspca-b9ad46be2923/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/harry/gspca-b9ad46be2923/v4l'
make: *** [all] Error 2

```

Beyond that, this laptop does not have Windows on it at all.  I bought it from a friend of mine who did, but, when he added another version of Linux, made the Windows portion to small to use.  So, I wiped the hard drive clean, installed Ubuntu 7.10, and bought it (for 50 bucks, no less!).  

Since then, I haven't tried using the webcam.  It has always been on of those things I've wanted to get working and use, but it's been a bottom feeder priority.  

So, now that it's not, I'm trying to get it to work.  

I'm going to upgrade to 8.10 anyway.  I suspect there is a larger problem in addition to the webcam issue, and I believe the upgrade would be a good solution to some of the problems.  (I upgraded to 8.04 the day it was released and encountered a series of problems, starting with the sound!)  

Hopefully it'll get the webcam working.  If not, maybe it will be easier working in the 8.10 environment.

---

### Post by hmich176 on 2008-12-18
Well, I tried to upgrade to 8.10, and it told me that Python couldn't install.  I guess it aborted, but I don't know why.  I tried to report the error, and it wouldn't let me.  It compiled the information, and then it told me it couldn't, with no explanation.

---

### Post by deputy on 2008-12-19
Have you tried just running off the Live CD? Does your webcam work when running off the CD?

---

### Post by hmich176 on 2008-12-19
I'll have to give that a try.

---

### Post by hmich176 on 2008-12-19
I solved it!  It took me to upgrade to 8.10, fix registry errors during a reboot, and remove python-bittorrent.  

Now my webcam works in xawtv and Skype.  But not Cheese.

---

### Post by rustutzman on 2008-12-19
Glad to see you got it going!

Russ

---

### Post by deputy on 2008-12-22
W00t, I'm glad it's working now.

---

