---
title: "Editing /etc/network/interfaces destroying connections"
date: 2015-11-23
forum: Networking &amp; Wireless
---

### Post by SuperGeorge on 2015-11-23
When i try and add this to the /etc/network/interfaces file  it ruins my network cards saying no connected devices from the connection manager up by the clock in ubuntu 15.10

I have a 2nd install of ubuntu 10.04 using this and it works fine there.  Any ideas why this would fry my network connections?  i'm setting up a squid server and need this to work as it is on older ubuntu 10.04.  Thanx!

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

post-up iptables-restore < /etc/iptables.up.rules

auto eth1
iface eth1 inet static
address 192.168.2.1
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255

---

### Post by grahammechanical on 2015-11-23
Ubuntu has not made use of the interfaces file for years. Most likely since Ubuntu started using Network Manager because it causes conflict with Network Manager. Any changes to the default contents will cause conflict. This is the default.

> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

Regards.

---

### Post by HermanAB on 2015-11-23
Basically, you either have to use the NetworkDamager GUI thingy, OR you have to blow it away and handle the networking manually.  You cannot mix manual configuration with NetworkDamager...

---

### Post by SuperGeorge on 2015-11-23
Makes sense, thanx for the good info guys

---

### Post by Bucky Ball on 2015-11-23
Take note: 10.04 LTS is no longer supported. We can't give you a lot of support for it. Please upgrade to a supported release, 14.04 LTS is the current long-term support release, supported until 2019. 15.10 is also an option, supported until about July next year.

There are no updates/upgrades for 10.04 and as time goes on it will become more of a security risk. If you are told to install anything to fix issues, you cant'. The 10.04 repositories are no longer there. 

Backup and upgrade. Don't hesitate to post a new thread if you run into problems. :)

(PS: If you're using Network Manager you shouldn't be messing with the /interfaces file, but then, don't remember much about 10.04. That may have been different.)

---

### Post by tgalati4 on 2015-11-23
Check your /etc/NetworkManager/NetworkManager.conf file.  Flip the *manage=false* switch to *true*. Restart network services or reboot.

---

### Post by slickymaster on 2015-11-23
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by chili555 on 2015-11-23
> **SuperGeorge said:**
> When i try and add this to the /etc/network/interfaces file  it ruins my network cards saying no connected devices from the connection manager up by the clock in ubuntu 15.10

I have a 2nd install of ubuntu 10.04 using this and it works fine there.  Any ideas why this would fry my network connections?  i'm setting up a squid server and need this to work as it is on older ubuntu 10.04.  Thanx!

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

post-up iptables-restore < /etc/iptables.up.rules

auto eth1
iface eth1 inet static
address 192.168.2.1
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255As was noted before, please update to an Ubuntu version of at least 14.04 LTS.

Next, your file lacks the required DNS nameservers. 

Network Manager was pretty primitive in 10.04. If it were me, I'd probably remove it.

---

