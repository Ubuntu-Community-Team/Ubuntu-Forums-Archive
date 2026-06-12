---
title: "Wireless problems with Edgy upgrade"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by Corfy on 2006-10-29
OK, I updated from Dapper to Edgy on my laptop, and lost my wireless network. It took me two weeks back in June and July getting the wireless set up to begin with, and I'm not looking forward to repeating that experience.

For the record, I have a Dell Latitude D600 with a TrueMobile 1400 (aka BCM4309) wireless device.

First off, here are the instructions I first followed with Dapper that got it working:

> Originally Posted by TheAngryPenguin
It didn't work for me. I have a Dell Latitude D400 with a "0000:01:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)" wireless card. I tried with the files from the first post as well as with a .sys that's known to work well with ndiswrapper. In all cases, I've ended up with a kernel panic right as the wireless card became active. To anyone else with this particular flavor of Broadcom, here's what I've done to get it to work (and I won't go that much into detail since most of this is documented very well elsewhere...):

1) Install ndiswrapper-utils

2) Download the TrueMobile 1400 (BCM4309 - 802.11a+b+g) driver package from Linuxant's site.

3) Rename R63259.EXE to R63259.EXE.ZIP and open with Archive Manager -- extract bcmwl5.inf and bcmwl5.sys from /TMSetup

4) Do the ndiswrapper voodoo with the file(s) above.

5) Blacklist bcm43xx

6) Add ndiswrapper to /etc/modules

7) Reboot

OK, that was then, this is now.

ndiswrapper -l says that both the hardware and the driver are installed. ndiswrapper is listed in /etc/modules, and bcm43xx is blacklisted.

But network settings is only seeing my wired connection, not my wireless connection. So, while trying to track down the problem, I was told to run lspci, lspci -n, sudo depmod -a and sudo modprobe ndiswrapper. However, that last gives me a fatal error. I also ran tail tail /var/log/messages to find out that information, but I have to admit, it is all greek to me.

lspci
```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)
```

lspci -n
```
00:00.0 0600: 8086:3340 (rev 03)
00:01.0 0604: 8086:3341 (rev 03)
00:1d.0 0c03: 8086:24c2 (rev 01)
00:1d.1 0c03: 8086:24c4 (rev 01)
00:1d.2 0c03: 8086:24c7 (rev 01)
00:1d.7 0c03: 8086:24cd (rev 01)
00:1e.0 0604: 8086:2448 (rev 81)
00:1f.0 0601: 8086:24cc (rev 01)
00:1f.1 0101: 8086:24ca (rev 01)
00:1f.5 0401: 8086:24c5 (rev 01)
00:1f.6 0703: 8086:24c6 (rev 01)
01:00.0 0300: 1002:4c66 (rev 02)
02:00.0 0200: 14e4:165d (rev 01)
02:01.0 0607: 1217:7113 (rev 20)
02:01.1 0607: 1217:7113 (rev 20)
02:03.0 0280: 14e4:4324 (rev 02)
```

sudo modprobe ndiswrapper (sudo depmod -a ran for a few seconds but didn't produce any text, I assume it ran successfully)
```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
```

tail /var/log/messages
```
Oct 29 19:36:10 localhost gconfd (root-5362): Exiting
Oct 29 19:36:58 localhost gconfd (jkc-5347): GConf server is not in use, shutting down.
Oct 29 19:36:58 localhost gconfd (jkc-5347): Exiting
Oct 29 19:38:06 localhost gconfd (jkc-5423): starting (version 2.16.0), pid 5423 user 'jkc'
Oct 29 19:38:06 localhost gconfd (jkc-5423): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Oct 29 19:38:06 localhost gconfd (jkc-5423): Resolved address "xml:readwrite:/home/jkc/.gconf" to a writable configuration source at position 1
Oct 29 19:38:06 localhost gconfd (jkc-5423): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Oct 29 19:38:06 localhost gconfd (jkc-5423): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Oct 29 19:38:06 localhost gconfd (jkc-5423): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Oct 29 19:41:08 localhost kernel: [17180148.644000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
```

I admit, I'm not sure what to do or where to go from here.

In case you want or need it, here is ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:B7:13:96  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:feb7:1396/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1737 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1385332 (1.3 MiB)  TX bytes:257832 (251.7 KiB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)
```

and iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

If I left anything out, feel free to ask. I am still something of a Linux newb, but I am learning. Any help would be greatly appreciated.

---

### Post by robertje on 2006-10-29
Exactly the same laptop, the same 4309, and exactly the same problem here! 
The alternative appears to be to use the "fwcutter" instructions. Those left me with the ability to see networks, but unable to connect. Please post if you get your laptop to work...

---

### Post by ishift on 2006-10-29
bump :)

---

### Post by Blacktalon on 2006-10-29
You can try this how to it uses the same type of card it looks like: 
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

or you can try this one it's not exactly the same card, I use it and it worked for me. :)  [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)


good luck,
~BT

---

### Post by Corfy on 2006-10-29
> **Blacktalon said:**
> You can try this how to it uses the same type of card it looks like: 
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

Well, it is worth a shot. Unfortunately, it is a bit late tonight. I will try it tomorrow.

> or you can try this one it's not exactly the same card, I use it and it worked for me. :)  [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

That is what caused the kernel panic when I was trying to get it to work back in June. The post I quoted is somewhere in the 80s in that thread, if I remember correctly.

---

### Post by Corfy on 2006-10-29
Hey, that worked!

I took a quick glance at the instructions in the first link and noticed two commands that I hadn't tried, "sudo ndiswrapper -m" and "sudo modprobe ndiswrapper", so I tried them. And it worked. My connection is up and running. I even rebooted, and I still have wireless access.

---

### Post by Feenix3k on 2007-03-26
> **Blacktalon said:**
> You can try this how to it uses the same type of card it looks like: 
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

or you can try this one it's not exactly the same card, I use it and it worked for me. :)  [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)


good luck,
~BT

The above link for the bcm4318 does work with the bcm4309 chip. The bcm4306 driver does not work with the bcm4309.

---

