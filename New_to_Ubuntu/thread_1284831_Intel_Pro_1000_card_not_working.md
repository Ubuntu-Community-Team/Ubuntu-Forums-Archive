---
title: "Intel Pro 1000 card not working"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by xtraspecialj on 2009-10-07
Ok, I found a post from 2006 under Networking & Wireless, but it being so old I didn't trust that the solution would still apply today.

I recently purchased an Intel PWLA8391GT 1Gbit  Pro 1000 card for my Ubuntu 8.10 machine.  I have installed it and it shows up in lspci as Intel Corporation 8254PI Gigabit Ethernet Controller.

Under Ifconfig, it is listed as **eth1** (I have disabled my onboard nvidia lan that was eth0) and shows all the correct capable speeds, **10Mbs, 100Mbs, 1000Mbs**.  However, under speed and duplex it simply says **Unknown!** and at the bottom it says **link detected: no**.  However, on the back of the card, the yellow 1Gbit light is lit.  Plus, it's a brand new cable and I have tried multiple known working ports on my router.   In /etc/network/interfaces it appears to be set up correctly as eth1 with the correct static IP, subnet mask, and default gateway for my LAN.

Do I need to download a driver for it?  I have found a linux driver on Intel's website, but before I go through all that, I want to make sure that it is necessary.  So far my Ubuntu experience has been painless and it has recognized every hardware device I have ever put into this machine without having to download and install any special drivers.  I can't imagine a simple $25 Intel brand card wouldn't be recognized and work immediately.  
Any suggestions from the experts?

---

### Post by tomBorgia on 2009-10-07
I've exactly the same NIC (Intel PWLA8391GT) and it is showing from lspci as

```
06:00.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)

``` 

and it's working fine - no additional drivers / config was needed.

If it's not giving the correct info from ifconfig (i.e. can't even work out if a cable is connected) I'd suggest taking it back to the shop and swapping it over... unless of course it's working fine in Windows / another PC.

Plus I'm assuming it's plugged into a 1GB switch... otherwise the orange light on the back would indicate a hardware / cable problem (brand new cable so probably not).

Just as a side note we use these cards a lot at work and have a fair few linux / Ubuntu boxes and the don't have any special config on the NIC... which makes me think it might be a duff one.

---

### Post by xtraspecialj on 2009-10-07
Hey, thanks for the reply, however my problem was a big ole' dumb human error on my part.  I didn't realize my motherboard had 2 LAN interfaces on it.  I was assuming that the new card was eth1, but it was in fact eth2.  So all I had to do was go into /etc/network/interfaces and activate the eth2 interface and poof!  it worked.  Oh well, my dumb quota for the day may already be filled.

---

### Post by tomBorgia on 2009-10-08
:lolflag:

---

### Post by metersales on 2011-09-16
I seem to be having trouble with my Pro 1000 card.  I'm runny natty on an old dell dimension 2400 that I've upgraded quite a bit.  The reason for the new network card is that the on-board NIC is dead.  I did a system check which detected the chipset of the Pro 1000, but failed the Internet connection test.  Eth0 shows up in the Network connections list, but has no MAC address.  In network tools, the state of the device is listed as inactive with the interface statistics all set at 0.  I am starting to suspect the card to be defective.  This one is really stumping me.

--Update-- Ended up recycling the Dimension anyway.  It wouldn't recognize a video card I installed either.  Weirdest computer I ever worked on.

---

