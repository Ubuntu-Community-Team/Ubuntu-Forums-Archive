---
title: "Wireless Wont Connect Automatically Anymore"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by g0dd3ss on 2007-07-17
Hi I am running Ubuntu Fiesty on a toshiba satellite laptop, I had set up my wireless connection with a static ip and wep key, and it automatically connects when I start my computer. But today it doesn't seem to work anymore, doesn't connect automatically. When I look in ifconfig everything looks right, I can connect to my AP fine using windows on the same machine.  I can see my wireless connection if I use kismet or wifiradar.  But I don't know the command to connect, or how to make it connect on boot like it used to. I haven't (knowingly)  changed any settings, the only things I have installed were a couple of games.  My interfaces file looks like this:

 ```

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.6
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
iface eth1 inet static
address 192.168.0.5
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid dm
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ppp0 inet ppp
provider ppp0

```

If anybody could please help me to fix this and make it start on boot again I would greatly appreciate it .

---

### Post by Goff101 on 2008-07-22
hi. im having the same problem. or at least i think i am. im a complete newb to linux so i dont know what happened. but i can see the networks but it wont connect to them.

---

### Post by Goff101 on 2008-07-23
nvmd. cant see the networks anymore. it just has the cannot connect icon.

---

