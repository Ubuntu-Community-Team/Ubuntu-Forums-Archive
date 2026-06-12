---
title: "DHCPD.Conf Problem(newbie)"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by Peter_APIIT on 2007-12-13
Hello all network administrator, i have openbsd 4.1 box act as router in front of my ubuntu box. I don't know how to set up dhcpd.conf
This is contest of /etc/dhcpd.conf : 
shared-network LOCAL-NET{ option domain name "openbsd.my.domain"
option domain name server 202.188.0.133;
subnet 10.0.0.255 netamsk 255.0.0.0{option router 10.0.0.10;
range 10.0.0.25 10.0.0.30; max-lease-time 86400; default-lease-time 18000;}}
Error message : Address range 10.0.0.25 to 10.0.0.30 not on net 10.0.0.255/255.0.0.0; 
Contents of /etc/hostname.rl0(External interface) dhcp none none;
Contents of rl1(internal) inet 10.0.0.1 255.0.0.0 none
Contents of ral0(Wireless)inet 10.0.0.2 255.0.0.0 none media autoselect mediaopt hostap mode 11g nwid Hacker_WORLD nwkey xxxxx; 
I have /etc/dhclient.conf and /var/db/dhclient.lease.rl0 and /var/db/dhcpd.leases. 
Thanks for oyur help. Urgent. Your help os greatly appreciated by me and others.

---

### Post by crmanski on 2007-12-13
> **Peter_APIIT said:**
> Hello all network administrator, i have openbsd 4.1 box act as router in front of my ubuntu box. I don't know how to set up dhcpd.conf
This is contest of /etc/dhcpd.conf : 
shared-network LOCAL-NET{ option domain name "openbsd.my.domain"
option domain name server 202.188.0.133;
subnet 10.0.0.255 netamsk 255.0.0.0{option router 10.0.0.10;
range 10.0.0.25 10.0.0.30; max-lease-time 86400; default-lease-time 18000;}}
Error message : Address range 10.0.0.25 to 10.0.0.30 not on net 10.0.0.255/255.0.0.0; 

I think that you needs this line...
subnet 10.0.0.0 netmask 255.0.0.0
if you want to use this range...
range 10.0.0.25 10.0.0.30

---

### Post by Peter_APIIT on 2007-12-14
I ahve changed according to what u mentioned here but the error from /var/log/daemon showing
can't listen rl1 -it has no ip address 
can't listen on YES - it has no ip address
I don't know what wrong with it. I hope you all can help me out. 
Your help is greatly appreciated by me and others.

---

### Post by Peter_APIIT on 2007-12-14
I try to plugin the cable to internal interface which is rl1. No address being assigned to this after i connect to another machine. 
This error i get it from /var/log/daemon :
1. openbsd[12661]:tun 0:warning:0.0.0.0/0: change route failed: errno: No such process
2. tun0:warning:ff01:7::/32: change route failed: errno:Network is unreachable
3. tun0:warning:ff02:7::/32 change route failed: errno:Network is unreachable
I hope this help. 
Thanks for your help.

---

### Post by Peter_APIIT on 2007-12-14
Any help is greatly appreciated by me and others.

---

### Post by Peter_APIIT on 2007-12-15
Urgnet.Please

---

### Post by Peter_APIIT on 2007-12-16
Please help me.

---

### Post by Peter_APIIT on 2007-12-17
Help me please.

---

