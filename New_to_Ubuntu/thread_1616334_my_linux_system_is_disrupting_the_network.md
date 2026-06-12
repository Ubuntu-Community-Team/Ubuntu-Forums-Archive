---
title: "my linux system is disrupting the network"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by nnamdi on 2010-11-08
good morning everyone..

am network / system admin in my work place but i personally run kubuntu on my personal laptop. but i noticed that my system ip is been sent out to other system as a default gateway cos i run a dhcp in my network a class C ip system. my gw is 192.168.0.250, so now some system can go to the internet but while some cant because they use their gw as 192.168.0.2 which is my system dhcp ip.. now i had to manually use a static ip. cos i remember install a dhcp server on my system could it be the cos.... dont know if my system is routing that ip address.

---

### Post by toekneewood on 2010-11-08
Sorry if this is teaching you to suck an egg, but if you are running dhcp on you system that is connected to your work LAN it will issue IP addresses.  to turn it off or on use the following
```
 sudo /etc/init.d/dhcp3-server stop 
```
If you want to stop it from starting up at every reboot then use:
```
 update-rc.d dhcp3-server remove 
```
you will then need to start it manually with:
```
 sudo /etc/init.d/dhcp3-server start 
```
that way you will have control of the DHCP Server
Hope this helps :-)

---

### Post by nnamdi on 2010-11-08
thanks man i have tried it let me look at it and also monitor the network...

---

### Post by toekneewood on 2010-11-08
To view active leases
```
 cat /var/lib/dhcp3/dhcpd.leases | less 
```

---

### Post by nnamdi on 2010-11-08
but i have already done this
```

sudo /etc/init.d/dhcp3-server stop

```

then ran this command

