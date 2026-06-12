---
title: "configuring dlink air v.d1 in ubuntu 8.04 using ndiswrapper, dhclient won't work"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by Jyrgazud on 2008-06-29
Having trouble configuring my dlink air vd.1 on ubuntu 8.04.

You can see various outputs of commands here:
[http://paste.ubuntu.com/23827/](http://paste.ubuntu.com/23827/)

I tried looking through a couple of help sites and reading some threads but I'm having trouble finding the one to get over this last hurdle. I've got lights coming from the card, but I can't connect, and dhcpclient goes to sleep on me. I'm using ndiswrapper (as you can see) with the windows xp driver from dlink for this card.

Thanks in advance.

---

### Post by pytheas22 on 2008-06-29
Sometimes using a different version of the Windows driver makes the difference.  If there are multiple .inf files on your CD (e.g. different ones for Windows 2000, XP, Vista...) try a different kind.  Or try downloading a different version of the driver and using that.

If that still doesn't work, building ndiswrapper from source might help.

By the way, are you sure you need to be using ndiswrapper for this card?  What kind of chipset is it?  If you don't know, what is the output of:

```
lshw -C Network
```

---

### Post by pytheas22 on 2008-06-29
Actually I did a quick search and it looks like your card has an r8187 chipset, which does have native Linux support.  Apparently earlier versions of Ubuntu included the native driver, but for some reason since Feisty it has been excluded.  The aircrack people have a [guide]("http://www.aircrack-ng.org/doku.php?id=r8187&DokuWiki=356e24d9f2459309396d784224209605") for building the driver from source (with injection support, which you don't need but is handy in case you ever want to steal your neighbor's Internet connection :)), however, if you're interested in that route instead of ndiswrapper.

---

### Post by Jyrgazud on 2008-06-29
lshw -C Network produced:

PCI(sysfs)

 *-network:0             
       description: Ethernet interface
       product: 3c905 100BaseTX [Boomerang]
       vendor: 3Com Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 00
       serial: 00:60:97:b6:9b:f7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=3c59x ip=192.168.1.108 latency=32 maxlatency=8 mingnt=3 module=3c59x multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32

attempted fix from second post, but haven't had luck with it. Seemed to remove the entry referring to my device entirely... going to check over the page to be sure I've done everything correctly.

magus@sleipner:~$ ifconfig wlan0
wlan0: error fetching interface information: Device not found
magus@sleipner:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

lspci -v shows the device still:
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
	Subsystem: D-Link System Inc Unknown device 3303
	Flags: bus master, medium devsel, latency 32, IRQ 11
	I/O ports at e800 [size=256]
	Memory at e7000000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2

---

### Post by pytheas22 on 2008-06-29
> *-network:1 **UNCLAIMED**
description: Ethernet controller
product: RTL8180L 802.11b MAC

It looks like no driver is claiming the device.  Maybe the ndiswrapper module is not loaded for some reason?  Try:
```

sudo modprobe --verbose ndiswrapper
sudo ifconfig wlan0 up
```

do you get any errors?

Otherwise I'm not sure what could be wrong, if ndiswrapper -l indicates that the correct driver and device are present.  You may want to try harder with the native driver method, however.

If you really can't get the native driver to work, it would be useful to see the output of:
```

dmesg
```

(it will be long, but helpful).

---

### Post by Jyrgazud on 2008-06-30
Hey, sorry I took so long to get back to you. Yeah, ndiswrapper was uninstalled; I figured that if it wasn't going to be needed I should remove it at the time. Anyways, I found a set of directions I navigated with relative confidence (and I am now connected and posting wirelessly:D)... I decided to reinstall from scratch (I had just done that anyways so I just had to restart since my bios was set to boot from the cd) and then follow:
[http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)
which gave me very little trouble and was mostly idiot-proof, although for a user like me they probably could have written 'Now, STAY IN THE SAME DIRECTORY and do the following...' in at least one spot. Also, I had to look up how to find my kernel, which turned out to be... in system monitor. My linuxfoo is 'eclectic', to put it politely, and often explodes, but I have infinite patience and a high caffeine tolerance, so its no big deal. :D
Anyways, thanks for the help! I think just learning that there /should/ be some form of supported non-windows driver out there was the significant piece of data for me.

---

