---
title: "D-Link DWL-G122 (Rev C1) with Feisty, no go."
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by Yourname on 2007-04-29
Hello,

I tried lots of ways to get this USB dongle working (Rev C1), but nothing works.
Followed this [guide]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73")

And first of all, the .h file didn't have a VENDOR clause like it says so. But I still added the device ids anyway.
Then, tried to run make all after changing to kernel 2.6, and it returned an error, and didn't create the module rt73.ko

```
mark@solo:~/tmp/RT73_Linux_STA_Drv1.0.3.6/Module$ sudo make all
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/mark/tmp/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/mark/tmp/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o
/home/mark/tmp/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c: In function ‘usb_rtusb_probe’:
/home/mark/tmp/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2065: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/mark/tmp/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2085: warning: unused variable ‘device’
make[2]: *** [/home/mark/tmp/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/mark/tmp/RT73_Linux_STA_Drv1.0.3.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2

```

I don't know how else do get this dongle working with WPA or WPA2.

---

### Post by gcpete on 2007-04-29
Yea, I think this is an old version of the driver that wont work with the kernel in feisty. However this one does work. [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz). You also have to blacklist some modules that feisty loads by default. There are instructions here [http://wiki.ubuntu-it.org/RalinkRT73](http://wiki.ubuntu-it.org/RalinkRT73) are in Italian, but I don't speak a word and still managed to follow along. 
This seems to work, BUT I have a problem that shortly after booting up (Whilst gdm is loading)  the wireless usb goes down and after logging in I have to do a sudo /etc/init.d/networking restart after which everything works fine till the next reboot. I would be interested if anyone has any suggestions round this. 

Peter

---

### Post by Yourname on 2007-04-30
I followed that guide, and I think it works now!
Thanks a lot dude.

Now, for you not having to do the networking restart thing, try opening /etc/rc.local and right on top of exit 0, put in the following:

ifdown rausb0
ifup rausb0

...should look like

ifdown rausb0
ifup rausb0
exit 0


Save the file, and reboot. When it reboots, hopefully, your wireless should be connected.
Even before you login.
Change rausb0 if yours is wlan0 or something.

---

### Post by gcpete on 2007-04-30
Hmm doesn't work. To clarify, the network comes up on boot but then drops out again at about the same time as the GDM screen comes up. I guess its something to do with hald. However I have found that if I boot without the USB wireless connected, wait till after gdm comes up and then plug it in it seems to work fine.
Also of note, if I do boot up with it in place, let it fail and remove it and plug it in it gets detected by the system, but does not come up properly. OH well at least I have a work around now.

Peter

---

### Post by Yourname on 2007-04-30
That's a bad workaround.

---

