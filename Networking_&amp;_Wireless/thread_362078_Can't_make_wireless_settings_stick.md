---
title: "Can't make wireless settings stick"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by j0sh0 on 2007-02-15
Hi,
I'm having problems making my wireless settings stick - ie, after rebooting the computer, I need to edit settings (iwconfig and iwpriv) manually for the modem to connect to the router! I only have to set the channel and authmode, but it is becoming a pain, especially when I have to tell my computer-spastic wife how to make the router connect over the phone (and she's not very patient with computers!). I have a DLINK DWL G-630 (atheros) cardbus, running Ubuntu 6.10. I'm thinking the problem may be in my interfaces file, however I've mainly just copied and pasted from other how-to's I've seen, but I don't know how to troubleshoot it myself.

Here is my interfaces file:
> auto lo
iface lo inet loopback

mapping hotplug
script grep
map  eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

mapping hotplug
script echo
map ath0
iface ath0 inet dhcp
wireless-essid CARTON_WIRELESS
wireless-channel 6
wireless-rate 54M
wireless-key ###
wireless-authmode 2

auto ath0

#auto wlan0
#iface wlan0 inet dhcp



Please, I'm sure the problem is staring me in the face, I just need someone more knowledgable and/or expreienced to point it out to me!!!

Thanks for your time guys, and for making Ubuntu the best-supported OS on the planet!

Cheers

j0sh0

---

### Post by bnuytten on 2007-02-15
Not sure about that mapping thing, but I would replace that entire section as follows:

#auto eth2
#iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid CARTON_WIRELESS
wireless-channel 6
wireless-rate 54M
wireless-key ###
wireless-authmode 2

#auto wlan0
#iface wlan0 inet dhcp

---

