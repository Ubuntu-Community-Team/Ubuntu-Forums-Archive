---
title: "Gutsy won't load after ndiswrapper and RTL8185"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by vfiz on 2007-12-16
I've been having quite a bit of trouble with my wireless setup for Gutsy.  My system now perpetually hangs on loading up (booting is fine; grub is fine). Since I can't get into the system to start things up, the error messages and such are from memory for the most part, so they may be a little different than the actual error message.  Here's some important info:

Distro: Ubuntu 7.10 AMD64
Wireless NIC: Realtek RTL8185

The preloaded driver (r8180) for the NIC was causing the system to hard lock (which other people experienced).  Since others had success with ndiswrapper and the WIN98 driver, I thought I'd give that a go.  I installed ndiswrapper, the WIN98 driver from Realtek, and blacklisted r8180.  I added ndiswrapper to /etc/modules and also did depmod and all that stuff.

This solved the hard lock problem (which I found out was a legitimate bug in Gutsy), but my wireless wouldn't work.  lshw -C network showed the card as "UNCLAIMED".  

I used dmesg | grep ndiswrapper, and it gave me an error saying that the driver I loaded was 32-bit when I was using a 64-bit system.  So, I browsed the folder of drivers downloaded from Realtek and found one that was labeled "x64", which I installed.  I restarted the system, and it never made it past the splash screen.

I used "Recovery Mode" and it didn't work either.  It got through a lot of stuff and then perpetually hangs once it puts up this:

```
[  43.174130] wlan0: ethernet device 00:0e:2e:6d:46:7b using NDIS driver: net8185x64, version: 0x50449, NDIS version: 0x500, vendor: 'Realtek RTL8185 Wireless LAN (Mini-)PCI NIC                       ', 10EC:8185.5.conf
[  43.174356] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2 PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  43.174610] usbcore: registered new interface driver ndiswrapper
```

Once it hits usbcore, it gets no further, no matter how long I let it sit.

I have the "System Rescue CD" live distro (based off of Gentoo), so I can get into my Ubuntu partition and edit any file I feel like.  However, I don't quite know what to edit.  I suppose the best bet would be to keep ndiswrapper from loading at startup, but I don't quite know how to do that.  I removed "ndiswrapper" from etc/modules, which didn't do anything.

If anyone has any ideas, let me know.  I'm not against reinstalling it form the beginning (yay for having a separate /home partition), but I'd kind of like to figure out how to bring my system back to life.

Thanks, and if there's anything more you'd like to know, just let me know.  Again, I can't replicate any of the error messages because I can't get into my system, but if I sit down and do some more googling, I'm sure I can jog my memory a bit.

---

### Post by dstew on 2007-12-16
This may be a kernel bug. See [https://bugs.launchpad.net/ubuntu/+bug/152527](https://bugs.launchpad.net/ubuntu/+bug/152527). There is some possibility that an unencrypted connection might work.

---

### Post by vfiz on 2007-12-17
I don't think that's it.  I believe the bug references the hard lock that happens under the preinstalled r8180 driver after the system is all loaded up and you're actually in Ubuntu.  I had the problem described in the bug but fixed it by blacklisting the driver.

I'm not sure if it has to do with encryption or not.  I went into etc/networks/interfaces (through the System Rescue CD) and removed the information that would make it automatically connect to my encrypted wireless network.  It didn't do anything different.  Still hangs on usbcore.

---

### Post by vfiz on 2007-12-17
The system has been resurrected by deleting 
```
iface wlan0 inet dhcp
auto wlan0
```
from the /etc/network/interfaces file.  Of course, this leaves me without any wireless card at all...

I'll fiddle around some more, probably break it again, and post back.

If anyone knows how to get a 32-bit wireless driver working in a 64-bit install, I'd love to know.

---

### Post by CoolDreamZ on 2008-02-09
RealTek have posted a new driver (dated 21st Dec 2007) which works (so far) for me (on a 32bit Feisty system)

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")

---

### Post by CoolDreamZ on 2008-02-09
Well, I have tried this and I get kernel freezes (from syslog it seems the wireless card/driver is constantly re-setting/crashing). I have moved to using the ndiswrapper solution instead which works fine with command line configuration of the wireless network connection although I have now lost the ability to configure through nm-applet :(

---

