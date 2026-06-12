---
title: "Home Router - cannot ping local machines by name, HELP"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by berbs on 2008-01-02
I know this is a topic that has been discussed over and over, but I still can't figure out what is wrong with my setup and I have been trying several configurations without any success.  Overall I can use my setup for internet browsing from all machines, but pinging by name doesn't work. 

Hopefully someone can spend a few minutes and review my configuration, maybe something is obvious.

I set up a home router running Gutsy server. Here is a representation of my network:

```

                                 | ---- eth1 ---- linksys wireless router --> laptop(s)
                                 |                dhcp/192.168.3.1            dhcp
internet <-- eth0 ------ br0 ----|
             dhcp    192.168.1.1 |
                                 | ---- eth2 ---- imac
                                                  dhcp

```

The router has three interfaces:
[LIST]
[*]eth0 is connected to the cable modem.
[*]eth1 is connected to a linksys wireless router. the router has an internal address of 192.168.3.1 and serves some laptops over dhcp.
[*]eth2 is connected to an imac.
[*]br0 bridges the two internal interfaces (eth1 and eth2)
[/LIST]

[B]The problems:
[/B]

[LIST]
[*] Why CAN'T I ping  directly connected machines by name (imac)???
[*] How can I get rid of this message each time I start the bind server: "Failure registering capabilities with primary security module."
[*] Is it possible to ping the laptops that are wireless connected to the linksys router
[/LIST]

I have installed dhcpd3, bind9 and shorewall, my router is called gecko and the internal lan is called "home.lan". The server provides addresses in the range 192.168.1.200 to 249. Here is the detailed configuration:

**/etc/dhcpd.conf**

```

authoritative;

ddns-update-style                       interim;
ddns-updates                            on;
deny    client-updates;
#allow  unknown-clients;
do-forward-updates                      on;

default-lease-time                      600; #604800;
max-lease-time                          600; #720000;

option domain-name                      "home.lan";
option domain-name-servers      192.168.1.1;

ddns-domainname             "home.lan";
ddns-rev-domainname         "in-addr.arpa.";
server-name                 "gecko.home.lan";

include "/etc/dhcp3/rndc.key";

zone    1.168.192.in-addr.arpa. {
        primary                         127.0.0.1;
        key                             "rndc-key";
}

zone    home.lan. {
        primary                         127.0.0.1;
        key                             "rndc-key";
}

subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.200 192.168.1.249;
    option subnet-mask          255.255.255.0;
    option broadcast-address    192.168.1.255;
    option routers              192.168.1.1;
}

```

**/etc/dhclient.conf**

```

interface "eth0" {
    supersede domain-name "home.lan";
    supersede domain-name-servers 192.168.1.1;
}
```

**/etc/resolv.conf**

```

search home.lan
nameserver 192.168.1.1
```

**/etc/hosts**

```

127.0.0.1       localhost
127.0.1.1       gecko.home.lan  gecko
...
```

***DNS Server***

[B]/etc/bind/named.conf.local
[/B]

```

include "/etc/bind/rndc.key";

zone "home.lan" {
    type master;
    file "/etc/bind/zones/db.home.lan";
    allow-update { key "rndc-key"; };
    notify no;
};
zone "1.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/zones/db.1.168.192";
    allow-update { key "rndc-key"; };
    notify no;
};
```


**/etc/bind/named.conf.options**

```

options {
        directory "/var/cache/bind";

        forwarders {
                68.87.76.178;
                68.87.78.130;
        };
        allow-transfer { none; };
        allow-recursion { localnets; };
        listen-on-v6 { none; };
};
```

**/etc/bind/zones/db.home.lan**

```

$TTL 3D
@ IN SOA gecko.home.lan. admin.home.lan. (
   2007062001
   28800
   3600
   604800
   38400
);
home.lan.  IN      NS         gecko.home.lan.
gecko      IN      A          192.168.1.1
```


**/etc/bind/zones/db.1.168.192**

```

$TTL 3D
@   IN  SOA     gecko.home.lan. admin.home.lan. (
                2007062001
                28800
                604800
                604800
                86400
)
        IN      NS      gecko.home.lan.
1       IN      PTR     home.lan.
```

Here is the list of rules for the firewall, the rest of the configuration is pretty standard.

**/etc/shorewall/rules**

```

#
#       Accept DNS connections from the firewall to the network
#
DNS/ACCEPT      $FW             net
DNS/ACCEPT      loc             $FW
#
#       Accept SSH connections from the local network for administration
#
SSH/ACCEPT      loc             $FW
SSH/ACCEPT      net             $FW
#
#       Allow Ping from the local network
#
Ping/ACCEPT     loc             $FW

#
# Reject Ping from the "bad" net zone.. and prevent your log from being flooded..

Ping/REJECT     net             $FW
ACCEPT          $FW             loc             icmp
ACCEPT          $FW             net             icmp

# Allow internal access to samba directory

SMB/ACCEPT      loc             $FW

#
ACCEPT          $FW             loc             udp             67,68
ACCEPT          loc             $FW             udp             67,68
#
```

