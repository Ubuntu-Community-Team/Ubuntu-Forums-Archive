---
title: "HELP! Getting Wireless Working HP DV 2000"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by wscg on 2010-10-27
hi guys I'm really loving ubuntu on my laptop and lubuntu on my old -really old- desktop but I am becoming frustrated with the wireless not working. I am absolutley new to linux. I did download the hp driver for it extracted it via cabextract and then try to install via windows wireless installer but it says the inf is invalid driver. 

my computer is an hp pavillion dv2000- white sticker lists it as dv2700 and I am running ubuntu I would really appreciate any help on this as it is now 10 pm and I've spent the whole day trying and I do need it tommorow. 

here is the info
 lspci | grep Wireless
07:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

And Im not sure this will help but here

-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:5a:8f:26
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A ip=96.55.202.13 latency=0 multicast=yes
       resources: irq:44 memory:f4200000-f4203fff ioport:3000(size=256)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:81:bd:29
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-22-generic firmware=228.61.2.24 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:f4300000-f4301fff

---

### Post by wscg on 2010-10-27
this is the router I have [http://www.tp-link.com/products/productDetails.asp?class=wlan&pmodel=TL-WR1043ND](http://www.tp-link.com/products/productDetails.asp?class=wlan&pmodel=TL-WR1043ND)

---

### Post by wscg on 2010-10-27
anyone?

---

### Post by Terl on 2010-10-27
Have you tried to connect with network manager at all?  It is on your upper panel to the right.  Looks like a radar (if you are not wired).  If there is a possible connection it will have a red ! in it.  Just click it and see if your router is listed.

If that does not work (is the light on for your wireless) then go to System/administration, hardware drivers menu and see if your wireless is listed there.  If so, activate it.

Intel usually works out of the box...

---

### Post by wscg on 2010-10-27
I was pressed for time so I went and installed linux mint9 which worked fine right away. I did like ubuntu but I'm gonna give mint a chance. When I get time I'll try the ubuntu live cd and try it again with your recommendations. I mayhave already tried it I'm not sure.

---

### Post by carlinaen on 2010-10-28
I have the same problem, till last week I was using Isadora and I switched to ubuntu10 and it's the same, my wireless It's not working.... I'm using dv2235la (dv2000)....

---

### Post by cgroza on 2010-10-28
If mint worked , have a nice life with it.

---

### Post by carlinaen on 2010-10-28
lol.... Well  you're right.... I'm going back to mint....

---

