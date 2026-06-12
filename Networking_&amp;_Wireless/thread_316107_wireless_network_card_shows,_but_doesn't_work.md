---
title: "wireless network card shows, but doesn't work"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by moshy on 2006-12-10
I just installed 6.06 from the live cd, and would like to get the wireless internet working, so I went to System > Administration > Networking and activated the wireless connection, yet nothing seems to be happening in Firefox. I've been at this for hours, I have no clue what to do in the properties box, I've tried all sorts of things. By typing iwconfig i got ESSID:"wlan-ap", but by looking at my brother's computer (Windows XP) he's got the ESSID equalling 00-04-ED-05-2A-D9. None of the How-To's I've read so far tell you with what to fill out the properties box.

I'm assuming the card is working, and the drivers were installed automatically, otherwise it wouldn't be showing up, unless I'm wrong, but this is the information I get from sudo lshw -C network

```

*-network:1
       description: Wireless interface
       product: Wireless PCI Adpator RT2400 / RT2460
       vendor: RaLink
       physical id: b
       bus info: pci@00:0b.0
       logical name: ra0
       version: 00
       serial: 00:08:a1:70:8d:b1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2400 multicast=yes wireless=RT2400PCI
       resources: iomemory:cfff8000-cfff9fff irq:3

```

I reckon I need to install firmware or something, which I don't know how to do

Help would be appreciated, but please don't refer me to [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174) because I've already tried that, and can't get the universe repositories working

thankyou

---

