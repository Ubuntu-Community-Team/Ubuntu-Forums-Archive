---
title: "Bridge Networking Troubles, loose static IP, networking gurus help!"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by Ngtstlkr on 2008-09-15
Okay, so I have VirtualBox installed and learned how to bridge my network and setup some interfaces so that VirtualBoxes can work.  Here is my /etc/interfaces:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

iface eth0 inet static
address 192.168.1.55
netmask 255.255.255.0
gateway 192.168.1.1

```



I then run this script on startup so that it sets up the networking I need for VBox to run properly:

```

tunctl -t vbox1 -u vboxuser
tunctl -t vbox2 -u vboxuser
chown root.vboxusers /dev/net/tun
chmod g+rw /dev/net/tun
brctl addbr br0
ifconfig eth0 0.0.0 promisc
brctl addif br0 eth0
dhclient br0
brctl addif br0 vbox1
brctl addif br0 vbox2
ifconfig vbox1 up
ifconfig vbox2 up
/etc/init.d/networking restart

```

Everything works GREAT!

Until...

Through a lot of trial and error and many hours of having to restart the network and reading / searching through as many psots as I can on this subject as well as just noticing when things go wrong, I have pieced together what I think happens is when the DHCP lease is up on the br0, it basically forces a different IP address to my eth0!  Basically it takes over my eth0 whenever the lease on the bridge is up and forces my eth0 into one of the IP's from my DHCP server.  To be completely thorough I have a Linksys WRT54GL v1.1 with the latest firmward from linksys.  (Haven't done the dd-wrt yet! :))

Am I correct in thinking it's the DHCP?  I increased the lease time on the DHCP server to the longest possible and it helps keep my box from getting eth0 taken over longer, so I think this is it.

Anyone have any ideas how I can force my eth0 to keep a static IP and keep it from being over run by the DHCP server?

---

### Post by Ngtstlkr on 2008-09-20
Anyone know how I can fix this?  Networking seems to act quite flakey lately.

---

