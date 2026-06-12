---
title: "Static IP and broadcasting Hostname from etc/hosts"
date: 2013-11-13
forum: Networking &amp; Wireless
---

### Post by greavette on 2013-11-13
Hello,

I'm actually running Debian Wheezy, but I'm hoping what i'm doing is similar to what I would do on Ubuntu. :)

I've set a static ip address on my server.  I've updated /etc/hostname and /etc/hosts to give this server a hostname.  I do have a DNS server on our gateway but no entry has been made to this DNS Server for this Debian Server. 

My question is..when I scan my network (I'm using Softperfect Network Scanner), any Server/Workstation that gets it's IP dynamically from our router has a hostname displayed.  But for this server that I've setup a static IP, no hostname is displayed.  Here is what I put into my interfaces file:

# The primary network interface
auto eth0
iface eth0 inet static

address 10.110.1.179
netmask 255.255.255.0
gateway 10.110.1.1
broadcast 10.110.1.255

Do I need to add anything to the interfaces file or to my /etc/hosts file that will broadcast out to my network the hostname associated with this server?  Or do I need to add the DNS name to router/gateway so it knows the hostname for this server?

Thank you.

---

### Post by TheFu on 2013-11-13
If you want other machines to locate this "server" by a name, then you need to modify DNS or the /etc/hosts file or the NIS+ hosts on the network.
Only MSwindows machines broadcast their machine-name (often the same as hostname, but not always). This is due to netbios. Samba may do the same, if installed and running on linux.

---

### Post by Iowan on 2013-11-13
If it's capable, you might consider setting up a static lease (reserved address) on the router. The server can use DHCP, get the same address, and (probably) be treated like the rest of the machines.

---

