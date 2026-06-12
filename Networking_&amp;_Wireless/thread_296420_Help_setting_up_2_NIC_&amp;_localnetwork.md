---
title: "Help setting up 2 NIC &amp; localnetwork"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by gertjan_hofman on 2006-11-09
I have very simple networking situation - or it should be but I haven't been able to make it work.

I have an Ubuntu 6.06 machine with 2 NIC cards. One card (1) is connected to our intranet, and via a gateway, to the internet

The other card (2) is connected to a single-board computer (SBC) running Debian Sarge via a cross-over cable.

I want the SBC computer to be able to see intranet & internet.  I have assigmed the SBC the IP 192.168.0.50 and card(2) in the Ubuntu machine 192.168.0.1. They communicate fine. I can even ping card(1) from the SBC, but nothing else on the intranet.

I have tried numberous /sbin/route add combinations but nothing convinces my Ubuntu machine to get as a gateway. Any one has a HOWTO on this ?

I think I have to set /proc/sys/net/ipv4/ip_forward to 1, but that did help.


Much appreciated

Gertjan

---

### Post by ssalman on 2006-11-09
Try [this ]("https://help.ubuntu.com/community/InternetConnectionSharing")how-to. still, I'm not sure if that is what your looks for or not.:)

---

### Post by mips on 2006-11-09
[http://www.ubuntuforums.org/showthread.php?t=269235](http://www.ubuntuforums.org/showthread.php?t=269235)

Use Firestarter, it does not get any easier. Look at the above post as an example.

---

### Post by gertjan_hofman on 2006-11-10
Thanks both of you for answering.  The link to the other Ubuntu forum put me on the right track. For the record, here is what I did:

[CENTER]**Internet Sharing or Using Linux as a Router**[/CENTER]

Scenario - you have one PC (A) with two ethernet connections (wireless or otherwise).  Card ath0 is connected to the outside world via a gateway, usually given by you internet provider.

You connected a second computer B via cross over cable to eth0 on computer A. How can you make computer B talk to the internet.

Two networks - for clarity I am going to use:
192.168.0.0    for network between A and the Internet router
192.168.10.0   for the little local network between A & B

There are a couple of parts. First of all you have to tell each machine how to route traffic. You have to enable forwarding, which in 2.6 kernels is done in /proc.  Most confusingly, since computer B's address isnt actually known to the internet, you have to use NAT: See [http://users.pandora.be/mydotcom/howto/lanconnect/router/linux.htm](http://users.pandora.be/mydotcom/howto/lanconnect/router/linux.htm)


1. Set up computer B:

ifconfig eth0 192.168.10.50   (I picked 50 randomly)
route add default gateway 192.168.10.1          (tell B that ALL traffic should go there)
Check with route:



2. switch on IP forwarding on computer A:

echo 1 > /proc/sys/net/ipv4/ip_forward

check with:  cat /proc/sys/net/ipv4/ip_forward

3. set up  eth0 on computer A:
  ifconfig eth0 192.168.10.1
  route add -net -n 192.168.10.0 netmask 255.255.255.0 dev eth0
 
4. I am assuming that ath0, the connection to the rest of the world is set up with DHCP using your provider.

check with route:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *                255.255.255.0   U     0      0        0 ath0
192.168.10.0    *               255.255.255.0   U     0      0        0 eth0
192.168.10.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0           UG    0      0        0 ath0

Now do the NAT translation stuff (just copied this....)

  iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE   ----> wrong see lines below
  iptables --append FORWARD --in-interface eth1 -j ACCEPT                                        ----> wrong see lines below

iptables --table nat --append POSTROUTING --out-interface ath0 -j MASQUERADE
iptables --append FORWARD --in-interface eth0 -j ACCEPT

And you should be done.

---

### Post by gertjan_hofman on 2006-11-14
There was an error in my last post...so just for the record, the iptables line should have read:
iptables --table nat --append POSTROUTING --out-interface ath0 -j MASQUERADE
iptables --append FORWARD --in-interface eth0 -j ACCEPT

i.e. the out interface is ath0 in my example and the in interface eth0.

---

### Post by mips on 2006-11-15
> **gertjan_hofman said:**
> There was an error in my last post...

Why not edit your post then to correct the error ??? Click on the Scisscor Icon, bottom right of your post.

---

