---
title: "[SOLVED] Help W/Wired Network Manual Config???"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by kshane on 2008-06-06
Did a fresh install of Kubuntu 8.04 on a separate partition and it seemed to go fine, except I cannot connect to the internet. I have edited /etc/network/interfaces to show:
```

auto eth0
iface eth0 inet static
address 172.16.63.212
netmask 255.255.240.0
gateway 172.16.48.1
```

The Network Manager doesn't give an option to do a static ip.

I have a triple-boot system with a Vista partition, a regular Gnome Ubuntu and Kubuntu (where I'm having trouble).  Windows does DHCP just fine.  My Gnome Ubuntu doesn't work with DHCP, but I am easily able to setup a static ip through Network Manager and have no other problems with internet.  Only the Kubuntu install will not allow me an option to do a static ip.  I have tried the below command line to try and establish a connection, but no luck...

```

sudo ifconfig eth0 down
sudo ifconfig eth0 172.16.63.212 netmask 255.255.240.0
sudo route add gw 172.16.48.1
sudo ifconfig eth0 up
```

Can anyone please help?

Kevin

---

### Post by kshane on 2008-06-06
bump

---

### Post by kshane on 2008-06-06
The only "help" I've found is for wireless networking, which doesn't help much...

Kevin

---

### Post by kshane on 2008-06-07
Bummer!  Got no help.  But the good thing is I kept looking around.  Finding I had actually done it right all along.  For some reason the network card never picked up on the new settings AND restarted properly.  Confirmnation to this noob would have been nice.

Basically, if you're having trouble with dhcp and need to make your ip static, here's how and also to make sure it boots up that way each time...

Make sure your "/etc/network/interfaces" shows your network device (eth0, in my case) make sure your ip number and others match.  If dhcp is working for you, then replace the word static with dhcp and delete the rest of the entry for eth0.

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 172.16.63.212
netmask 255.255.240.0
gateway 172.16.48.1

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

```

Then, one at a time, execute the following lines, substituting your **device/numbers**:

```

sudo ifconfig **eth0** down
sudo ifconfig **eth0 172.16.63.212** netmask **255.255.240.0**
sudo ifconfig **eth0** up

```

I hope this helps someone else.  Networking seems to spook some folks...

Kevin

---

