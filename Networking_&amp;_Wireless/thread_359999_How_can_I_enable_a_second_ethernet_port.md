---
title: "How can I enable a second ethernet port?"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by hodad on 2007-02-12
I'm trying to connect to a second pc at home using the second of two ethernet ports on the back of my primary pc.  Eth0 connects to the internet, I'd like to make Eth1 connect to the other pc.  Eth1 shows up under hardware mgr, but I can't figure out how to activate it.

Anyone know how to turn on an ethernet port?

Thanks!

---

### Post by phiphedog on 2007-02-12
try [COLOR="Red"]sudo ifconfig eth1 up[/COLOR] from a terminal window or there's the networking GUI which should have an activate button on it that you can hit after you've selected eth1.

---

### Post by hodad on 2007-02-12
Here's what I got:

************:~$ sudo ifconfig eth1 up
Password:
eth1: ERROR while getting interface flags: No such device
************:~$

---

### Post by phiphedog on 2007-02-13
what do you get when you do a ifconfig -a , is the eth1 listed there and does it have an IP address?

under [COLOR="Lime"][COLOR="SeaGreen"]System-->Administration-->Networking [/COLOR][/COLOR]you should be able to see the connection eth1 there. Highlight it and hit [COLOR="lime"][COLOR="seagreen"]Preferences[/COLOR][/COLOR] and you should be able to enable it there.

Also, you can try adding an ip address manually with [COLOR="red"][COLOR="SeaGreen"][COLOR="Red"]ifconfig add eth1 192.168.1.20 255.255.255.0[/COLOR][/COLOR][/COLOR] and then enabling it [COLOR="Red"]ifconfig eth1 up[/COLOR]

---

