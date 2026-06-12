---
title: "Wireless: Error getting interface flags"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by marinedalek on 2008-09-14
Hi, I'm running Ubuntu server 7.04 with a Belkin wireless dongle. Everything's been working fine up until today - I host a personal website on the server and people were able to login and post up until late last night. 

I came to check the server today and rausb0 won't come up. When I type ifconfig rausb0 up it says:
```
rausb0: ERROR while getting interface flags: No such device
```

The same message comes up if I restart networking.

Any thoughts?

---

### Post by pytheas22 on 2008-09-14
Did you restart the machine?  Did you look at dmesg for errors regarding rausb0 (type in a command like 'dmesg | grep -e rausb -e rt2570)?  What is the output of 'lshw -C Network?'

---

### Post by marinedalek on 2008-09-14
I've restarted the machine and also done a cold boot. dmesg has no entries for rausb, rausb0 or rt2570, the only non-bus reference I can find to usb in the dmesg output is:
```
usb 5-4: new high speed USB device using ehci_hcd and address 2
usb 5-4: configuration #1 chosen from 1 choice
```

lshw -C Network just shows the details of eth0

I've checked lsusb by the way, and the wireless dongle is listed: 
```
Bus 005 Device 002: ID 050d:705a Belkin Components
```

EDIT: Forgot to mention that I did install updates a couple of days ago, but everything was working fine for over a day.

---

### Post by pytheas22 on 2008-09-15
How did you install the rt2570 driver initially?  If you compiled it manually (which I think you must have, because I don't think Ubuntu 7.04 came with this driver by default), then you would need to recompile it each time you upgrade the kernel.  So if you've changed to a newer kernel, the module probably does not exist on it yet.

You can download the source code for rt2570 from [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads).  If you need help installing it, let me know.  I think that if you install it again, things should work.

The other possibility is that rt2570 exists but is no longer being automatically loaded for some reason.  If you type:
```

sudo modprobe rt2570
```

what does it say?

---

### Post by marinedalek on 2008-09-15
I still have the source downloaded in my home directory - looks like I used the rt73 drivers, however modprobe rt73 brings up nothing, whereas modprobe rt2570 locks up the server.

Something odd seems to be happening at any rate. 
I tried to recompile the rt73 drivers and this is what I got:

```
sudo make
make -C /lib/modules/2.6.20-17-server/build SUBDIRS=/home/pete/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-17-server'
  CC [M]  /home/pete/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o
/home/pete/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c: In function âusb_rtusb_probeâ:
/home/pete/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2065: error: âstruct net_deviceâ has no member named âget_wireless_statsâ
/home/pete/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2085: warning: unused variable âdeviceâ
make[2]: *** [/home/pete/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/pete/RT73_Linux_STA_Drv1.0.3.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-17-server'
make: *** [all] Error 2

```

I downloaded and compiled the rt2570 drivers and it seems to have compiled them correctly, however I'm not sure how to find the interface name to configure it.

---

### Post by pytheas22 on 2008-09-15
I remember something weird about these drivers where you could only compile them once for each .tar.gz source code package that you downloaded.  Even if I ran 'make clean' first, the compilation would fail if I'd already compiled using the same source files.  So maybe that's why you got the errors trying to use source code that you had downloaded previously.

For the name of the interface, check your /etc/modprobe.d/ralink file.  It should give aliases and names for the interface so that you can configure it.  If not, can you tell what the interface is named by looking at the 'iwconfig' command?

---

### Post by marinedalek on 2008-09-15
Aha! I've managed to get it working using the latest rt73 CVS snapshot and this guide: [http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73+howto](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73+howto)

I'd got as far as step 8 myself, but got stuck when it said the module file was too big.

In any case, the wireless is working fine again now - thanks so much for your help!

---

