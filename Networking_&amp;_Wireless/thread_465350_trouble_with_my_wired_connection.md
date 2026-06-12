---
title: "trouble with my wired connection"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by Ryzol on 2007-06-05
Got my nice new System76 laptop, plug in an ethernet cable and nothing. It acts as if it wasn't there. The router light turns on when the cable is connected. When I run: ```
sudo mii-tool eth0
SIOCGMIIPHY on 'eth0' failed: No such device

sudo mii-tool eth1
eth1: 10 Mbit, half duplex, no link
```
The eth1 mii-tool results are the same regardless of the ethernet cable being plugged in. Help would be much appreciated. Note, at the moment all I want to do is to be able to access the internet, I can worry about networking later. ;)

---

### Post by reckless2k2 on 2007-06-05
go ahead and post your ifconfig with the cable plugged in. i just want to see if you get a local addy. do you have a wifi card turned on too?

---

### Post by macubo on 2007-06-05
Please post your "cat /etc/iftab" and your "cat /etc/network/intefaces".
And the output of "dmesg | grep eth0" and then with eth1.

Do you know whether your router is using DHCP or not?

edit: @reckless2k2: you burnt me!

---

### Post by Ryzol on 2007-06-05
So weird, I turned it off for a bit, came back, turned it on and now it works. Thanks for the help!

---

### Post by reckless2k2 on 2007-06-06
In that case, it could be a hardware issue between NIC, router, and or modem. Keep an eye on it.

---

