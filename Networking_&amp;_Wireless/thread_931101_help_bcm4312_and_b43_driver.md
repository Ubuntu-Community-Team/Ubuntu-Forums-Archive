---
title: "help bcm4312 and b43 driver"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by c@sp3r on 2008-09-26
I have being trying to get my bcm4312 with the new b43 driver for the last few days but I can't get to work. I have follow this guides 

[http://fourlovesfour.blogspot.com/2008/05/setting-up-broadcom-b43-wireless-with.html]("http://fourlovesfour.blogspot.com/2008/05/setting-up-broadcom-b43-wireless-with.html")
[http://ubuntuforums.org/showthread.php?t=600097]("http://ubuntuforums.org/showthread.php?t=600097")
I do everything in this guides but when I try loading the b43 nothing happens. I can use it with ndiswrapper and wl but both of them have problems.

this is my lspci
```
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

lspci -n
```
04:00.0 0280: 14e4:4315 (rev 01)
```

uname -a
```
Linux April 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

```

dmesg when i load bcm43xx
```
bcm43xx driver
[  464.316180] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  464.316186] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>

```

dmesg when I load b43 shows nothing about it

dmesg for wl
```
[ 1628.993322] ACPI: PCI Interrupt 0000:04:00.0[A] -> Link [LK4E] -> GSI 19 (level, low) -> IRQ 22
[ 1628.993334] PCI: Setting latency timer of device 0000:04:00.0 to 64
[ 1628.999928] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.6

```

I have completely remove ndiswrapper. Also the lshw -C network when I load the b43
```
 *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
```

Does the b43 or bcm43xx driver work at all with this card? Thanks in advance

---

### Post by Ayuthia on 2008-09-27
Unfortunately, the b43 and bcm43xx drivers do not work with your card yet.  The linuxwireless.org site ([http://linuxwireless.org/en/users/Drivers/b43)shows](http://linuxwireless.org/en/users/Drivers/b43)shows) that they are generating the specs for the programmers right now though. If you look there, your card is listed as a BCM4310 card (isntead of a 4312) because it was labled incorrectly a while back.

---

### Post by Paultergeist on 2008-10-01
When do they expect to release the drivers, then?

Can they say a stimated time?

whit lspci -n i got:
02:00.0 0280: 14e4:4315 (rev 01)

It's the same one, right?

---

### Post by Ayuthia on 2008-10-01
> **Paultergeist said:**
> When do they expect to release the drivers, then?

Can they say a stimated time?

whit lspci -n i got:
02:00.0 0280: 14e4:4315 (rev 01)

It's the same one, right?
It is the same one and the developers have not given any timeframe on when it will come out.

---

### Post by maxcomx on 2008-12-11
hey dude, i have a bc4312 rev02, and it work, but i wont say that it easy, it was so complicated and pain in the a$$ that i forgot how i fix that.

 I'm sorry !

But it anyway depend of the distribution your are using.

i was with Ubuntu 8.04 and it was the one pain in the a$$ but once i got it was ok.

And then i decide yo install 8.10 intrepid, and wowww, it work at the first time out of the box.

But in between you, me and everybody else, the next time you buy a computer be sure to NOT get a d@mn Broadcom device !  they are big problem of compatibility and install and far from the best.

So good luck on that.
Cheers dude.

---

