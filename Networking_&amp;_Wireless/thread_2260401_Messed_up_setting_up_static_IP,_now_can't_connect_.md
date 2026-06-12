---
title: "Messed up setting up static IP, now can't connect to server"
date: 2015-01-11
forum: Networking &amp; Wireless
---

### Post by 1255525 on 2015-01-11
I attempted to set a static IP address on a local server by setting [COLOR=#333333][FONT=Monaco]/etc/network/interfaces 

to 
[/FONT][/COLOR]
```
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface

#iface lo inet interface
iface eth0 inet static
address 192.168.1.250
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 8.8.4.4
~           
```        

I believe I forgot to write in "auto eth0" in there and now cannot communicate with the server. Router does not see it as connected. What's the best way to get myself out of trouble and would adding in auto etho solve the problem?

---

### Post by chili555 on 2015-01-11
> would adding in auto etho solve the problem?I suspect so. Please add it:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.250
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 8.8.4.4
```Restart the interface:```
sudo ifdown eth0 && sudo ifup -v eth0
```Test:```
ifconfig
ping -c3 www.ubuntu.com
```

---

### Post by 1255525 on 2015-01-11
didn't work, but it was due to probably conflict between that and GUI settings. reverted it to how it was before and did it through GUI.

---

