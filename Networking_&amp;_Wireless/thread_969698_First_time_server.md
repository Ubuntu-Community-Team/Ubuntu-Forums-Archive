---
title: "First time server"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by abandonedthe_mulletator on 2008-11-03
Hi I am setting up a home server for the first time.
The problem I am having right now is connecting my home network to the internet.

I have an old pc running ubuntu server and it is connected like this:
Internet <--> Ubuntu Server <--> Ethernet Hub <--> LAN Machines

I have taken out the hub and hooked up just one laptop to set this up.
The server can connect to the internet via eth0.
I have no problems updating and installing software from the server.
The laptop can connect to the server via eth1.
The laptop can run webmin on the server and they can ping each other.
However the laptop cannot connect to the internet.

I have installed and configured Shorewall firewall which a appears to be running fine.

Any ideas?

---

### Post by jimv2000 on 2008-11-03
You need to setup a DHCP server to give out IP addresses to your other machines.

Here's a quick and dirty how-to:

[http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html)

---

### Post by abandonedthe_mulletator on 2008-11-03
Thanks.  I set up the DHCP and it gives out IP address.

The problem remains though.
It works exactly the same just my laptop has different IP address.

---

### Post by Iowan on 2008-11-03
Does this How-To on [Internet/Connection Sharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing") provide any useful information?

---

### Post by abandonedthe_mulletator on 2008-12-13
YES!
That website did help.
After a long searching and learning process I determined that the bind9 DNS server wasn't doing what I wanted to.

I installed the dnsmasq and dhcp from that site that Iowan recommended.

My server is running nicely now.

Thanks guys!

---

