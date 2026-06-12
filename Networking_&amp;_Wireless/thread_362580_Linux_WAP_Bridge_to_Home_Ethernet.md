---
title: "Linux WAP Bridge to Home Ethernet"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by quintok on 2007-02-15
Hi Guys,
I am currently trying to get my nintendo wii onto the internet by using linux as it's WAP.  I have a bcm43xx network card with firmware installed, I also have had to use the wireless-dev fork of the kernel on kernel.org to enable "mode master" on this card.  Currently I can get the wii to access the wireless card but the bridge does not seem to want to work (which could quite possibly be a hardware issue).  Here is my /etc/network/interfaces file:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
  address 10.0.0.1
  netmask 255.255.255.0
  gateway 10.0.0.138

#auto br0
#iface br0 inet dhcp
# pre-up ifconfig eth0 down
# pre-up ifconfig eth1 down
# pre-up iwconfig eth1 mode master
# pre-up brctl addbr br0
# pre-up brctl addif eth0
# pre-up brctl addif eth1
# pre-up ifconfig br0 up
# post-down brctl delbr br0

```

This is actually so I can get on the internet, however when I'm testing it is inversed, with eth0 commented and br0 uncommented followed by
```
sudo ifdown -a & sudo ifup -a
```.  eth1 is my wireless card and I'm quite certain it works as the ESSID is found by the wii it just fails the connection test (which I assume is something like ping [www.nintendo.com)](www.nintendo.com)).
Is there something I could quite have easily missed? Also, do you know a good diagnostic toolkit for this work because I can't tell what's going on.... unless you count gnome-netstatus-applet :)

Thankyou.
-Q

---

