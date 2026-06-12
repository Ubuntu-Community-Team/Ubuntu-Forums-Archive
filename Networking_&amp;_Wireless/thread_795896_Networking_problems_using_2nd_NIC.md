---
title: "Networking problems using 2nd NIC"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by dylanhky on 2008-05-15
Hello everyone,

I've just installed ubuntu server 8.04 on a pc to serve as firewall/gateway.

Before I continue I'd like to roughly describe the network topology at my company.  We have a static ip line, using windows server 2003 for active directory+file+dns server (with one nic). All the hardware is connected through a switch including a cisco pix firewall/gateway which in turn is connected to a modem router. For example purpose lets say my internal network domain is xyz.com

We have a client who wishes to host their webserver in our office with a separate internet connection. If converted one of the older pcs to serve as a firewall/gateway for their webserver. Their domain name would be abc.com

The problem I face now is that the internet line has yet to be installed hence I would have to rely on my own company network for the internet connection (temporarily to setup the server). I bought a 2nd nic card to be installed in the pc, using the lspci command ubuntu shows that the network card is detected but upon using the ifconfig only eth0 and lo shows up on the screen. Eth0 is configured as a static ip using my company gateway ip and dns server ip.

command dmesg revealed these lines 
[34.191029]udev: renamed network interface eth1 to eth0
[34.227625]udev: renamed network interface eth0_rename to eth1
[45.424934]eht0: no IPv6 routers present

I've been using ubuntu as my home desktop but its the first time I'm using ubuntu server in an office environment. I don;t have exceptional skills in networking and I'm terrified.  Can anyone tell me what should I do to have eth1 working? thanks.

---

### Post by Iowan on 2008-05-16
Post results of **ifconfig -a** and contents of **/etc/network/interfaces.** Check MAC address to see if if that renaming verbage means what was eth1 is now eth0 (& vice-versa). When you're looking at **/etc/network/interfaces**, verify that there is a **auto eth1** line (presumably there will be one for eth0 and lo).

---

