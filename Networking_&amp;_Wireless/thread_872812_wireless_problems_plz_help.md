---
title: "wireless problems plz help"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by Foxfire on 2008-07-28
I have to keep manualy starting my network everytime I restart my computer I have to type in sudo ifconfig wlan0 up then go to network settings and put in my passcode then wicd connects  what can I do to keep from having to do this all the time?

---

### Post by rlzyoner on 2008-07-28
If the network is configured by DHCP then you can add the following to your /etc/network/interfaces file

auto eth0
iface eth0 inet dhcp

(Assuming the network adaptor is called eth0)

---

### Post by wessie on 2008-07-28
Hey Foxfire,

I'm certainly no pro at linux but through my own recent struggles and search for solutions to networking problems in the last 3-4 days, I've seen alot of people recommend that you put the commands that you type in manually to enable networking, in the /etc/rc.local file. That way, when the machine boots up all the 'typing' is done for you.

hth
Wessie!

---

