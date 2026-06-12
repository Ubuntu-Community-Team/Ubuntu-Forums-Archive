---
title: "Wifi hotspot issue"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by drascus on 2007-01-10
Ok so I have no problem connecting to my home network with network manager that comes with the Ubuntu 6.06. But when I go to other networks like at work or hotspots even though they appear in the networks list, and even though they are listed as open networks I cannot connect to them. I have accidentally connected to my network at work by turning off an d on my wireless card restarting a couple of times, basically hitting any button or setting I could think of. This seems to be a usless way of troubleshooting every time I need. Is there a defined procedure for connecting to a network using network manager. If so is there a Wiki or could someone explain that procedure here. for some reason it is not explained in either one of my books. Thanks everyone for your help. 
~Mike~

---

### Post by tturrisi on 2007-01-10
The network manager that comes w/ ubuntu is actually called net-admin, not to be confused w/ network-manager-gnome which is a separate package.  Net-admin often does not display the correct wlan info.  I have found it to often show a wlan as unencrypted when in fact it really uses encryption, and vice-versa.  Try the command:
iwlist ethx scan
where ethx = your device, e.g. eth1, wlan0, ath0, etc.

---

