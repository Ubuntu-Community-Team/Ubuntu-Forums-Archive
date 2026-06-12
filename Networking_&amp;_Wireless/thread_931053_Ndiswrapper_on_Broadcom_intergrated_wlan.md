---
title: "Ndiswrapper on Broadcom intergrated wlan"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by bryctucker on 2008-09-26
hey guys, i just got around to getting ndiswrapper working with another card for an older laptop of mine, but i just bought a laptop with an intergrated wlan, its a broadcom 802.11wireless g wlan card, i was just wondering if anyone made a linux drive for it, or if it would work with ndiswrapper

---

### Post by Ayuthia on 2008-09-27
There are different options for the Broadcom cards in Linux.  You will need to find out what model the card is.  If you are running Linux on the laptop, you can find the info by going to the Terminal and typing:
```
lspci -nnd 14e4:*
```This will return the PCI information for anything that is Broadcom.

From there, you might be able to use the b43 driver:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

You can also use ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Some Broadcom cards can also use the wl driver:
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

If you don't mind using a testing kernel version of Ubuntu that has the wl driver:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

---

### Post by bryctucker on 2008-09-27
when i put that command in, i get 

05:00.0 "0280" "14e4" "4315" -ro1 "105b" "e003"

does that mean i can use the b43 drivers ?

---

### Post by Ayuthia on 2008-09-27
> **bryctucker said:**
> when i put that command in, i get 

05:00.0 "0280" "14e4" "4315" -ro1 "105b" "e003"

does that mean i can use the b43 drivers ?

Unfortunately no.  It needs to use either the wl or the ndiswrapper option.  However, 8.04.1 does provide the wl driver.  All you should have to do is go into System->Administration->Hardware Drivers and disable the b43 option and enable the wl driver.

If you have 8.04 and a working internet connection, you can get your system updated and then enable the wl driver.

The b43 developers are still working on getting the specs written up for your card so it will be a while before it will be supported.

---

### Post by NoWayBill on 2008-09-27
I have integrated bcm-4312 wireless.
had to install b43-fwcutter from Synaptics to get it to work.

With "wl" driver.

---

### Post by bryctucker on 2008-09-27
i updated my system, but my wlan nic isn't showing up

---

### Post by Ayuthia on 2008-09-28
> **bryctucker said:**
> i updated my system, but my wlan nic isn't showing up

Can you show the results of the following:
```
lshw -C network
sudo updatedb
locate wl.ko
```
I would like to see what driver your card is trying to use and then see if the wl module is installed.  The updatedb command will update the search database and the locate will look for the wl module.

You might even check dmesg to see if there are any messages out there for your wireless.

---

