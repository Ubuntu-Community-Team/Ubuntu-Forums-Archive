---
title: "dhcp3-server problems"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by juzt3r on 2008-10-16
I have a project at school, where i am supposed to set up a dhcp-server on a ubuntu-machine. The problem is the computer is connected to the student network, so if the dhcp-server starts to give out ip's from eth0 problems can occure.

```

root@Gruppe1Server:/etc/dhcp3# /etc/init.d/dhcp3-server start
dhcpd self-test failed. Please fix the config file.
The error was: 
/etc/dhcp3/dhcpd.conf line 24: expecting a declaration
# option definitions common to all supported networks...
^
Configuration file errors encountered -- exiting

```


here is the dhcpd.conf
```

option domain-name "hiof.no";
option domain-name-servers trond01.hiof.no, trond02.hiof.no;
option routers                  192.168.1.1;

default-lease-time 600;
max-lease-time 7200;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# This is a very basic subnet declaration.

subnet 192.168.1.0 netmask 255.255.255.0 {
   range 192.168.1.10 192.168.1.250;
        option broadcast-address 192.168.1.255;
}



# This entry ignores requests on eth0...
subnet 158.39.162.0 netmask 255.255.254.0 {
        not authoritative;
}

# option definitions common to all supported networks...
/etc/router.sh

```


Here is the:
/etc/router.sh

```

#!/bin/bash

echo "Routing starter..."

# Enabler modul for passive ftp-connections
modprobe ip_nat_ftp

######################################################################
# Setter først noen parametere som gjør det enkelt å forandre
# på skriptet senere med tanke på ip-adresser, regelsett, osv.
######################################################################
IPT="/sbin/iptables"
LOOP_INTERFACE="lo"
EXT_IP="158.39.163.23"
INT_IP="192.168.1.1"
INT_NET="192.168.1.0/24"
INT_NET_BROADCAST="192.168.1.255"
BROADCAST="255.255.255.255"
ANYWHERE="any/0"
HIGHPORTS="1024:65535"

######################################################################
# Flusher (sletter) eksisterende regler
######################################################################
$IPT -F INPUT
$IPT -F FORWARD
$IPT -F OUTPUT
$IPT -F -t nat

######################################################################
# Setter policy til ACCEPT for all trafikk
######################################################################
$IPT -P INPUT ACCEPT
$IPT -P OUTPUT ACCEPT
$IPT -P FORWARD ACCEPT

######################################################################
# Tillater all trafikk for loopback-interfacet
######################################################################
$IPT -I INPUT 1 -i lo -j ACCEPT
$IPT -I OUTPUT 1 -o lo -j ACCEPT
######################################################################

#Enabler IP-forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

#  Standard Masquerade (skjuler lokalnettet bak brannmuren)
$IPT -t nat -A POSTROUTING -o eth0 -j MASQUERADE

echo "Routing startet..."

```

ifconfig
```


eth0      Link encap:Ethernet  HWaddr 00:0d:56:0a:3a:6b  
          inet addr:158.39.163.23  Bcast:158.39.163.255  Mask:255.255.254.0
          inet6 addr: 2001:700:a00:ff80:20d:56ff:fe0a:3a6b/64 Scope:Global
          inet6 addr: fe80::20d:56ff:fe0a:3a6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9921 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:15759899 (15.0 MB)  TX bytes:1567357 (1.4 MB)
          Base address:0xdf40 Memory:fe8e0000-fe900000 

eth1      Link encap:Ethernet  HWaddr 00:02:b3:08:6b:36  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:b3ff:fe08:6b36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:72203 (70.5 KB)  TX bytes:28304 (27.6 KB)


```
/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
	address 	192.168.1.1
	netmask 	255.255.255.0
	broadcast 	192.168.1.255
	network 	192.168.1.0

iface eth0 inet dhcp

auto eth0

```


Can anyone see what the problem is in the dhcpd.conf ?

---

### Post by Iowan on 2008-10-16
From the looks of the error message, it didn't like this line/section:```
# option definitions common to all supported networks...
/etc/router.sh
```

---

