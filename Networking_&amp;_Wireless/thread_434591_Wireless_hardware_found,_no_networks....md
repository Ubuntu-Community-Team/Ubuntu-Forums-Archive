---
title: "Wireless hardware found, no networks..."
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by ccw127 on 2007-05-06
Like the title says, Feisty doesn't seem to have any problems finding the pci wireless network card, but when I look for networks it can't seem to find any. I know that the access point is configured correctly (actually there are two available) but it doesn't see either one. I tried to set up the connection manually but to no avail. Any suggestions?

Chris

---

### Post by MeneM on 2007-05-06
Hi,

Could you perhaps also post the output of "lspci -v" for us? It would be good to know what kind of hardware is involved.

---

### Post by ccw127 on 2007-05-06
Here is the applicable portion of the report:

07:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Linksys Unknown device 0014
        Flags: bus master, fast devsel, latency 32, IRQ 20
        Memory at 90004000 (32-bit, non-prefetchable) [size=8K]

As you can see, it doesn't seem to be a hardware issue.

Chris

---

### Post by MeneM on 2007-05-07
Hi again,

Actually, the fact that this is about a broadcom type wireless card is the sole reason your wireless is not quite working as expected.

You see, broadcom believes they can sell wireless cards without actually creating a wireless card that does what it is supposed to do... Most everything with this card is done by the software that Broadcom created... For windows... Only for windows...

So we need to install some software that will enable this card so you can use it ;-)

Try this: [http://ubuntuforums.org/showthread.php?t=391961]("http://ubuntuforums.org/showthread.php?t=391961")

---

### Post by ccw127 on 2007-05-08
Thanks for the info. I actually found the answer to my question already but I forgot to post here saying I had solved the issue. Yes, the driver was the problem. I ended up using ndiswrapper to use the windows driver, works now.

As far as Broadcom is concerned, actually that sounds a lot like a Software Defined Radio, which are really cool devices when built corre3ctly; I have no idea about this case. Not that it matters much when the company is unwilling to open up the drivers to us that would make playing with this card fun.

Chris

---

