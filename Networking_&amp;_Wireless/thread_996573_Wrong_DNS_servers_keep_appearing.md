---
title: "Wrong DNS servers keep appearing"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by Mazin on 2008-11-29
For some reason, two incorrect DNS servers keep being added to my list of DNS servers.  At system boot, my list of DNS servers is reset to

10.n.nn.nnn  (wrong)
10.nnn.nn.nnn  (wrong)
192.168.1.1 (correct dns server from DHCP)

causing a big lag whenever the system tries to resolve an address.  The system is supposed to get DNS servers from DHCP and it does, except the correct ones are added to the end of the list.  The DNS servers starting with 10.* are not in /etc/dhcp3/dhclient.conf.   Where could they be?

---

### Post by superprash2003 on 2008-11-29
enter the correct DNS servers like this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html) .. opendns servers 208.67.222.222 and 208.67.220.220 used in the above example , you can change to whatever you like.. better to use opendns

---

### Post by Mazin on 2008-11-29
I did.  The new DNS servers get added to the end of the list, after the wrong 10.x servers.

---

### Post by darco on 2008-11-29
You still need to update your router to point to the opendns servers...

darco

---

### Post by Mazin on 2008-11-29
Perhaps you don't understand my problem.   My problem is solely with this computer.  NetworkManager consistently adds two incorrect DNS servers to resolvconf's list of DNS servers.  I don't know where it has these two incorrect servers stored, else I would go in and remove them.

---

### Post by superprash2003 on 2008-12-01
use static ip address instead of dhcp then it wont use the router's DNS servers. [http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html) .. post output of /etc/dhcp3/dhclient.conf

---

### Post by Mazin on 2008-12-01
Where does NetworkManager store its configuration?

The incorrect DNS servers are not on the router; they are on my computer.  I would like to use the router's DNS server, but NM still adds those two incorrect entries before the DNS it gets from DHCP.

dhclient.conf
(notice that I do not have any prepend commands.)
```
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

---

### Post by Iowan on 2008-12-01
Check */etc/resolv.conf*.  That file *should* be a receptacle.  Whatever is grabbing 10.x.y.z may put it back there... if it's there at all.

---

### Post by superprash2003 on 2008-12-02
as mentioned by lowan try removing those 2 dns address' from the /etc/resolv.conf file

---

