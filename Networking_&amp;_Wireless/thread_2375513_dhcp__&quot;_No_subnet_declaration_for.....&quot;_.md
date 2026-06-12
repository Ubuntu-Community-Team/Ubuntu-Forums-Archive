---
title: "dhcp : &quot; No subnet declaration for.....&quot; probem"
date: 2017-10-25
forum: Networking &amp; Wireless
---

### Post by habernir on 2017-10-25
hi all i try config dhcp server but every time i got "Active: failed" and after "journalctl" command it write me 

```
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: No subnet declaration for enp8s0f1 (no IPv4 addresses).&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: ** Ignoring requests on enp8s0f1.  If this is not what
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]:    you want, please write a subnet declaration
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]:    in your dhcpd.conf file for the network segment
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]:    to which interface enp8s0f1 is attached. **
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: 
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: 
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: No subnet declaration for enp8s0f0 (192.168.2.1).
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: ** Ignoring requests on enp8s0f0.  If this is not what
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]:    you want, please write a subnet declaration
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]:    in your dhcpd.conf file for the network segment
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]:    to which interface enp8s0f0 is attached. **
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: 
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: 
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: Not configured to listen on any interfaces!
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: 
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: If you think you have received this message due to a bug rather
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: than a configuration issue please read the section on submitting
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: bugs on either our web page at www.isc.org or in the README file
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: before submitting a bug.  These pages explain the proper
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: process and the information we find helpful for debugging..
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: 
&#1488;&#1493;&#1511; 25 08:48:00 nirUbuntu dhcpd[7944]: exiting.



```

i'm using ubuntu 16.04

and i i have 3 network card

1) enp3s0 : (connected to the internet and the the ip its 192.168.1.101 and mask 255.255.255.0

and thhe other two that i want to add them to the dhcp server are 

2) enp8s0f0: i manually config it to ip 192.168.2.1 and mask 255.255.255.0

2) enp8s0f1: i manually config it to ip 192.168.3.1 and mask 255.255.255.0

this is the ifconfig

```
enp3s0    Link encap:Ethernet  HWaddr 40:8d:5c:bd:7b:fb            inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a6f7:c65d:33eb:d5bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:577656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:999368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:120050899 (120.0 MB)  TX bytes:1446428221 (1.4 GB)
          Interrupt:18 


enp8s0f0  Link encap:Ethernet  HWaddr a0:36:9f:87:f3:be  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::56f1:e36:44d4:e93b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:361493 (361.4 KB)  TX bytes:234216 (234.2 KB)
          Memory:ef200000-ef2fffff 


enp8s0f1  Link encap:Ethernet  HWaddr a0:36:9f:87:f3:bf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:ef100000-ef1fffff 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:24724 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:4906368 (4.9 MB)  TX bytes:4906368 (4.9 MB)


vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.62.1  Bcast:192.168.62.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.37.1  Bcast:192.168.37.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1395 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


habernir@nirUbuntu:~$ sudo gedit /etc/dhcp/dhcpd.conf



```




and this is the /etc/dhcp/dhcpd.conf
```


ddns-update-style none;


default-lease-time 600;
max-lease-time 7200;


authoritative;


log-facility local7;


subnet 192.168.2.0 netmask 255.255.255.0 {
 option routers 192.168.2.1;
 option subnet-mask 255.255.255.0;
 range 192.168.2.20 192.168.2.30;
 }


subnet 192.168.3.0 netmask 255.255.255.0 {
   option routers 192.168.3.1;
   option subnet-mask 255.255.255.0;
   range 192.168.3.10 192.168.3.100;
}



```

and this is /etc/default/isc-dhcp-server

```
# Defaults for isc-dhcp-server initscript# sourced by /etc/init.d/isc-dhcp-server
# installed at /etc/default/isc-dhcp-server by the maintainer scripts


#
# This is a POSIX shell fragment
#


# Path to dhcpd's config file (default: /etc/dhcp/dhcpd.conf).
#DHCPD_CONF=/etc/dhcp/dhcpd.conf


# Path to dhcpd's PID file (default: /var/run/dhcpd.pid).
#DHCPD_PID=/var/run/dhcpd.pid


# Additional options to start dhcpd with.
#    Don't use options -cf or -pf here; use DHCPD_CONF/ DHCPD_PID instead
#OPTIONS=""


# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="enp8s0f0 enp8s0f1"
```

