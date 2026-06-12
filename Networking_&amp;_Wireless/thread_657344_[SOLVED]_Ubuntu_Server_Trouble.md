---
title: "[SOLVED] Ubuntu Server Trouble"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by Kewley on 2008-01-03
I'm having loads of trouble trying to get my Ubuntu server to work. I downloaded and installed it today, and it is currently connected to my Netgear WPN824 router. The router is showing that something is plugged into port 1, however on the router config page, it only shows that my laptop is connected. I've changed some of the network settings, following some tutorials, in an attempt to get OpenSSH working, but I am still unable to connect.

When I try to update the server 'apt-get update' It fails with the error 'temporary failure resolving......'.

Any help would be great. My aim is to have the server as a file server for my laptop and other desktop, as well as a web server so I can access the files on the internet.

I've tried the following tutorials:
[http://www.ubuntugeek.com/ubuntu-704...ver-setup.html](http://www.ubuntugeek.com/ubuntu-704...ver-setup.html)
[http://www.howtoforge.com/perfect_setup_ubuntu704_p3](http://www.howtoforge.com/perfect_setup_ubuntu704_p3)

---

### Post by Predator[23rd] on 2008-01-03
Hi!

more informations pls!

what do **lspci** and **ifconfig** say ...

---

### Post by Kewley on 2008-01-03
Hi, sorry this is a bit late.

This is the output from lspci, I've only copied the ethernet info though: 

01:0d.0 Ethernet controller: Realtek Semiconductor co., Ltd. RTL -8139/8139c/8139c+ (rev 10)


ifconfig output:

eth0      link encap:Ethernet HWaddr 00:11:09:2F:B5:41
inet addr:192.168.0.100 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::211::9ff:fe2f:b541/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric1
RX packets:130 errors:0 dropped:0 overruns:0 frame:0
TX packets:29   errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:17070 (16.6KB) TX bytes:26662 (26.0 KB)
Interrupt:20 Base address:0x8000

lo    Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:128 errors:0 dropped:0 overruns:0 frame:0
TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:12792 (12.4 KB) TX bytes:12792 (12.4 KB)

Again help is greatly appreciated :).

---

### Post by Kewley on 2008-01-03
bump

---

### Post by Kewley on 2008-01-03
Come on, sombody out there must know what I'm doing wrong. 

I'm off to catch a bit of sleep.

---

### Post by Predator[23rd] on 2008-01-04
Sorry, I was sleeping. :D

Well, your network card is detect and configured. That is the most important part. The rest is only a minor configuration detail ...

I guess your Netgear router is configured to be a DHCP server, right? I also assume that your laptop has internet.

can you tell us what your */etc/network/interfaces* says?

---

### Post by Kewley on 2008-01-04
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

---

### Post by sdide on 2008-01-04
You NIC is staticly configured, hence it does not get DNS servers from DHCP. So to make it resolve names, you need to enter some DNS servers.

edit /etc/resolv.conf 

and enter lines

nameserver <ip_of_nameserver_1>
nameserver <ip_of_nameserver_2>

you can see the nameserver on you other machines. If on windows, do 

> ipconfig /all 
and look for DNS servers in the output.

if on linux look in /etc/resolv.conf.

---

### Post by njparton on 2008-01-04
I have the same router and I think the gateway address should be 192.168.1.1 unless you've manually changed it?

Use the same IP address for your DNS server settings in "resolv.conf".  Your router will then forward this request onto your ISPs DNS servers.

---

### Post by Kewley on 2008-01-04
Thanks for the help, but the I'm still getting the same problem.

The gateway is 192.168.1.1 sorry, thanks for pointing that out.
I changed that in the interfaces file, and then the resolv.conf file. But when I ran "sudo /etc/init.d/networking restart", I got the following output: 

*reconfiguring networking interfaces...
SIOCADDRT: No such process
Failed to bring up eth0.
[ OK ]

Thanks to everyone for the help so far :).

Edit: Though I would post the contents of resolv.conf, just in cast it's useful:

nameserver 192.168.1.1

---

### Post by Predator[23rd] on 2008-01-04
> **Kewley said:**
> nameserver 192.168.1.1

that will most probably not work ... enter your ISP's DNS IPs instead.

don't forget that your IP has to be also something like 192.168.1.x, e.g.

[I]auto eth0
iface eth0 inet static
  address 192.168.1.100
  netmask 255.255.255.0 
  network 192.168.1.0
  broadcast 192.168.1.255
  gateway 192.168.1.1
[/I]

try restarting again ... **sudo /etc/init.d/networking restart**

---

### Post by metoor30 on 2008-01-04
> **Kewley said:**
> Hi, sorry this is a bit late.

ifconfig output:

eth0      link encap:Ethernet HWaddr 00:11:09:2F:B5:41
inet addr:192.168.0.100 Bcast:192.168.0.255 Mask:255.255.255.0
.

Your IP address is your problem.  You setup a static IP on a different subnet then your gateway router.  You need to edit your /etc/network/interfaces file and change any thing that says '192.168.0.xxx' to '192.168.1.xxx'.  

Hope this helps

---

### Post by Kewley on 2008-01-04
Thanks a lot to everyone for your help.

Everything is great now, I have SSH and web access. Going to start writing some PHP to allow the uploading and downloading of files.

Thanks again for your help :).

---

