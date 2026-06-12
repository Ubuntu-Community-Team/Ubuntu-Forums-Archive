---
title: "Wireless issues with Centrino Wireless-N 2230 on Ubuntu 14.04"
date: 2016-04-06
forum: Networking &amp; Wireless
---

### Post by haraldnordgren on 2016-04-06
I am having problems with my wirless adapter on Ubuntu 14.04. Sometimes when I boot the computer it is able to establish a connection, maybe one fifth of the time, but mostly it is just trying to connect forever:

```
 % nmcli nm
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connecting      enabled         enabled    enabled         disabled
```

Even when it is able to establish a connection there are many problems. After a long uptime the connection seems to get congested and often gets dropped. The same thing happens if I try to stream video or download large files.

My current hardware setup is somewhat peculiar. I spilled soda all over my other laptop, ruining the motherboard, so I decided to put this hard drive into my old one (the one I am currently on) in order to keep all my files and settings. Everything works except for the wifi. On that old machine I had noticed problems with the wireless connection under low signal strength. I solved that problem by downgrading and putting the `bcmwl-kernel-source` on hold using `apt-mark`. That option doesn't seem to exist for my current drivers. I have since purged these obsolete drivers but it had no effect on the problem.

Here is my info:

```
 % sudo lshw -C network
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: c4
       serial: 60:6c:66:32:96:f5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.2.0-35-generic firmware=18.168.6.1 ip=10.0.0.13 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:33 memory:f7d00000-f7d01fff
```

I also tried the following to no avail:
```
sudo apt-get install --reinstall linux-firmware
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```

---

### Post by weatherman2 on 2016-04-06
Some users of Intel wireless card report that one setting helps their connectivity

Try this:

```

echo "options iwlwifi 11n_disable=8" | sudo tee  /etc/modprobe.d/iwlwiwi.conf

```

then reboot and see if that works any better.  I use Intel wireless cards in several laptops and have never needed to do this - mine seem to work fine out of the box, but you might give it a try.

---

### Post by haraldnordgren on 2016-04-06
Thanks for the tip, but it didn't work.

---

### Post by weatherman2 on 2016-04-06
In what environment are you using this laptop with WiFi?  Are you using it with known good WiFI that works well with other devices (or did with the old laptop) in that exact location?

It looks like your Intel iwlwifi driver is pretty recent.

I suppose it's remotely possible the Broadcom wireless card in your dead laptop was superior to the Intel card in this one.  If by chance neither of the laptops are HP or Lenovo, you could try swapping the wireless cards, if the dead laptop's wireless card survived.  It might be easy to swap wireless cards; I have upgraded many of them.  HP and Lenovo both "whitelist" their wireless cards, meaning that if you try to install a wireless card not on the "whitelist" the BIOS will reject it and not even let you boot.  Dell, Toshiba, Acer and others do not restrict you like this.  Replacing a wireless card is often pretty easy - sometimes one panel on the bottom gives you access to the card.  The antenna wires just clip on, and the card should be in a slot and just pop out, not soldered in.

It might also be worth checking to make sure the antenna wires are clipped on securely to that Intel 2230 wireless card.

---

### Post by haraldnordgren on 2016-04-07
> **weatherman2 said:**
> In what environment are you using this laptop with WiFi?  Are you using it with known good WiFI that works well with other devices (or did with the old laptop) in that exact location?
Yes, my iPhone is connected to the same wifi and has never had problems. The signal quality is not all it could be, but there is nothing I can do about that. I found the best spot in the house and the problem still persists. I'm generally around Link Quality=40/70 according to iwconfig which seems decent enough to me.

> **weatherman2 said:**
> I suppose it's remotely possible the Broadcom wireless card in your dead laptop was superior to the Intel card in this one.  If by chance neither of the laptops are HP or Lenovo, you could try swapping the wireless cards, if the dead laptop's wireless card survived.  It might be easy to swap wireless cards; I have upgraded many of them.  HP and Lenovo both "whitelist" their wireless cards, meaning that if you try to install a wireless card not on the "whitelist" the BIOS will reject it and not even let you boot.  Dell, Toshiba, Acer and others do not restrict you like this.  Replacing a wireless card is often pretty easy - sometimes one panel on the bottom gives you access to the card.  The antenna wires just clip on, and the card should be in a slot and just pop out, not soldered in.

The broken one was a Lenovo, but current one is an Asus. Will that work?

---

### Post by weatherman2 on 2016-04-07
It might work but only in Linux (not in Windows probably if you dual boot).  I have done that before, though it might have weird issues.  If it is easy to try (because the two wireless cards are easy to reach), it might be worth a shot, especially if the old Broadcom card worked well before.  Of course, you will have to go back and re-install all the Broadcom drivers you just finished purging...

---

### Post by weatherman2 on 2016-04-07
You might also request this thread be moved to the Networking & Wireless forum and see if someone can suggest a better software solution.  I gave you a hardware suggestion because you posted in the hardware forum. ;-)

---

### Post by haraldnordgren on 2016-04-07
> **weatherman2 said:**
> It might work but only in Linux (not in Windows probably if you dual boot).  I have done that before, though it might have weird issues.  If it is easy to try (because the two wireless cards are easy to reach), it might be worth a shot, especially if the old Broadcom card worked well before.  Of course, you will have to go back and re-install all the Broadcom drivers you just finished purging...
I'm not dual-booting, so no worries there. Unfortunately, the Broadcom card had a different connector, so that didn't work. It was much smaller and didn't even fit in the socket even if I wanted to give it a shot.

For anyone who wants to disassemble an Asus K56, the wireless card is *not* easy to reach. I had to remove the entire back panel, voiding the warranty (no worries, it's old and that was bound to happen anyway). At least I got the check the antenna wires, they seem to be where they should. Still no progress with the connectivity though.

> **weatherman2 said:**
> You might also request this thread be moved to the Networking & Wireless forum and see if someone can suggest a better software solution. I gave you a hardware suggestion because you posted in the hardware forum. ;-)
Right. Let's move it over! :)

---

### Post by howefield on 2016-04-07
Moved to the "*Networking & Wireless*" forum as requested.

---

