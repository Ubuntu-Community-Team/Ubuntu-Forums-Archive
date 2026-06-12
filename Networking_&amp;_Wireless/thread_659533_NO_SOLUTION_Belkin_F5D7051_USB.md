---
title: "NO SOLUTION Belkin F5D7051 USB"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by bigfella35uk on 2008-01-05
I installed Ubuntu 7.10 AMD64 a week or so ago and there still doesn't seem to be a solution to my problem.  I've used windows for a while now and I have to admit command lines don't appeal to me.

I've been trying to install my Belkin F5D7051 usb wirefi card now for some time.  I've used Ndiswrapper 5.51 with BCMRNDIS.inf and the 2 sys files also (bcmrndis.sys & usb8023k.sys).  Hey presto, it recognises the card.  From there I have given it the network name of my router and WPA key but when I check to see if it contacts, it show me that it isn't even connecting to an IP address...  MY hopes of this taking over from my use of vista is slipping further away.

Any help greatly appreciated.  I jut want my net back.

Regards

Big

---

### Post by joewhite on 2008-01-12
**Edit: After searching I just found this thread [http://ubuntuforums.org/showthread.php?t=540942]("http://ubuntuforums.org/showthread.php?t=540942").** It includes instructions on how to setup a native driver instead of ndiswrapper. At the time of writing, version [20071213]("http://www.jooz.net/rndis/rndis_wlan-snapshot-20071213.tar.gz") is recommended as the most stable. Just read the thread: it involves a standard make -> make install, and I also had to put, alias wlan0 usbcore in /etc/modprobe.conf or /etc/modules.d on some systems. There is also a cleanup script included.

Read the thread carefully... even if you decide to stick with the ndiswrapper version it tells you howto add a udev rule that is needed to fix a bug in this usb dongle on older kernel versions. Since your install is seeing the device, you are probably ok, though. 

If it is just bringing the device up that you are having trouble with, then try this:

```

iwconfig wlan0 essid yourroutersessid
iwconfig mode managed
iwconfig channel yourrouterschannel e.g., 6
iwconfig key s:password or (iwconfig key passwordconvertedtohex)
dhcpcd wlan0 (might need to install dhcpcd)
```

The last mentioned step assumes your router has dhcp enabled. To get an ip manually, for example:

```

ifconfig wlan0 192.168.1.101 netmask 255.255.255.0 broadcast 192.168.1.255 (varies)
ifconfig wlan0 up
```

Also, to state the obvious, check your essid for spelling and case mistakes.

---

