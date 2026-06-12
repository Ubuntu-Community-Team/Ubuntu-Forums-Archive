---
title: "Feisty Fawn and DLink Wireless Issue"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by sports51 on 2007-02-21
Hey guys, I got ubuntu going (obviously) and am ready to learn! :popcorn: 


My main issue right now is that I have Feisty Fawn 7.04 64bit.  I figured, since I'll be playing around, why not play around with the latest stuff.

Card: Dlink DWA 552. (Range N Xtreme)

I've done all the ndiswrapper stuff using windows xp drivers and 64bit vista drivers.  They all claim to work saying "Driver Installed, Hardware Present"


But yet, I don't get any hardware shown in network connections, under iwconfig, ifconfig, nothing.  I've read around and I've blacklisted different things like the broadcom one, ath_pci, ath_hal and it still doesn't work.

Card: Dlink DWL-G122 Rev. D1

Same as above, doesn't work.


Is this a Feisty issue, a 64bit issue, a combo of both?

---

### Post by sports51 on 2007-02-21
I haven't found it anywhere, but I'm going to check if it is a 32-bit/64-bit issue as well as a kernel issue by trying it in Damn Small Linux and see what happens.

---

### Post by sports51 on 2007-02-21
According to the older DSL kernel and the ndiswrapper that comes with it, invalid drivers is all I get.  Maybe it's an ndiswrapper problem?

---

### Post by OffAxis on 2007-02-21
I'm having a similar issue with my usb D-Link DWL-G122. Mine shows up in both 
```
ifconfig
```
and
```
iwconfig
```
though.

what does your /etc/network/interfaces file look like?

and which one are currently trying to get going?

---

### Post by OffAxis on 2007-02-21
by the way I've had the D-Link working in Edgy Eft with both 32-bit and 64-bit installs.

---

### Post by sports51 on 2007-02-21
Oh, I'm sorry.  I listed both as I'm trying to get either one going right now.  I keep having to pop back into windows to post my results.


All I get with ifconfig is lo and eth0.  iwconfig gives me a message saying that neither connection has a wireless extension.


I'm going to try some other distros tonight.  I'm gonna look at Sabayon and I guess try a revert back to Edgy Eft.  I'd like to stick with Ubuntu as I think it has the best community behind it.

---

### Post by OffAxis on 2007-02-21
here's what my interfaces (etc/network/interfaces) file looked like on my previous, working install of of edgy 64-bit server with the usb D-Link DWL-G122. It is a static setup.

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto rausb0
iface rausb0 inet static
address 192.168.1.20
netmask 255.255.255.0
gateway 192.168.1.1
pre-up ifconfig rausb0 down
pre-up iwconfig essid "DLink"
pre-up iwconfig rausb0 mode Managed
pre-up ifconfig rausb0 up



This is without ANY encryption (I was just seeing if I could connect).

rausb0 is what my card was showing up as in ifconfig.
essid should be set to your wireless router's name.
gateway should be set to your router's address.

For a dhcp ip address change the line
```

iface rausb0 inet static 

```to 
```

iface rausb0 dhcp

```
and comment out the address and netmask lines.

Also, if you have the usb NIC hooked up when you do the install it'll autodetect it (and set it up as best it can).
I think it'll do the same on a reboot.

I should also mention that I got the basis of my file from a HowTo on the forums, which I can't find atm.

For an exhaustive Troubleshooting Guide try here:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

---

### Post by sports51 on 2007-02-22
Still a big no go no matter what distro I use.  Ubuntu, DSL and Sabayon all ran into the same problem.

I still get the message driver installed. hardware present.   but no wlan0, no ath0, nothing.  All 3 distros have the problem.... exactly.  

I've done the modprobe ndiswrapper, everything.  I've tried madwifi on sabayon and I get a missing symvers error based off of a gentoo file system folder.


Any one know what to do next?


EDIT: I can't do ifconfig ath0(or wlan0) up as in the top post, iwconfig just lists lo and eth0 as well as ifconfig.  All three distros know however that the hardware is there.

---

### Post by sports51 on 2007-02-24
just a bump to try and get this post one more look.  The problem is on 3 different distros, so I'm thinking it's something I'm doing.

---

### Post by hefty_efty on 2007-03-31
Feisty broke my DLink 122 wireless too.

I had it working with Edgy Eft, after following the advice elsewhere in these forums, but something in Feisty broke the wireless extension configs....

---

### Post by Shay Stephens on 2007-03-31
I have a D-Link DWL-G650 that works without having to do anything.  I had a G630 but ti didn't work right in breezy if I remember right, so that is when I got the G650 and have not had a problem since.

---

### Post by djknorr75 on 2007-04-14
I have the G630 and have not been able to get it to work properly in Feisty (new convert from Windows, so don't know if worked in earlier versions or not).  The majority of the time, I can't get any kind of action from the card, but actually just now I got a really weak signal, at least I assume that is what the little bar and 30% means!

However, it isn't enough for me to connect to the network.  If I switch over to XP, the card works splendidly and I always have a full signal regardless where I am in the house.

Any ideas on why I would only sometimes get a weak signal?

---

