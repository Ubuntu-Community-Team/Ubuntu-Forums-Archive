---
title: "Network driver installed but still &quot;network UNCLAIMED&quot;"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by Plompie on 2008-08-15
Good day to all,
Ive just installed Ubuntu for the first time some months ago and everything worked fine! But after a update +/- 1 month ago I cant get my wireless network card back to work....

I use the Windows net work driver and it installs just fine but the network remains "Unclaimed" which means (as far as I understand) that no driver is installed.... This is the output I get:

```
paul@paul-desktop:~$ ndiswrapper -l
rt61 : driver installed
	device (1814:0301) present (alternate driver: rt61pci)

```
```

paul@paul-desktop:~$ sudo lshw -C network
[sudo] password for paul: 
  *-network UNCLAIMED     
       description: Network controller
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
paul@paul-desktop:~$
```

Im using a Linksys WMP54g v4.1 WLAN card. Anyone any suggestions on how to get it back to work...? :confused:

Thanks in advance!

---

### Post by Ayuthia on 2008-08-15
Have you tried blacklisting rt61pci and loading the ndiswrapper module?  Does this work:
```
sudo modprobe -r rt61pci
sudo depmod -ae 
sudo modprobe ndiswrapper
```

Also, rt61pci comes with Ubuntu.  Have you already tried it before using ndiswrapper?  Also there is an alternate version, the rt61.  You can get it from here:
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

It seems to work also.

---

### Post by Plompie on 2008-08-16
Hi Ayuthia,

Thanks for you're help! After you're suggestion on trying it without the ndiswrapper I searched this form on how to to that (I'm really new to Ubuntu) and I noticed that if I ran you're command back worts it should to the trick... and it did!

I used:
```
sudo modprobe -r ndiswrapper (to remove the ndiswrapper)
sudo depmod -ae (don't know what it dos but just entered it..)
sudo modprobe rt61pci (to load the original driver)

```

Now I'm back online! Thanks a lot!!:)

---

