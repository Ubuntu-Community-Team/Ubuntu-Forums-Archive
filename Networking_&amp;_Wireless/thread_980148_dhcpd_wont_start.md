---
title: "dhcpd wont start"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by p3t3 on 2008-11-12
Hello :)

I am having a few problems configuring my hardy pc as a dhcp server.

I have an internet connection through my halls at uni configured and running eth0.

I installed a new network card into the machine and ubuntu picked it up straight away and its called eth2. (what happened to eth1?)

Following a guide i found on the internet

i ran this command... 

```
sudo apt-get install dhcp3-server
```

and the dhcp server was installed.

i then configured...

/etc/default/dhcp3-server

...so interface is run on "eth2"

then i changed the /etc/dhcp3/dhcpd.conf

to look like this...

```
#naming the server
# and enabling ddns
server-identifier router;
authoritative;

ddns-update-style interim;

include "/etc/bind/rndc.key";

# Use what key in what zone
zone lan.debuntu.local. {
  primary 127.0.0.1;
  key "rndc-key";
}

#Standard DHCP info
option domain-name "lan.debuntu.local";
option domain-name-servers ns.lan.debuntu.org;

default-lease-time 600;
max-lease-time 7200;

log-facility local7;

subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.5 192.168.2.200;
  option routers  router.lan.debuntu.local;
  zone    2.168.192.in-addr.arpa. {
    primary ns.lan.debuntu.local;
    key             "rndc-key";
  }
  zone    lan.debuntu.local. {
    primary ns.lan.debuntu.local;
    key             "rndc-key";
  }
}

```

but when i try to start/restart the dhcpd service i get this error message... 

```
pete@PeteDesktop:~$ sudo /etc/init.d/dhcp3-server start
dhcpd self-test failed. Please fix the config file.
The error was: 
Can't open /etc/bind/rndc.key: No such file or directory

```


What does it mean? Where can i get a rndc.key? 


if this helps here is my ifconfig

```
pete@PeteDesktop:/etc/dhcp3$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:8b:7e:5c:03  
          inet addr:10.0.1.131  Bcast:10.0.7.255  Mask:255.255.248.0
          inet6 addr: fe80::218:8bff:fe7e:5c03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8821 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9282936 (8.8 MB)  TX bytes:1241570 (1.1 MB)
          Interrupt:21 

eth2      Link encap:Ethernet  HWaddr 00:06:4f:77:43:98  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::206:4fff:fe77:4398/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34110 (33.3 KB)  TX bytes:70142 (68.4 KB)
          Interrupt:20 Base address:0x9c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:133447 (130.3 KB)  TX bytes:133447 (130.3 KB)

```


Hope you can help

Thank you

Pete

---

### Post by cariboo on 2008-11-12
Run:

```
sudo rndc-confgen
```

to generae a mdc key. See here:

[http://linux.die.net/man/8/rndc-confgen](http://linux.die.net/man/8/rndc-confgen)

Jim

---

### Post by p3t3 on 2008-11-12
Thanks for your help :)

What is an rndc.key? Do i need one? none of the guides say anything about creating one.

After changing the dhcpd.conf file, it isnt asking for one anymore.

How do i need to configure the eth2 (internal) NIC, do i need to give it a static IP? 

Your help is very much appreciated :)

---

### Post by p3t3 on 2008-11-12
I am pretty sure my problem is with my dhcpd.conf file.

How should it look?

Do i need to assign a static IP to my eth2 NIC?

Thanks :)

---

### Post by p3t3 on 2008-11-12
Bump.

---

### Post by Iowan on 2008-11-12
You needn't bump your post every half hour - once/day is considered plenty. It's usually easier to have a static address for the DHCP server.  My version did not have **rndc** - nor does it add .local. In fact, I'll try to get a copy posted for you (although it IS an older version - much older).

---

### Post by p3t3 on 2008-11-12
It worked thank you very much :)

---

