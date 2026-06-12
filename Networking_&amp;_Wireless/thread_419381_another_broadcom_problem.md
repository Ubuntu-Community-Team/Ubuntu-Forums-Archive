---
title: "another broadcom problem"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by 4agte on 2007-04-23
ok ive got a r3000 presario and broadcom wireless

ive followed a few tutorials used ndiswrapper with bcmwl5a.inf driver and the wireless light on the laptop is now on woohoo!!!

but i cant seem to connect to my network

i tried using the system/administration/networking and configuring the wirekess card to my network but to no avail

I tried following another tutorial that suggested downloading some Network Tools but that didnt work either

Any help is appreciate


I followed this tutorial for the Networking Tools (only the downloading and install of the network tools part)

[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+wireless](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+wireless)

This one i used to setup the card which turned the light on......

[http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+wireless](http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+wireless)

---

### Post by 4agte on 2007-04-23
when using
sudo ifup eth1

i get....

There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

---