```

cat /var/lib/dhcp3/dhcpd.leases | less

```
```


# The format of this file is documented in the dhcpd.leases(5) manual page.
# This lease file was written by isc-dhcp-V3.1.3

lease 192.168.0.100 {
  starts 5 2010/10/29 13:49:09;
  ends 5 2010/10/29 13:51:09;
  tstp 5 2010/10/29 13:51:09;
  cltt 5 2010/10/29 13:49:09;
  binding state free;
  hardware ethernet 00:1d:72:0c:bd:a9;
  uid "\001\000\035r\014\275\251";
  client-hostname "user-eca056f830";
}
lease 192.168.0.101 {
  starts 5 2010/10/29 14:10:14;
  ends 5 2010/10/29 14:13:11;
  tstp 5 2010/10/29 14:13:11;
  cltt 5 2010/10/29 14:10:14;
  binding state free;
  hardware ethernet 00:1f:16:4b:52:13;
  uid "\001\000\037\026KR\023";
}
lease 192.168.0.104 {
  starts 5 2010/10/29 14:34:42;
  ends 5 2010/10/29 14:36:42;
  tstp 5 2010/10/29 14:36:42;
  cltt 5 2010/10/29 14:34:42;
  binding state free;
  hardware ethernet 00:30:67:49:14:f8;
  uid "\001\0000gI\024\370";
  client-hostname "SPMHN1";
}
lease 192.168.0.105 {
  starts 5 2010/10/29 14:44:48;
  ends 5 2010/10/29 14:46:48;
  tstp 5 2010/10/29 14:46:48;
  cltt 5 2010/10/29 14:44:48;
:}
lease 192.168.0.102 {
  starts 5 2010/10/29 15:21:28;
  ends 5 2010/10/29 21:21:28;
  tstp 5 2010/10/29 21:21:28;
  cltt 5 2010/10/29 15:21:28;
  binding state free;
  hardware ethernet 00:1e:33:cd:dc:f0;
  uid "\001\000\0363\315\334\360";
}
lease 192.168.0.106 {
  starts 5 2010/10/29 16:26:26;
  ends 5 2010/10/29 22:26:26;
  tstp 5 2010/10/29 22:26:26;
  cltt 5 2010/10/29 16:26:26;
  binding state free;
  hardware ethernet 00:1b:24:1c:cd:e2;
  uid "\001\000\033$\034\315\342";
}
lease 192.168.0.112 {
  starts 2 2010/11/02 11:48:04;
  ends 2 2010/11/02 11:50:04;
  tstp 2 2010/11/02 11:50:04;
  cltt 2 2010/11/02 11:48:04;
  binding state free;
  hardware ethernet 00:16:36:1e:c3:95;
  uid "\001\000\0266\036\303\225";
  client-hostname "user-a29d9fc66f";
}
lease 192.168.0.114 {
  starts 2 2010/11/02 12:28:00;
  ends 2 2010/11/02 12:30:00;
  tstp 2 2010/11/02 12:30:00;
  cltt 2 2010/11/02 12:28:00;
  binding state free;
  hardware ethernet 00:1e:ec:36:e9:cb;
  uid "\001\000\036\3546\351\313";
:}
lease 192.168.0.116 {
  starts 2 2010/11/02 12:45:20;
  ends 2 2010/11/02 12:47:20;
  tstp 2 2010/11/02 12:47:20;
  cltt 2 2010/11/02 12:45:20;
  binding state free;
  hardware ethernet 00:30:67:49:14:00;
  uid "\001\0000gI\024\000";
  client-hostname "mdsec";
}
lease 192.168.0.117 {
  starts 2 2010/11/02 13:26:01;
  ends 2 2010/11/02 13:28:01;
  tstp 2 2010/11/02 13:28:01;
  cltt 2 2010/11/02 13:26:01;
  binding state free;
  hardware ethernet 00:e0:4c:77:32:c1;
  uid "\001\000\340Lw2\301";
  client-hostname "spmhn-01-Sec";
}
lease 192.168.0.109 {
  starts 2 2010/11/02 13:26:32;
  ends 2 2010/11/02 13:28:06;
  tstp 2 2010/11/02 13:28:06;
  cltt 2 2010/11/02 13:26:32;
  binding state free;
  hardware ethernet 00:1b:24:03:52:46;
  uid "\001\000\033$\003RF";
}
lease 192.168.0.118 {
  starts 2 2010/11/02 13:34:12;
  ends 2 2010/11/02 13:36:12;
  tstp 2 2010/11/02 13:36:12;
  cltt 2 2010/11/02 13:34:12;
  binding state free;
  hardware ethernet 00:30:67:49:12:9d;
:
}
lease 192.168.0.119 {
  starts 2 2010/11/02 13:34:42;
  ends 2 2010/11/02 13:36:42;
  tstp 2 2010/11/02 13:36:42;
  cltt 2 2010/11/02 13:34:42;
  binding state free;
  hardware ethernet 00:30:67:49:15:13;
  uid "\001\0000gI\025\023";
  client-hostname "fnhe11";
}
lease 192.168.0.120 {
  starts 2 2010/11/02 13:38:33;
  ends 2 2010/11/02 13:40:33;
  tstp 2 2010/11/02 13:40:33;
  cltt 2 2010/11/02 13:38:33;
  binding state free;
  hardware ethernet 08:00:27:8f:50:ad;
  uid "\001\010\000'\217P\255";
  client-hostname "test";
}
lease 192.168.0.121 {
  starts 2 2010/11/02 14:21:07;
  ends 2 2010/11/02 14:23:07;
  tstp 2 2010/11/02 14:23:07;
  cltt 2 2010/11/02 14:21:07;
  binding state free;
  hardware ethernet 00:1f:16:e3:3d:ea;
  uid "\001\000\037\026\343=\352";
  client-hostname "DOCTOR-PC";
}
lease 192.168.0.123 {
  starts 2 2010/11/02 15:50:06;
  ends 2 2010/11/02 15:52:06;
  tstp 2 2010/11/02 15:52:06;
  cltt 2 2010/11/02 15:50:06;
  binding state free;
:  client-hostname "COMMPH1";
}
lease 192.168.0.107 {
  starts 2 2010/11/02 10:52:10;
  ends 2 2010/11/02 16:52:10;
  tstp 2 2010/11/02 16:52:10;
  cltt 2 2010/11/02 10:52:10;
  binding state free;
  hardware ethernet 00:1b:24:0d:e5:7c;
  uid "\001\000\033$\015\345|";
}
lease 192.168.0.103 {
  starts 2 2010/11/02 17:28:54;
  ends 2 2010/11/02 17:30:54;
  tstp 2 2010/11/02 17:30:54;
  cltt 2 2010/11/02 17:28:54;
  binding state free;
  hardware ethernet 00:22:41:36:66:c5;
  uid "\001\000\"A6f\305";
}
lease 192.168.0.108 {
  starts 2 2010/11/02 12:30:51;
  ends 2 2010/11/02 18:30:51;
  tstp 2 2010/11/02 18:30:51;
  cltt 2 2010/11/02 12:30:51;
  binding state free;
  hardware ethernet 00:22:64:5c:cd:16;
  uid "\001\000\"d\\\315\026";
}
lease 192.168.0.113 {
  starts 2 2010/11/02 14:46:39;
  ends 2 2010/11/02 20:46:39;
  tstp 2 2010/11/02 20:46:39;
  cltt 2 2010/11/02 14:46:39;
  binding state free;
  hardware ethernet 00:e0:4c:77:2a:d9;
  uid "\001\000\340Lw*\331";
: uid "\001\000\340Lw*\331";
}
lease 192.168.0.122 {
  starts 2 2010/11/02 15:47:50;
  ends 2 2010/11/02 21:47:50;
  tstp 2 2010/11/02 21:47:50;
  cltt 2 2010/11/02 15:47:50;
  binding state free;
  hardware ethernet 00:26:9e:97:c1:28;
  uid "\001\000&\236\227\301(";
}
lease 192.168.0.125 {
  starts 4 2010/11/04 13:19:43;
  ends 4 2010/11/04 13:21:43;
  tstp 4 2010/11/04 13:21:43;
  cltt 4 2010/11/04 13:19:43;
  binding state free;
  hardware ethernet 00:30:67:49:13:dc;
  uid "\001\0000gI\023\334";
  client-hostname "fnh11";
}
lease 192.168.0.126 {
  starts 4 2010/11/04 13:22:58;
  ends 4 2010/11/04 13:24:58;
  tstp 4 2010/11/04 13:24:58;
  cltt 4 2010/11/04 13:22:58;
  binding state free;
  hardware ethernet 00:30:67:49:0d:80;
  uid "\001\0000gI\015\200";
  client-hostname "COMP3";
}
lease 192.168.0.124 {
  starts 4 2010/11/04 14:07:23;
  ends 4 2010/11/04 14:10:33;
  tstp 4 2010/11/04 14:10:33;
  cltt 4 2010/11/04 14:07:23;
  binding state free;
:lease 192.168.0.110 {
  starts 1 2010/11/08 08:53:34;
  ends 1 2010/11/08 14:53:34;
  tstp 1 2010/11/08 14:53:34;
  cltt 1 2010/11/08 08:53:34;
  binding state active;
  next binding state free;
  hardware ethernet a4:ba:db:94:b3:ca;
  client-hostname "ty-laptop";
}
lease 192.168.0.111 {
  starts 1 2010/11/08 08:55:29;
  ends 1 2010/11/08 14:55:29;
  tstp 1 2010/11/08 14:55:29;
  cltt 1 2010/11/08 08:55:29;
  binding state active;
  next binding state free;
  hardware ethernet 00:23:5a:9d:67:8c;
  uid "\001\000#Z\235g\214";
  client-hostname "IbrahimWaziriJr";
}
lease 192.168.0.127 {
  starts 1 2010/11/08 08:55:32;
  ends 1 2010/11/08 14:55:32;
  tstp 1 2010/11/08 14:55:32;
  cltt 1 2010/11/08 08:55:32;
  binding state active;
  next binding state free;
  hardware ethernet 00:30:67:49:15:23;
  uid "\001\0000gI\025#";
  client-hostname "COMP8";
}
lease 192.168.0.128 {
  starts 1 2010/11/08 08:55:35;
  ends 1 2010/11/08 14:55:35;
  tstp 1 2010/11/08 14:55:35;
  cltt 1 2010/11/08 08:55:35;
:
}
lease 192.168.0.128 {
  starts 1 2010/11/08 08:55:35;
  ends 1 2010/11/08 14:55:35;
  tstp 1 2010/11/08 14:55:35;
  cltt 1 2010/11/08 08:55:35;
  binding state active;
  next binding state free;
  hardware ethernet 00:03:0d:40:b8:48;
  uid "\001\000\003\015@\270H";
  client-hostname "zinox-4d43a2fc1";
}
lease 192.168.0.115 {
  starts 4 2010/11/04 13:38:17;
  ends never;
  tstp never;
  cltt 4 2010/11/04 13:38:17;
  binding state active;
  next binding state free;
  hardware ethernet 00:ab:00:00:00:00;
}
(END) 

```

