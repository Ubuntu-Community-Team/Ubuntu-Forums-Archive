---
title: "If using 64-bit Ubuntu - what wireless chipset/driver works for you?"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by kevdog on 2008-01-31
An all out mass campaign to see what is working with 64-bit Ubuntu installs in terms of wireless cards.  Please list your chipset driver combination for others to prosper!

To determine chipset, type at command line (or just cut and paste this code into the terminal):
```

lspci -nn | grep Network

```

This will list the driver (If you have multiple network drivers, like a wired and wireless, all networking drivers will be listed with the following command.  Please only submit the wireless driver) (Cut and paste into terminal)
```

lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=

```

Your wireless chipset should be listed (If you have multiple network cards, wired, wireless, please list the wireless chipset)
If you select other - please let me know the chipset and driver.

---

### Post by scradock on 2008-01-31
-laptop:~$ lspci -nn | grep Network
03:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

works with 64-bit Gutsy and Hardy (as well as 32-bit both). Now using b43legacy driver on Hardy...

---

### Post by Prometheum on 2008-01-31
I voted positive for broadcom (as I haven't had any problems with bcm43xx or ndiswrapper in 7.10 on a bcm4311), but I can't vote positively for my current chipset, the AR5007EG.

For starters, lspci thinks its an AR5006EG:

```

03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

```

Also, even though Atheros has been great for linux over the years, I happened to land the one chipset and architecture that's unsupported for madwifi.While there is a patch from Atheros to allow the HAL to work with AR5007EG's, its only for 32-bit x86. Not even ndiswrapper works consistently, and usually I need to change APIC state, reboot, shutdown, change state, reboot, reboot again, until something works. This is a bug that does not exist on 7.10 x86.

The only option I have for stable wireless is downgrade my functionality to 32-bit.

---

### Post by carpenter00 on 2008-02-01
Wireless card : Broadcom Corp. BCM4312 802.11a/b/g (rev 01)
Wireless driver : ndiswrapper+bcmwl5

Using Gutsy, if that's relevant.

This particular card works with the restricted driver suggested by Ubuntu (bcm43xx, I believe), but ndiswrapper handles it much more nicely, at least in my case.

---

### Post by chewearn on 2008-02-01
$ lspci -nn | grep Network
**0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)**

$ lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
**driver=ipw3945**

---

### Post by kevdog on 2008-02-01
For you broadcom types, was the bcmwl5 driver a 32 or 64 bit driver -- that seems like the same xp driver you would use for a 32 bit install!

---

### Post by kevdog on 2008-02-16
Anyone else successful getting a wireless card to work with 64 bit Ubuntu?

---

### Post by Melcar on 2008-02-16
Currently using an rt61 chip with Gutsy 64bit.  Works out of the box, but the rt61pci module that the kernel uses is slower than snails.  I have also used one of those USB Airlink101 adapters (I think it was a zd11 chip) that also worked out of the box.  I'm relying more and more on kernel modules, since ndiswrapper freezes my system under 64bit.

Edit:  [This]("http://www.airlink101.com/products/awll3055.html") is the Airlink I was talking about.  So far, it has been the best adapter I have used with Linux.  Only reason I switched it out was because I moved my PC ouside the house and I needed a beefier antenna for a better reception.

---

### Post by odiseo77 on 2008-02-16
I'm using the rt2500 legacy driver (the daily cvs version, not the old beta) and it works fine both on Ubuntu 32-bit and Ubuntu 64-bit. The driver that comes by default with Gutsy (rt2x00, I think) doesn't work very well with WPA connections (both, on 32-bit and 64-bit), as has been reported before.

```
lspci -nn | grep Network
05:00.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
```

```
sudo lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
[sudo] password for userxxx:
driver=RT2500STA
```

---

