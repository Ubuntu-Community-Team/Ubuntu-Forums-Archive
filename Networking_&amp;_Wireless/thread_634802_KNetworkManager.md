---
title: "KNetworkManager"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by MacAnthony on 2007-12-08
I have my wireless card working, but for some reason, KNetworkManager says there is no active device and therefore doesn't allow me a gui to make changes to my wireless network. It recognized my wired network when I have that connected, but I would like to use this to scan for wireless networks when not at home. I can type a iwlist scan in konsole, but it would be nice to have a gui to help me select an AP.

Any one have any ideas?

---

### Post by mikyt on 2007-12-15
Look at the file /etc/network/interfaces.

There should be a line like:
auto eth1

(where eth1 is your wireless network card name)

if it's not there, just add it and kill and restart Networkmanager.

Without that line, KNetworkManager will ignore the wireless card.

---

### Post by cahill on 2007-12-25
same problem here. NO ACTIVE DEVICE in Knetworkmanager. wired works without any problems, 
iwlist scan sees my AP. but the knetworkmanager doesn't. 
network card is ipw3945. and is named eth1 in the config file.

thanx for any help

---

### Post by MacAnthony on 2008-01-02
My wireless nic is eth1 and there is already a line with "auto eth1" in my /etc/network/interfaces file.

---

### Post by glennph on 2008-01-18
Same problem here.. 

"iwlist scan"  gives plenty of results, but knetworkmanager wont cooperate.. 

atheros ar5007eg, gutsy...

---

### Post by gdzsi on 2008-02-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/154581](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/154581) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				edit /etc/network/interfaces and comment out everything except these two lines:

auto lo
iface lo inet loopback

then run 

sudo /etc/init.d/networking restart

if it still doesn't work, you should add yourself to the netdev group:

sudo adduser your_username netdev

i found it somewhere and it worked for me.

---

### Post by MacAnthony on 2008-03-29
The steps gdzsi mentioned didn't work for me. I ended up installing wicd and stopped using knetworkmanager as a solution. Wicd seems to work just fine.

---

