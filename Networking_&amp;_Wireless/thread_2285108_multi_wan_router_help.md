---
title: "multi wan router help"
date: 2015-07-03
forum: Networking &amp; Wireless
---

### Post by atux on 2015-07-03
hello everyone. i do need some help in setting my pc as a router. it has three ethernet cards (eth0, 1, 2)
-eth0 & 1 are the wan ports. the modems of the ISP are in bridge mode and i do have the username/passwd of the connections 
username1:user1@dsl.com passwd1:foo1, username2:user2@dsl.com passwd1:foo2
-eth2 is the LAN 192.168.2.1/24 and it will give dhcp to clients from 192.168.2.10-59 lease time is 0s.
-for dns the router will use the google dns 8.8.8.8 and 4.2.2.2

i would like to have the router as load balance per connection. also in case of failure of one of the wan connections to be transparent to the user which connection it will use. finally i would like a port forward for both connections of ports 1723 and 4423 tcp at 192.168.2.98

please for your help. it is very urgent and very important. since my dsl connections are really bad i do need to have constant internet access, please.

---

### Post by nlee2 on 2015-07-03
There is firmware to transform your pc into a multi-wan router but I am not aware of any that is based on ubuntu. Have you research any firmware to run on your pc?

---

### Post by atux on 2015-07-03
i would like to have this to run in my ubuntu system

---

### Post by nlee2 on 2015-07-03
and yet you say it is urgent and important to you.

---

### Post by atux on 2015-07-03
i did setup pfsense to do the load balance. ok it does the job.
the problem is that i cannot run all of my software in that PC as well the router.
this is the reason i am looking in ubuntu.

---

### Post by nlee2 on 2015-07-03
Tried pfsense vm in kvm?

---

### Post by atux on 2015-07-03
not really a fan of it.
is there any way to get rid of pfsense and stick on ubuntu?
it will be really nice to have it ubuntu

---

### Post by atux on 2015-07-27
i have setup pfsense to do the job, but i need it to run the dual wan in a linux box.
in my search i have found the [http://ubuntuforums.org/showthread.php?t=2214561](http://ubuntuforums.org/showthread.php?t=2214561) and i have a few problems during the installation. i got some errors that i cannot find a way to solve them. i do attach a log of the installation and system details. could someone help, please?

I had a solution in my installation issues. i had to run apt-get --reinstall install perl to fix it.

---

### Post by atux on 2015-07-28
could someone help me with the config of that utility please? 
i got the software installed but i cannot get to the internet.
i have :
auto lo
iface lo inet loopback
#WAN 1
auto eth0
iface eth0 inet static
        address         192.168.178.79
        netmask         255.255.255.0
        gateway         192.168.178.1
#WAN 2
auto eth1
iface eth1 inet static
        address         192.168.2.79
        netmask         255.255.255.0
#LAN
auto eth2
iface eth2 inet static
        address         192.168.1.1
        netmask         255.255.255.0
        post-up /etc/network/load_balance.pl


# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.178.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0



is there anything i am missing?

---

### Post by houstonbofh on 2015-07-28
Multi WAN is hard.  Very hard.  There is a reason that of the m0n0wall children, only pfSense (and OPNsense when it works) does it.  However, pfSense can do it on low end hardware.  If you can get an old thin terminal with an expansion slot, you can have a 5 port firewall for under $100. (Depending on how good the thin terminal is, you may be limited to 60meg or so)  Or you can get dedicated hardware like this. [http://www.mitxpc.com/products.php?cat=140](http://www.mitxpc.com/products.php?cat=140)  These come with SmallWall installed, but should support pfSense embedded version.

---

### Post by atux on 2015-07-31
at the moment i have a pfsense running in a server. i got the job done. the issue is that i would like it to run in linuxes of the debian family, preferably ubuntu.
The reason for that is that i have a lot of tailor made apps writen/compiled in ubuntu 12.05/debian 7 and it has to run together with the loadbalance/failover feature. this is why i am struggling to make it work in ubuntu

---

### Post by atux on 2015-08-11
i am still trying to make it work and i have found [http://wiki.ubuntuusers.de/Multiple_Uplink_Routing](http://wiki.ubuntuusers.de/Multiple_Uplink_Routing)
I have altered my config to make it as in the link. i am referring to the sketch of the above link.
the problems are:
-while in the router i can access the Internet only from eth1, not from eth2. ping -I eth1 8.8.8.8 works.  ping -I eth2 8.8.8.8 it does not work
-the PC client which connects to eth0 (LAN) it cannot access the Internet.

could someone help please?

---

