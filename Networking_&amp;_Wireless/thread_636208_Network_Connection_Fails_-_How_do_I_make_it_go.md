---
title: "Network Connection Fails - How do I make it go?"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by Sagadon on 2007-12-09
I've been struggling with my networking on my first-time Ubuntu install, and haven't had much luck with network connectivity. When I first installed, everything worked fine, but at some point between then, de-installing open-office, and running all the updates, it stopped working.  I've tried both DHCP and Static IP without success. Here's the skinny:

OS: Ubuntu 7.04

NIC: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 05)

/etc/resolv.conf:
> nameserver 192.168.1.120

/etc/network/interfaces:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


ifconfig:
> [eth0 Link encap:Ethernet  HWaddr 00:90:xx:xx:xx:xx
UP BORADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b)  TX bytes:0 ( 0.0 b)

eth0:avah Link encap:Ethernet  HWaddr 00:90:xx:xx:xx:xx
inet addr: 169.254.4.242 Bcast:169.254.255.255 Mask 255.255.0.0
UP BROADCAST MULTICAST  MTU:1500  Metric:1

Loopback entry

dhclient eth0:
> Internet Systems Consortium DHCP Client V3.0.4

Listening on LPF/eth0/00:90:xx:xx:xx:xx
Sending on LPF/eth0/00:90:xx:xx:xx:xx
DHCPDISCOVER on eth0 to 255.255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Currently it's configured for DHCP, but I've also tried setting a static IP and DNS the same as an XP box I also have on the router.  I know the issue is not the router - I've had multiple XP systems hooked up to it without any problems.

What steps should I take to get my wired networking functioning?

---

### Post by dannemil on 2007-12-09
> **Sagadon said:**
> I've been struggling with my networking on my first-time Ubuntu install, and haven't had much luck with network connectivity. When I first installed, everything worked fine, but at some point between then, de-installing open-office, and running all the updates, it stopped working.  I've tried both DHCP and Static IP without success. Here's the skinny:

OS: Ubuntu 7.04

NIC: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 05)

/etc/resolv.conf:


/etc/network/interfaces:



ifconfig:


dhclient eth0:


Currently it's configured for DHCP, but I've also tried setting a static IP and DNS the same as an XP box I also have on the router.  I know the issue is not the router - I've had multiple XP systems hooked up to it without any problems.

What steps should I take to get my wired networking functioning?

At least try to put in the gateway and netmask into your interfaces file:

$sudo gedit /etc/network/interfaces

#make it look like this

auto eth0
iface eth0 inet dhcp
netmask 255.255.255.0
gateway 192.168.15.1    #put in the internal ip address for your router 192.168.1.1 ?????

You will have to put in the internal ip address of your router in place of 192.168.15.1

save the file and close gedit

Then restart networking

sudo /etc/init.d/networking restart

---

### Post by Sagadon on 2007-12-09
Added the two lines.  The results are the same:
> DHCPDISCOVER on eth0 to 255.255.255.255 on port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I have also tried statically setting these as well as the IP address with no success.  I've searched and searched, and tried everything with no luck.

Thanks for your quick reply btw!

---

### Post by satish_buntu on 2007-12-09
I had a problem with my dual boot machine with XP and ubuntu. Apparently, XP update had messed up the network card (don't ask me how it can do that). I wasn't able to use the network in Ubuntu. I read some messages posted and then rolled back network driver update from XP and then network card worked in Ubuntu as it was working before.

---

### Post by Sagadon on 2007-12-09
I don't have dual boot on this machine. It's only Ubuntu on the one drive with one partition.  I'm also not running any virtual machines with XP.

---

### Post by Sagadon on 2007-12-10
Does anyone have any other suggestions?  I still have no networking on my system.

---

### Post by sherrife on 2007-12-11
I have the same issue with being unable to change the netmask address from 255.255.255.255 to 255.255.255.0... Even after editing the /networking/interfaces file and using the konsole to do it manually!

Not sure if that's even important, but argh... Linux loses so much of its appeal without the internet and the associated updates and customisations.

---

### Post by kevdog on 2007-12-11
Likey the updates broke your wireless packages, so Im not sure if anything is going to work.  I would try connecting from the command line to an unencrypted network first.  The instructions are in my signature.

---

### Post by Sagadon on 2007-12-11
I do not have a wireless card.  My card is an Intel PC100 oldschool PCI card.

What steps should I take to try to get Ubuntu's networking functioning?

---

### Post by Sagadon on 2007-12-12
( in a deeper voice)

Hey, it sounds like maybe your NIC isn't working. How about trying another NIC?

(back in my normal voice)

Oh, that's a good idea...  So how do I go about installing a different network card?  Do I just shutdown and pull the old one out and put the new one in?  Do you need to install drivers somehow?

---

### Post by Sagadon on 2007-12-13
It turns out, the ethernet card was partially seatted in the PCI slot. Enough so that it was visible to lspci, and would enable via ifup eth0, but not enough that it could communicate with anything.  I think this is rare, and probably not anyone else's situation.  I find it hard to believe, even now, that Ubuntu could see the thing while it was slightly popped out of the PCI slot, but whoomp. There it is.

---