anyone can help me please?

thanks a head , nir.

---

### Post by habernir on 2017-10-27
anyone know whats the problem?

---

### Post by Doug S on 2017-10-27
> **habernir said:**
> anyone know whats the problem?I did look at your question when it first came out, but didn't see anything wrong with your setup, at least for enp8s0f0. Since enp8s0f1 doesn't seem to start up properly (doesn't have an IP address), I would suggest to start there. Once you get enp8s0f1 working, then move on to the dhcp server issues.

---

### Post by SeijiSensei on 2017-10-27
Let's start with just enp8s0f0 and see if it works for that subnet.  Remove anything from the configurations that reference enp8s0f1 and see if that works.

I've never configured a server to answer on two different interfaces with two different subnets, and I'm not sure it can be done.  DHCP works by listening for broadcasts on an interface and returning an address to the broadcasting machine.  I just skimmed "[man dhcpd.conf](https://linux.die.net/man/5/dhcpd.conf)," and I don't see anything about how to have dhcpd answer with addresses in different subnets by interface. Maybe I was just blind.

---

### Post by Doug S on 2017-10-28
> **SeijiSensei said:**
> I've never configured a server to answer on two different interfaces with two different subnetsNeither have I, but I saw [this]("https://askubuntu.com/questions/956457/how-do-i-set-up-an-ubuntu-server-to-be-the-router-for-two-private-networks-on-my") recently.

---

### Post by collisionystm on 2017-10-28
I am using 16.04 server as my firewall/router/dns/dhcp. I have 2 physical NIC's with multiple virtual adapters on vlan's. I run a single isc-dhcp-server instance.

Here is my configuration so you can compare it to yours. I've removed some of the configuration that included custom dhcp options and static host entries.

Confirm that you have your network interfaces declared properly and check your dhcpd.conf for whitespaces - there should be no whitespaces following the semicolons at the end of each statement.


/etc/network/interfaces

```
# LAN
auto enp30s0
iface enp30s0 inet static
        address 192.168.1.1
        netmask 255.255.255.0


# WAN
auto enp48s0
iface enp48s0 inet dhcp




# VOIP
auto enp30s0.40
iface enp30s0.40 inet static
        address 10.10.40.1
        netmask 255.255.255.0
        broadcast 10.10.40.255
        vlan-raw-device enp30s0


# TESTING
auto enp30s0.50
iface enp30s0.50 inet static
        address 10.10.50.1
        netmask 255.255.255.0
        broadcast 10.10.50.255
        vlan-raw-device enp30s0



```


/etc/dhcp/dhcpd.conf

```
authoritative;
log-facility local7;
deny duplicates;




# Test Network
  subnet 10.10.50.0 netmask 255.255.255.0 {
  range 10.10.50.150 10.10.50.200;
  option domain-name-servers 10.10.50.1;
  option domain-name "testnet.local";
  option subnet-mask 255.255.255.0;
  option routers 10.10.50.1;
  option netbios-node-type 1;
  option broadcast-address 10.10.50.255;
  default-lease-time 28800;
  max-lease-time 28800;
}


# Phone Network
  subnet 10.10.40.0 netmask 255.255.255.0 {
  range 10.10.40.150 10.10.40.160;
  option domain-name-servers 10.10.40.1;
  option domain-name "voip.local";
  option subnet-mask 255.255.255.0;
  option routers 10.10.40.1;
  option broadcast-address 10.10.40.255;
  default-lease-time 28800;
  max-lease-time 28800;
}


# LXC Network
  subnet 10.10.30.0 netmask 255.255.255.0 {
  range 10.10.30.100 10.10.30.150;
  option domain-name-servers 10.10.30.1;
  option domain-name "lxc.local";
  option subnet-mask 255.255.255.0;
  option routers 10.10.30.1;
  option broadcast-address 10.10.30.255;
  default-lease-time 28800;
  max-lease-time 28800;
}

# LAN
  subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.150 192.168.1.200;
  option domain-name-servers 192.168.1.1;
  option domain-name "batcave.local";
  option subnet-mask 255.255.255.0;
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
  option netbios-node-type 1;
  default-lease-time 28800;
  max-lease-time 28800;
}


```

---

### Post by habernir on 2017-10-28
well i solve it 
i have to change /etc/ltsp/dhcpd.conf 
soo thanks a lot everyone

---

