---
title: "Wireless Worked on Installation, Not Since"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by llanitedave on 2007-09-29
I installed a TRENDnet TEW-443PI wireless PCI adapter on my system running Kubuntu 7.0.4.  The wireless access point is a D-link DWL-2100 AP.  I know it's working, because I also have an iBook running OS X that's having no difficulty accessing the internet through it.  It's using WAP-Personal as the encryption mode.

After installing the card and rebooting the computer, I had to do some playing with the network control utility to get it to work.  Unfortunately, I don't know exactly what I did, but it involved have to do a manual configuration and changing my default IP address.  After a few false starts, it asked me for my WAP password, and I was up and running -- quite fast, I might add.

I shut the computer down to go to bed, and when I booted up this morning, no wireless.

The "Wireless Assistant" utility for Kubuntu shows the signal as the network "dlink", with a lock for the WEP encryption.  It doesn't seem capable of WAP.

The KDE Control Module shows the WIFI card as Ath0. It shows it as "enabled".  It gives it no IP address in dhcp (although my ethernet card does display one), so I entered one in manual.  When I do that sometimes it gives me an error (invalid default gateway IP address) and sometimes not.  But even when it takes, the wireless network does not show up at all on KNetwork Manager, and I get a "Connection Failed" when trying to connect through Wireless assistant.

Any suggestions?

---

