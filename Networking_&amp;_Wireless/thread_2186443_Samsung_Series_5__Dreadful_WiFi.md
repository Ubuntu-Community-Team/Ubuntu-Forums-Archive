---
title: "Samsung Series 5:  Dreadful WiFi"
date: 2013-11-07
forum: Networking &amp; Wireless
---

### Post by asearle on 2013-11-07
Hi Everyone,

I have a Samsung Series 5 ultra-book style laptop (with an AMD chip-set) running 13.10 64bit (fresh install) and find that I get dreadful WiFi connections:

At home the signal is weak (considering that I am in the same room as the transmitter!) but it works pretty much OK.  On the road I first thought that it was cafés and hotels which had bad WiFi but this time I compared my connection with a friend's and realised that my connection is weak and gives me sporadic "outage" while his is stable (connected to the same WiFi link),

I also find that I sometimes lose WiFi when I go into suspend.  I can get WiFi back by running "sudo nmcli nm sleep false" but then find that I often cannot shutdown ubuntu.  When I try to force shutdown with "sudo shutdown now" the system locks with a string of messages saying repeatedly: "modem-manager [54971] could not get the system bus ... ".  Then I have to power the system down which I really don't like doing.

So what I really need to find out is ...

a.) whether I should install a new/alternative driver for my WiFi adaptor
b.) whether I should adjust my WiFi settings
c.) whether my on-board unit is bad and I should get an extern usb WiFi adaptor

My ideal scenario would be to disable my WiFi adaptor and run with a trusted USB unit.  But I have tried this and the two adaptors seem to compete with each other.  I wanted to switch the on-board apapter off but there is no setting in the BIOS to do this (as far as I can see).

And Ubuntu is not stable at all with regular crashes and problem reports being generated.  My suspicion here is that it is all connected to the WiFi adaptor.  But I can't be sure.

If anyone can help me diagnose this, then I would be infinitely grateful.  Maybe point me to an explanation or a Howto?  At the moment the whole thing is driving me round the bend.

Many thanks,
Alan

PS: Here are my wireless details ...
<code>
  *-network
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 50:b7:c3:42:50:c6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-12-generic firmware=N/A ip=192.168.2.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:fea00000-fea7ffff memory:fea80000-fea8ffff
</code>

---

### Post by asearle on 2014-08-17
Hi Everyone,

WiFi sort of improved a little with various releases but my Samsung Series 5 never really worked well with Linux (I never tried it with MicroS**t Windows).  Recently the unit "died":  The power cable connection is very flimsy and a small knock broke off the internal connection.

I had SO MANY problems (and unexplainable crashes) with this model that I think I am not going to bother replacing or repairing it:  I've gone back to my trusty old Compaq 6910p ... heaven!  Yes, it's absolute bliss and the big bonus was that I simply pulled the hard-disk out of the Samsung and put it in the Compaq and it ran straight-off.  Mind-blowing!  Bravo Ubuntu ... shame on Samsung!

So be warned: Samsung Series 5 ... is a Dog!

Good riddence!

Regards,
Alan

---

### Post by kc1di on 2014-08-17
for others not having a fall back -- editing the ```
/etc/modprobe.d/ath9k.conf
``` to include the following statement:
```
options ath9k nohwcrypt=1 blink=1 btcoex_enable=1
```  may be of help.

If ```
/etc/modprobe.d/ath9k.conf 
``` does not exist create it using your favorite text editor with just the above statement and save it.

Cheer!

---

### Post by asearle on 2014-08-17
Many thanks for the tip.

And a quick question to everyone:  Have I got it wrong?  Are there things that I could have done to get my Series5 working efficiently?

Has anyone had good experiences with this unit?  Or has it given other people endless headaches?  As was the case with me.

Yes, maybe I just had a "dud machine"?

Am curious to find out.

Many thanks,
Alan

---

