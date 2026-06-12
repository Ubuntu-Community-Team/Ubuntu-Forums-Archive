---
title: "Wireless working wierdly"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by StinkyCat on 2010-11-25
hi i got my wireless card workin and connected to my home wirelerss connection. but at my university, while in windows i have a good signal, in ubunu it tries to connect, never actually getting to connect.. any ideas? (in my place if im far from the router it disconnects, while in windows i can connect at the same distance).
thk

---

### Post by t4thfavor on 2010-11-25
What brand of wireless card do you have, this sounds like it could be a driver issue, I know not all drivers have the same sensativity support.

I had the same problem with an early intel card, but it's since been rectified, and now I connect better from Linux.

---

### Post by Rex Bouwense on 2010-11-25
I agree.  It sounds like a driver problem.  I had a problem with my Dell wireless card (connecting in Windows and not in Linux) before I saw the light and deleted Windows.  Connect your computer directly to the router while booting Ubuntu and see if you can download the driver needed.

---

### Post by t4thfavor on 2010-11-25
Dell's usually have broadcom chips, which frankly suck in the world of wifi. This is not an uncommon issue.

---

### Post by Rex Bouwense on 2010-11-25
Oh yes.  It was a Broadcom, but I got it working.  For some reason, who knows why, a big Company like Dell ought to know better.  I wonder if the OP has a Dell.  He never did say.

---

### Post by t4thfavor on 2010-11-25
Dell does it because there (broadcom) the cheapest cards available, and that's their MO. Dell is in it for the margin, and not the customer satisfaction.

---

### Post by oleink on 2010-11-25
> **Rex Bouwense said:**
> Oh yes.  It was a Broadcom, but I got it working.  For some reason, who knows why, a big Company like Dell ought to know better.  I wonder if the OP has a Dell.  He never did say.

Which actual Broadcom card do you have?

---

### Post by perspectoff on 2010-11-25
Re: Weirdly

Probably has nothing to do with the wireless card nor the driver itself.

Removing Windows as the solution? That's pretty ridiculous.

Probably has to do with the networking cache, which is finicky in Ubuntu with Network Manager.

---

### Post by Rex Bouwense on 2010-11-25
> **oleink said:**
> Which actual Broadcom card do you have?
It is the Dell Wireless 1350 card.  It slides into my old Dell Inspiron 1000 which believe it or not has Lucid installed and running great on it.  It used to have Windows XP and Jaunty dual boot but that went away a while ago.  I had no reason to keep Windows.

---

### Post by oleink on 2010-11-26
> **Rex Bouwense said:**
> It is the Dell Wireless 1350 card.  It slides into my old Dell Inspiron 1000 which believe it or not has Lucid installed and running great on it.  It used to have Windows XP and Jaunty dual boot but that went away a while ago.  I had no reason to keep Windows.

Dell has been bad about that stuff lately.  Obviously it doesn't relate as much to Ubuntu but there is carryover.  Poor hardware and poor drivers means that making a proprietary driver for the card isn't as easy.

---

### Post by Dark7man on 2010-11-26
> **StinkyCat said:**
> hi i got my wireless card workin and connected to my home wirelerss connection. but at my university, while in windows i have a good signal, in ubunu it tries to connect, never actually getting to connect.. any ideas? (in my place if im far from the router it disconnects, while in windows i can connect at the same distance).
thk

You get sorted yet mate? My wifi was doing the same thing and had a bit of work to sort it out! Just to check in case I can help-if Your chip is similar to mine that is... :) Do You know what wifi card You have?

Just in case :)
You can run this command that might help find out the details of Your hardware:

Paste the output from the terminal of the following command..

1. Open a terminal and type the command:
```
sudo lshw -C network
```
And You're looking for the output, for me is usually near the bottom that looks something like this.
```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:26:5e:8f:f8:33
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.7.101 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:d9500000-d9503fff
```

:popcorn:

---

