---
title: "eth0: Device not found - on HD boot, but ok with install CD"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by Tired48 on 2007-01-17
Hi there!

I have a rather odd problem: I cannot access my network card if I boot from hard disk - if I boot from the install CD everything works fine.

ifconfig eth0 yields
eth0: error fetching interface information: Device not found

The kernel module is loaded correctly and dmesg shows that the device eth0 actually exists. However, /proc/interrupts doesn't list the NIC.

I'm running edgy right now and used to have the linux-image-2.6.17-10-server kernel installed. I tried -generic and -386 and some older kernels, too - with no other results.

Then I tried to boot from the install cd (server install) which brings up the NIC! Everything works fine then.

The system I'm trying to get this to work is an "Asus Pundit" Barebone with a "P4SL" Mainboard which has a SIS chipset. The NIC in question is a Broadcom BCM4400. I tried a Realtek 8139 (8139too module) and a Gigabit nic (Realtek 8169 - r8169 module), too. Again, the same problem: The NICs are shown in dmesg but ifconfig isn't able to access them and they don't show up in /proc/interrupts.

I tried various kernel options (noapic, pci=routeirq, pci=noacpi etc) with no luck.

The strangest thing is, that everything works with the install CD, so it has to be some kind of setup problem...

Maybe I'll check out the /proc/cmdline from the boot CD and try these options...

Also, if I put the hard drive in another system with different hardware everything works fine.

I don't have any ideas left... Any suggestions?

-T

---

### Post by dmizer on 2007-01-18
could simply be that your network adapter is not "eth0" when booting to the full install.

please post the contents of:
```
dmesg | grep eth
```

also post the contents of this file:
/etc/network/interfaces

by the way ... i've been here before ;) [http://www.ubuntuforums.org/showthread.php?t=266248](http://www.ubuntuforums.org/showthread.php?t=266248)

---

### Post by Tired48 on 2007-01-18
When I boot using the install CD, the adapter is recognized as eth0. ifconfig eth0 works and shows useful information. The card itself works, too. Whereas when I boot form HD, the card doesn't work.

dmesg | eth showes eth0 for the NIC (I'll post original output from the commands later today when I'm back home). Also, I'll post the content of /etc/network/interfaces but AFAIK that's just a config file to bring the NIC into a configured state... so ifconfig should always work.

The oddest thing I noticed is that eth0 isn't listed in /proc/interrupts although a interrupt is assigned to it when the module is loaded. (See dmesg output... later)

I'll try your eth1 trick you mentioned in the other Thread and report if I succeded.

Bye,
-T

---

### Post by Tired48 on 2007-01-21
Hi dmizer,

Thanks for your hint with the additional NIC!

I added eth1 to my /etc/network/interfaces and saw no diffrence than I just tried eth2 and *boom* it worked. That's odd and I have no idea how that works internally and what's wrong anyway... but I don't really care so much because it works now!

Thanks again for your help!

Cheers,
-T

---

### Post by dmizer on 2007-01-22
fantastic, glad you're online.  i think you had about the same response as i did. :)

in reality, this should probably be filed as a bug somehow, though i'm not sure how it would be possible to confirm or reproduce it.  but, like you ... i'm simply happy to be online.  what nic do you have?  it isn't a pcmcia adapter by chance is it?

---

