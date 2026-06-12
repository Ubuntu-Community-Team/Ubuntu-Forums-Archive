---
title: "Newbie trying to go wifi"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by Alternet on 2008-08-07
Hi there, as you can see im fairly new to this stuff and well I am trying to wifi with my router but its clearly not working out... it seems that ubuntu doesn't recognize that i even have a wireless card. (at least when i click on the network settings it doesn't).

I've searched around a lot and not quite sure whats what cause there's alot of talk about trying to get wifi so heres what i've done.

i typed in 

lshw -class network

and it came out with all of this stuff..

WARNING: you should run this program as super-user.
PCI (sysfs)  

  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 12
       serial: 00:03:25:2a:9e:80
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.10 latency=0 module=sky2 multicast=yes


I'm assuming the first is my wireless card info, but i just can't seem to figure out how to get it to work..

help?

thank you

---

### Post by tamoneya on 2008-08-08
you were right in figuring out which one is your wireless card.  Lets follow this guide together: [http://www.willdaniels.co.uk/articles/10-howto/15-rtl8180-hardy](http://www.willdaniels.co.uk/articles/10-howto/15-rtl8180-hardy)

Try to get as far as you can and when/if you get stuck just tell us on what command and show us what errors you got.

---

