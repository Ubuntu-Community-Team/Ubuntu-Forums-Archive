---
title: "is my /etc/network/interfaces config correct?"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by spartan777 on 2007-06-21
I'm following this how to to get my wireless usb adapter working 

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73#head-cfea35eda750890a23c58873b4183271cc3a650c](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73#head-cfea35eda750890a23c58873b4183271cc3a650c)

and at the bottom of my /etc/network/interfaces config file i notice the the three lines beginning with "auto." I've been having some issues with my wireless, and was wondering if I erroneously added those three lines. Can anyone verify this for me?




```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-essid minerhome
wireless-key s:avalanche33


iface wmaster0 inet dhcp
wireless-essid minerhome
wireless-key s:avalanche33





auto rausb0
iface rausb0 inet dhcp
        pre-up ifconfig rausb0 up
        pre-up ifconfig rausb0 down
        pre-up ifconfig rausb0 up
        pre-up iwconfig rausb0 essid "MYESSID"
        pre-up iwconfig rausb0 mode Managed
        pre-up iwpriv rausb0 set AuthMode=WPAPSK
        pre-up iwpriv rausb0 set EncrypType=TKIP
        pre-up iwpriv rausb0 set WPAPSK="YOUR KEY"
        pre-up ifconfig rausb0 up







































auto wlan0

auto wmaster0

auto eth0
```

---

### Post by scrooge_74 on 2007-06-21
you can comment out all the extra cards, I suppose eth0 is your wired connection. The system is probably getting confuse by all those extra entries

USB wireless is a pain to setup

---

### Post by spartan777 on 2007-06-24
yeah, usb wireless does really suck. I tried looking into a pci card adapter too, turns out they ALL suck (and i haven't even looked into linux support). you'd think at least one company would come out with a decent pci wifi card. 

anyways, mwaster just dissappeared when I checked the config file again, I think it either the RT73 driver or the RUTIL gui utility for that driver that is doing this weird crap. It's kinda resolved itself for the most part. I don't lose my wireless connection in an hour of use like I used to. However, I still have to unplug the dumb thing every time I boot into ubuntu, to plug it in once I'm logged in, otherwise the driver won't recognize it. oh, and WPA doesn't appear to be supported.

---

### Post by scrooge_74 on 2007-06-24
I also had that same issue, if i leave it plug when booting the system would stall, and yes some cards cant use WPA or even WEP in some cases...lack of driver support, what can I say.

So far I have been very lucky with all three of my PCs, the hardest to set was a Compaq using broadcom card

---