---

### Post by nnamdi on 2010-11-08
```

ty@ty-laptop:~$ sudo /etc/init.d/dhcp3-server stop
[sudo] password for ty: 
 * Stopping DHCP server dhcpd3     [fail]        
ty@ty-laptop:~$   

ty@ty-laptop:~$ sudo update-rc.d dhcp3-server remove
update-rc.d: /etc/init.d/dhcp3-server exists during rc.d purge (use -f to force)
ty@ty-laptop:~$ sudo update-rc.d dhcp3-server remove -f
update-rc.d: /etc/init.d/dhcp3-server exists during rc.d purge (use -f to force)
ty@ty-laptop:~$ 
 
```

what do i do cos i had to revert my setting back to dhcp instead of static...

---

### Post by toekneewood on 2010-11-08
Can I just confirm that you are attempting to stop your Laptop from issuing IP to depktops.  If so then you need to stop the DHCP Server on your Laptop, as mentioned above.

For your Laptop you should have the following inside the "interfaces" file as your GUI Network manager will auto configure your Network adapter.
```

cat /etc/network/interfaces 
auto lo
iface lo inet loopback

```

If you want your adapter to have a static IP then this is an example:
```

sudo nano /etc/network/interfaces 

auto eth0
iface eth0 inet static
metric 10
address 10.1.32.33
netmask 255.255.255.0
network 10.1.32.0
broadcast 10.1.32.255
gateway 10.1.32.254

```

