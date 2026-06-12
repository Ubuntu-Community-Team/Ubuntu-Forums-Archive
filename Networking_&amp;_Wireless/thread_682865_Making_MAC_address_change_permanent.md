---
title: "Making MAC address change permanent"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by phidia on 2008-01-30
I'm using 64bit Gutsy on my HP laptop with the Atheros AR5007EG network chip.
Following the advice and how to by afterstep13 [here]("http://ubuntuforums.org/showthread.php?p=4234505#post4234505")I was able to get wireless working! 
I did have a problem of getting the MAC address change to stay after a reboot but I think the answer was to edit /etc/network/interfaces; adding the line hwaddress ether xx:xx:...
*where the x's = network card actual address. 

I'm still a little unclear though on how the network manager expects wlan0 to be set up.

I haven't rebooted yet, to check if the correct MAC address gets used, but I think it may be worth it to post this letting others know that it is possible to get the atheros ar5007eg working in 64 bit Ubuntu.

---

### Post by phidia on 2008-01-30
It's not actually going as well as I hoped. I can't permanently add or edit /etc/network/interfaces because the system removes those lines-yes i'm using sudo to do the edit.

The atheros chip can be made to work, but getting an easy to use wireless connection is not there yet.

---

### Post by Gourgi on 2008-05-30
did you find any solution to this ?
i need it too

[COLOR="Red"]Edit[/COLOR]

i found it: 
just edit the /etc/network/interfaces , here is mine
```

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
hwaddress ether 02:01:02:03:04:01

```
and test it : 
```

sudo /etc/init.d/networking restart
ifconfig

```
done !

---

