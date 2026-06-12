---
title: "internet connection from local network"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by gluk1024 on 2008-11-06
Hello all, I need some help configuring my network at home. I have 2 computers, 1st of them have 2 ethernet cards, one card is connected to adsl modem, and another to 2nd computer. I need to get acces to the internet from second computer.

/etc/network/interfaces on 1st computer:
------------------------------------------------------
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
  address 192.168.1.2
  netmask 255.255.255.0
  gateway 192.168.1.1
  broadcast 192.168.1.255

auto eth1
iface eth1 inet static
  address 192.168.0.1
  netmask 255.255.255.0
  broadcast 192.168.0.255
----------------------------------------------------

/etc/hosts on 1st computer:
----------------------------------------------------
127.0.0.1	        localhost
127.0.0.1	        gluk1024
192.168.0.1	gluk1024
192.168.0.2	ukur1024-desktop
------------------------------------------------------

/etc/network/interfaces on 2nd computer:
-------------------------------------------------------
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
  address 192.168.0.2
  netmask 255.255.255.0
  gateway 192.168.0.1
  broadcast 192.168.0.255
-------------------------------------------------------

/etc/hosts on 2nd computer:
-----------------------------------------------------
127.0.0.1	        localhost
127.0.0.1	        ukur1024-desktop
192.168.0.2	ukur1024-desktop
192.168.0.1	gluk1024
---------------------------------------------------

P.S.: Internet works fine on 1st computer

---

### Post by Iowan on 2008-11-06
Check [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") How-To on Internet/connection sharing.

---

### Post by gluk1024 on 2008-11-08
thanks a lot for info Lowan, I will try this today :)

---

### Post by gluk1024 on 2008-11-08
hm, I did all as it said in the How-to... though I still can't connect to the intenet from my second machine... mayabe the problem is that I turned off network manager from autostart(I did it because it was ignoring the configuration setttings in /etc/network/interfaces)?? Forgot to say I'm using kubuntu 8.10

---

### Post by gluk1024 on 2008-11-09
finally configured network, the problem was that I put openDNS servers in /etc/dhcp3/dhclient.conf, as it said in manual, though as I found, dhclient.conf is used by networkmanager to get DNS servers(maybe I'm wrong, if yes then I would be glad to hear what is it used for). But network manager is turned off on me computer as I said, so I manually wrote openDNS server's IP adresses into /etc/resolv.conf on second computer, and after restarting network I got my internet connection working :)

P.S. Thanks again for link on How-to ;)

---

### Post by Iowan on 2008-11-09
Glad it's working for you.  If you believe the problem is fixed, mark this thread [SOLVED] (Under Thread Tools). \\:D/

---

