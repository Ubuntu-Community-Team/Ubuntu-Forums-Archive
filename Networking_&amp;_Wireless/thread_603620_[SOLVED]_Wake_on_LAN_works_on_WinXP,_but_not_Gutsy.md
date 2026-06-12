---
title: "[SOLVED] Wake on LAN works on WinXP, but not Gutsy"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by t0m on 2007-11-05
Hi,

I want to use Wake on LAN via "Magic Packet" but I just get it to work on WinXP, not on Gutsy. I have used it before in Ubuntu with success, not with this hardware though.

```
t0m@ubuntu:~$ lspci|grep Ethernet
03:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
```

That's the ethernet port of the Asus P5B-E and in my Ubuntu it's eth0.

I activate wake on lan via ```
sudo ethtool -s eth0 wol g
```

Then I get the following configuration:

```
t0m@ubuntu:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: umbg
        Wake-on: g
        Link detected: yes
```

So far it should work then, right? But it doesn't. I can send as many packets I want, it doesn't power on, but if I boot WinXP on the same machine and shut it down again, it works flawlessly.

Any suggestions?

Thanks for the help!

T0m

---

### Post by digitalbenji on 2007-11-05
Which one is set as the default in Grub?  My understanding is that Wake on Lan will just boot the Motherboard, and so it has nothing to do with the OS.  The Mobo will then kick up the PC and Grub will just boot the normal default, which I'm guessing you have set as XP.

---

### Post by t0m on 2007-11-05
Well, it obviously does depend on the power state the OS leaves the mainboard in after shutdown.
I would be happy if I would get to Grub already, but if I switch off the pc with ubuntu (with the configuration done mentioned above) I can't switch it on again remotely, which is possible if I switch it off in WinXP.

---

### Post by jcliburn on 2007-11-05
Wake-on-LAN is busted in the mainline kernel version of the atl1 driver.  It's a known condition.  If you really need WOL support for the L1, the vendor version of the driver is alleged to support it, but I've not tried it myself.

---

### Post by t0m on 2007-11-06
thank you!
do you have a source or a link with further information on that matter? couldn't find anything

---

### Post by jcliburn on 2007-11-06
[ftp://ftp.hogchain.net/pub/linux/attansic/vendor_driver/l1-linux-v1.2.40.2.tar.gz](ftp://ftp.hogchain.net/pub/linux/attansic/vendor_driver/l1-linux-v1.2.40.2.tar.gz)

---

### Post by t0m on 2007-11-07
thanks again! 
tried it and wake-on-lan works like a charm! :)

---

### Post by jcliburn on 2008-05-04
> **jcliburn said:**
> Wake-on-LAN is busted in the mainline kernel version of the atl1 driver.  It's a known condition.  If you really need WOL support for the L1, the vendor version of the driver is alleged to support it, but I've not tried it myself.

I've fixed wake-on-LAN in the atl1 driver.  It will be included in the mainline kernel version 2.6.27.

For now, I've made available on my ftp site some standalone versions of the atl1 driver with WOL fixed.

[ftp://ftp.hogchain.net/pub/linux/attansic/kernel_driver/atl1-2.1.3-linux-2.6.23-standalone.tar.gz](ftp://ftp.hogchain.net/pub/linux/attansic/kernel_driver/atl1-2.1.3-linux-2.6.23-standalone.tar.gz)
[ftp://ftp.hogchain.net/pub/linux/attansic/kernel-driver/atl1-2.1.3-linux-2.6.24-standalone.tar.gz](ftp://ftp.hogchain.net/pub/linux/attansic/kernel-driver/atl1-2.1.3-linux-2.6.24-standalone.tar.gz)
[ftp://ftp.hogchain.net/pub/linux/attansic/kernel-driver/atl1-2.1.3-linux-2.6.25-standalone.tar.gz](ftp://ftp.hogchain.net/pub/linux/attansic/kernel-driver/atl1-2.1.3-linux-2.6.25-standalone.tar.gz)

---