---

### Post by berbs on 2008-01-02
bump :-)

---

### Post by dannyboy79 on 2008-01-02
how does your wifi router get an ip 192.168.3.1 if your gutsy server hands out addresses from 192.168.1.foo? I don't use a dns server, I just use static ip's and hosts file for my little lan. I have 1 windows machine and 2 ubuntu computers and 2 xbox's on it.

Also, I don't really understand your illustration? So, does your gutsy box have 3 ethernet cards? eth0, eth1, eth2? I-net comes into eth0, eth1 connects to your wifi router which is also a DHCP server? Shouldn't there only be one dhcp server? Also, are they on the same subnet? laptops on a network of 192.168.3.1 wouldn't be able to ping machines on a network of 192.168.1.1 would it? Why are you bridging a connection, is that so you don't have to get a switch for the imac?

I am not the one to really help you, I am merely asking some questions in hopes that it'll maybe make you see what you're doing wrong. Do you have iptables rules setup?

---

### Post by berbs on 2008-01-02
> 
how does your wifi router get an ip 192.168.3.1 if your gutsy server hands out addresses from 192.168.1.


The linksys router gets its external address through DHCP (ex: 192.168.1.2490). The linksys router has an internal address of 192.168.3.1 and it allocates through DHCP in the range 192.168.3.30 through 50.

> I don't use a dns server, I just use static ip's and hosts file for my little lan. I have 1 windows machine and 2 ubuntu computers and 2 xbox's on it.

I would rather use DHCP since I have 3 laptops that are used in different environment and using DHCP removes the need to deal with different network configurations depending on  location.

> Also, I don't really understand your illustration? So, does your gutsy box have 3 ethernet cards? eth0, eth1, eth2? I-net comes into eth0, eth1 connects to your wifi router which is also a DHCP server? Shouldn't there only be one dhcp server? Also, are they on the same subnet? laptops on a network of 192.168.3.1 wouldn't be able to ping machines on a network of 192.168.1.1 would it? Why are you bridging a connection, is that so you don't have to get a switch for the imac?


I happened to have a wireless router, not a switch. I used to have this linksys router serve my network, but I added the linux box instead. I am wondering is there is some masquerading rules required to enable pinging from one network to the next. 

The main issue though is the fact that I can't even ping by name machines that are directly connected into the linux router.

> I am not the one to really help you, I am merely asking some questions in hopes that it'll maybe make you see what you're doing wrong. Do you have iptables rules setup?


I have enabled IP forwarding in the kernel. I am using shorewall as the firewall, all traffic is blocked by default and enabled through the rules included in the post. the local interface is br0 (bridge eth1 and eth2). 

Hope this clarifies.

---

### Post by dannyboy79 on 2008-01-02
well something doesn't seem correct with you using a wifi router where it's own ip is 192.168.3.1 when you're connecting it to a dhcp server that's giving out ip's in the range of 192.168.1.1? did you turn the dhcp server off within in the wifi router? you actually probably want to turn off dhcp and spi and nat on the router if you can. Also, I would suggets checking out a guide on setting up a dns server. If you're saying that your imac can't even ping the gutsy router by name that that would mean to me that dns isn't working. Are you saying that you have internet access at each of the machines? Also, can't you change the ip of the wifi router?

---

### Post by berbs on 2008-01-02
DNS is working on the main router (mostly). I tried 'dig' and I can see a performance improvement when looking up external addresses.  To answer your other comment, any router will have an external and internal interface. it decides which subnet to use for internal clients, hence the 192.168.3.x range. It's external address is provided by the linux router and is 192.168.1.249. Even if I was to use the same subnet for the linksys router, there would need to be some address translation to go between subnets allocated between the two routers (or so I think).

This is a lower priority for me to fix though, I will most likely buy a cheap wireless switch. I am more concerned about the situation where the linksys router is not involved and clients are directly connected to the linux router. Why can't I ping them by name, is something wrong with my setup (most likely)?

---

### Post by dannyboy79 on 2008-01-02
if you're not even worrying about the wifi computers being able to ping the router, than first turn off your shorewall firewall to see if that's blocking the pings. then with the shorewall firewall off you can rule that out. I haven't set up a dns server so I am totally sure. what guide did you use to set up the dns server? maybe check out another guide to see where you may  have misconfigured something. good luck. I am sorry I couldn't be of more help.

---

### Post by berbs on 2008-01-02
I did try with the firewall not running (shorewall clear)... same result.  Hopefully someone can take a look at the config files and point me in the right direction. Thanks for the help.

---

