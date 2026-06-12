---
title: "Routing stops working after a few minutes (DHCP server + static + dhclient)"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by dahlberg on 2007-09-15
I'm trying to get my network set up and by now I've been at it for a couple of days. Sure, I've learnt a lot but I'm starting to get a bit tired of it and would really appreciate some help! 

The network
1. ADSL modem
2. Computer with Ubuntu. DHCP lease from 1 on eth1. Serving 3 on eth0 and 4 on eth3.
3. Computer with windows. Connected to 2 with a static IP of 192.168.20.2
4. FON router (la fonera) Requires a DHCP server running on 2.

/etc/network/interfaces
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.20.1
netmask 255.255.255.0

auto eth1
iface eth1 inet dhcp

auto eth3
iface eth3 inet static
address 192.168.30.1
netmask 255.255.255.0

```

dhcpd.conf
```
ddns-update-style none;

# No service will be given on this subnet, but declaring it helps the
# DHCP server to understand the network topology.
subnet 192.168.20.0 netmask 255.255.255.0 {
}
subnet 85.0.0.0 netmask 255.0.0.0 {
}

subnet 192.168.30.0 netmask 255.255.255.0 {
  range 192.168.30.10 192.168.30.22;
  option domain-name-servers 195.54.122.198, 81.26.227.3;
  option routers 192.168.30.1;
  option ip-forwarding off;
  option broadcast-address 192.168.30.255;
  default-lease-time 600;
  max-lease-time 7200;
}

```

dhclient.conf
```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;

timeout 30;

lease {
  interface "eth1";
}

```

Restarting network with this
```
/etc/init.d/networking restart
/etc/init.d/dhcp3-server restart

```
I'm also running this to make sure that it's not causing any trouble:
```
dhclient3 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases eth1
```

Everything is well for a while and num 3 can access the net through num 2. I'm not sure about num 4 yet since I don't have a wlan client I'm sure is working right now. 

```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.20.0    *               255.255.255.0   U     0      0        0 eth0
192.168.30.0    *               255.255.255.0   U     0      0        0 eth3
85.229.64.0     *               255.255.240.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         ua-85-229-64-1. 0.0.0.0         UG    0      0        0 eth1

$ ps -ef | grep dhc
root      5781     1  0 Sep12 ?        00:00:01 /usr/sbin/dhcdbd --system
dhcpd    10791     1  0 17:34 ?        00:00:00 /usr/sbin/dhcpd3 -q eth3 -pf /var/run/dhcp3-server/dhcpd.pid -cf /etc/dhcp3/dhcpd.conf
dhcp     10830     1  0 17:34 ?        00:00:00 dhclient3 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases eth1
pmd      10833 28639  0 17:35 pts/12   00:00:00 grep dhc
dhcp     17668     1  0 16:32 ?        00:00:00 dhclient

```
Then after a while when I guess the dhclient is trying something the default 192.168.30.1 is added and the routing no longer works.

```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.20.0    *               255.255.255.0   U     0      0        0 eth0
192.168.30.0    *               255.255.255.0   U     0      0        0 eth3
85.229.64.0     *               255.255.240.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.30.1    0.0.0.0         UG    0      0        0 eth3
default         ua-85-229-64-1. 0.0.0.0         UG    0      0        0 eth1

$ ps -ef | grep dhc
root      5781     1  0 Sep12 ?        00:00:01 /usr/sbin/dhcdbd --system
dhcpd    10791     1  0 17:34 ?        00:00:00 /usr/sbin/dhcpd3 -q eth3 -pf /var/run/dhcp3-server/dhcpd.pid -cf /etc/dhcp3/dhcpd.conf
dhcp     10830     1  0 17:34 ?        00:00:00 dhclient3 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases eth1
pmd      10973 28639  0 17:41 pts/12   00:00:00 grep dhc
dhcp     17668     1  0 16:32 ?        00:00:00 dhclient

```

---

### Post by whistl on 2007-09-15
Your problem appears to be twofold.  Your dhcp server is listening on your WAN port, and you are running two dhclient processes.

You don't need to manually run dhclient3.  ifup will automatically run dhclient on any interface configured type "dhcp" in /etc/network/inferfaces.  Run "sudo ifdown eth1", "sudo killall -r dhclient" and "sudo ifup eth1".  "ps -ef | grep dhclient" should only show one process running.

Configure your dhcp daemon to only listen on eth3 by running "sudo vi /etc/default/dhcp3-server" and modifying the last line to be

INTERFACES="eth3"

Then run "sudo /etc/init.d/dhcp3-server restart"

That should take care of your problem.

---

### Post by dahlberg on 2007-09-16
Working like a charm. Thank you very much! :)

---

