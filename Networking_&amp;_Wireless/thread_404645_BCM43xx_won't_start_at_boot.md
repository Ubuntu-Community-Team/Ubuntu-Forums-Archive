---
title: "BCM43xx won't start at boot"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by jimmymac on 2007-04-08
Alright guys,

I've just installed Feisty and most things are working ok.

However, my bcm43xx doesn't work at boot.  I have to manually restart the networking every time I boot.

When I restart it I also get:

root@pluto:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
SIOCDELRT: No such process

is that message anything to worry about?

Any ideas?

Cheers,

Jimmy

---

### Post by klock on 2007-04-08
Jimmy,
 
 if you wouldnt mind posting your /etc/network/interfaces, that would help out.

 mine did the same thing when I upgraded, and all I had to do was re-add auto wlan0 to my /etc/network/interfaces, and it worked fine after that

The "SIOCDELRT: No such process" error message is normally generated when you
try to delete a route which doesn't exist of is no longer there.

---

### Post by jimmymac on 2007-04-09
My /etc/network/interfaces as requested:

```
root@pluto:~# more /etc/network/interfaces 
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet static
address 192.168.2.6
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid galaxy
wireless-key xxxxx
```

Righto off to work :mad: 

Cheers,

Jimmy

---

