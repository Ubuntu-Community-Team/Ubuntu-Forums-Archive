---
title: "Multiple Wireless Cards (7.10)"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by underscoredavid on 2007-10-22
First, major props to the development team - I'm not a linux guru by any means, so having the wireless issues come to a trickle with this release (7.10) is outstanding.

My Intel3945 worked straight out of the box w/ network-manager, and I'm pretty much fully migrated over to ubuntu now.

Just to make things hard on myself - I've installed a 2nd Intel3945 WLAN card into the laptop, I want to start playing w/ wireless security stuff on a single laptop, versus having to use two. This is where the trouble starts. Network Manager has no problem with one card, but I don't even know how to go about configuring a 2nd duplicate card.

I'd either like to be able to use network manager for both, or even if I could just get the OS to recognize the 2nd w/o having to use network manager - that would work as well. I've already tried real simple stuff like adding an interface to /etc/network/interfaces, but that didn't change anything.

the interfaces file is empty (with the exception of lo) - i'm assuming because that's what network-manager needs in order to function correctly.


Can anyone give me a heads-up, point me in the right direction, or explain how to get a 2nd wireless card configured? Thanks a million.

- Dave

---

### Post by underscoredavid on 2007-10-22
Bump - I know someone out there is running multiple wireless cards.

Here's the bottom part of the output from lspci -nn

04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter [11ab:1fa6] (rev 07)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

The top one is a PCMCIA Wireless card that isn't functioning or showing up, I used this a test to see if perhaps a different type card would show up as a choice.

Second is the built-in NIC

Third is the first Intel3945 - this is up and running w/ network-manager.

Fourth is the second Intel3945 - the one I'd like to use. This or the first PCMCIA connector.

Ideas?

---

### Post by underscoredavid on 2007-10-23
Bump. Anyone out there?

---

### Post by underscoredavid on 2007-10-23
A big hearty thank you to anyone who responds? Maybe?

Just looking to get two identical network cards setup on the same computer.
One's working fine.
The other - isn't showing up as a network interface, but is showing up when I query lspci.

Someone out there has had to of done this?

---

