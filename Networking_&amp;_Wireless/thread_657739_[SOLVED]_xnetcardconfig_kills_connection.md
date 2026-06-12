---
title: "[SOLVED] xnetcardconfig kills connection"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by taffer on 2008-01-03
I'm am having a strange problem with my ethernet connnection.  I have a public static ip on a wired connection hooked to a bridged DSL modem.  I was using the Network manager applet to control my network settings and everything was working fine.  One day, I used ***xnetcardconfig*** to see how it worked.  I put all of my static ip settings in and it continued to work until I rebooted.  After that my internet connection broke.  I can get it to work by reentering my settings using ***xnetcardconfig***, but it breaks again when I reboot, or "bounce" the interface using ```
ifconfig eth0 down
``` followed by ```
ifconfig eth0 up
```.  When the connection is broken, I cannot ping my gateway, but an ```
ifconfig -a
``` shows that the interface is up, and has all of the correct settings.  

Let me know what other information you need, and thank you in advance for any assistance.

---

### Post by taffer on 2008-01-03
Found the problem.

Looks like ***xnetcardconfig*** was putting info in /etc/network/interfaces in the wrong spot.

The file looked like this(Ips changed to protect the identity ofthe innocent):

```
auto lo
iface lo inet loopback


#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

address 10.4.12.150
netmask 255.255.252.0
gateway 10.4.12.1

auto eth0
iface eth0 inet static
        address 10.4.12.150
        netmask 255.255.252.0
        gateway 10.4.12.1

```

Changed file to the following fixed it:

```
auto lo
iface lo inet loopback


#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

#address 10.4.12.150
#netmask 255.255.252.0
#gateway 10.4.12.1

auto eth0
iface eth0 inet static
        address 10.4.12.150
        netmask 255.255.252.0
        gateway 10.4.12.1

```

---

### Post by www.rzr.online.fr on 2008-05-14
As xnetcardconfig upstream,

Can you reproduce the bug ? if yes please report how to reproduce the bug and I'll fix it :

[https://launchpad.net/xnetcardconfig/](https://launchpad.net/xnetcardconfig/)

---