If you are attempting to configure the DHCP scope then you need to edit this:
```

sudo nano /etc/dhcp3/dhcpd.conf
# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;
 
# option definitions common to all supported networks...
option domain-name "home.lan";
option domain-name-servers ubuntu.home.lan;
 
default-lease-time 600;
max-lease-time 7200;
 
# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;
 
# This is a very basic subnet declaration.
subnet 10.10.10.0 netmask 255.255.255.0 {
  range 10.10.10.100 10.10.10.200;
  option routers router.home.lan;
}

```



If you want to use DHCP on a specific adapter:
```

sudo nano /etc/default/dhcp3-server
look for
INTERFACES=""
change to
INTERFACES="eth1"

```

---

### Post by nnamdi on 2010-11-08
ty@ty-laptop:~$ sudo update-rc.d dhcp3-server remove -f
update-rc.d: /etc/init.d/dhcp3-server exists during rc.d purge (use -f to force)
ty@ty-laptop:~$ sudo update-rc.d -f dhcp3-server remove 
 Removing any system startup links for /etc/init.d/dhcp3-server ...
   /etc/rc1.d/K40dhcp3-server
   /etc/rc2.d/S40dhcp3-server
   /etc/rc3.d/S40dhcp3-server
   /etc/rc4.d/S40dhcp3-server
   /etc/rc5.d/S40dhcp3-server
ty@ty-laptop:~$

---

### Post by toekneewood on 2010-11-08
By the looks of it your post "#8" has removed the DHCP Server from startup so that it will not auto start.  You should now be able to start it when you want to and so that it will not clash with work.

---

### Post by nnamdi on 2010-11-08
man thank you so much for your time... let me watch the network

---

