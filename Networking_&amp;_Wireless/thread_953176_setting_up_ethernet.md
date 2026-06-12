---
title: "setting up ethernet"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by mercfoot9 on 2008-10-19
So the laptop I have installed Ubuntu on (an old Sony Vaio) doesn't have an internal ethernet connection.  I'm thinking what I want to do is set it up as a non-wifi workstation, so ethernet would be the best answer.  I could plug it in when i needed to install updates, and leave it isolated otherwise.  
The laptop has an ethernet PCMCIA card which is taking up both slots.  When I plug in an ethernet cable a red light comes on in the slot (its refracted in the male end of the cable), but the OS doesn't seem to have any connection, and I can't find an intuitive location for networking info.  Am I right in thinking I'll probably have to track down a driver for the PC card?  I couldn't see any brand labels as to what kind of PC card was in there.  Any thoughts how I could figure that out to get the right driver without taking the laptop apart?  Any tips? Thanks for any help!

---

### Post by Barriehie on 2008-10-20
How about System > Preferences > Hardware Information?  That tell you anything???

Barrie

---

### Post by cariboo on 2008-10-20
THe driver is probably already installed, to make sure in a Applications-->Accessories-->Terminal type:

```
sudo lshw -C network
``` 

This will print out a list of your network hardware.

The output should look something like this:

```
description: Ethernet interface
       product: MCP51 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 14
       bus info: pci@0000:00:14.0
       logical name: eth0
       version: a3
       serial: 00:16:17:9c:84:b5
       size: 100000000
       capacity: 1000000000
       width: 32 bits
       clock: 66MHz
       capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.100 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-pci:4
```

If there is a problem, it will be listed as unclaimed or disabled. Paste the output in your next post and if you could please use the code tags. The code tags are located in the advanced editor, just click on the # sign.

Jim

---

