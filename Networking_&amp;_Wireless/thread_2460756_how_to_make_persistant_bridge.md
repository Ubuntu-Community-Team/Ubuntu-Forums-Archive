---
title: "how to make persistant bridge"
date: 2021-04-18
forum: Networking &amp; Wireless
---

### Post by fishbait on 2021-04-18
starting off i have a fresh 20.04 lts desktop install with nftables and bridge-utils installed

im trying to start off turning it into a router first (i'll add a wireless ap after) 
i know that to do that i need to 

1. establish a bridge (persistant across boots and ipv6 compatible)

2. add dhcp onto the bridge vis dnsmasq

3. check for ip being handed out

4. setup nftables ruleset(O_O im dreading this part a bit)

5. check if ip acess via ping and try to load a website

once the router bit is up i plan on adding squidproxy for cacheing and add in antivirus to it, samba and swat, and eventually a plex media server 

>_<; i remember doing all this a decade plus ago when i was little but everything's changed since then.

UPDATE: managed to convert from netplan back to ifconfig (i need a bridge that neither has a master nor shares its masters internet so that i can tie off lan services to that interface) 
to convert back from netplan to ifconfig i used
[start commands]

sudo su
apt install ifupdown && apt purge netplan.io
rm -rf /usr/share/netplan && rm-rf /etc/netplan
apt install net tools
reboot

[end commands]

okay so bunged up the switch a bit and lost network referring to [this guide]("https://linuxconfig.org/how-to-switch-back-networking-to-etc-network-interfaces-on-ubuntu-20-04-focal-fossa-linux") i set allow-hotplug for all my interfaces than made a special eth0 file under interfaces.d for the primary interface line aannd now we have network again!

made up the br0 bridge file
```

##static config for br0 bridge##

auto br0
iface br0 inet static[INDENT]address 10.0.0.1
netmask 255.255.255.0
[/INDENT]
[INDENT]bridge_stp off
[/INDENT]
[INDENT]bridge_ports enp5s0f1 enp6s0f0 enp6s0f1
[/INDENT]
iface br0 inet6 auto

allow-hotplug enp5s0f1
allow-hotplug enp6s0f0
allow-hotplug enp6s0f1



```

net.ipv4.ip_forward=1 line uncommented 
 in sysctl.conf

dnsmasq installed default config changes
```

domain-needed
bogus-priv

server=8.8.8.8
server=8.8.4.4

no-resolv

interface=br0

dhcp-range= 10.0.0.1,10.0.0.150,12h

dhcp-range=2605::2, 2605::500 slaac

dhcp-host=f4:92:bf:6c:94:73,10.0.0.5

```


UPDATE! I HAVE IP!!!!! YAASS :D

nftables ruleset 
```

#!/usr/sbin/nft -f

flush ruleset

define internal_nic = br0
define external_nic = enp5s0f0

table inet filter {
    chain input {
        type filter hook input priority 0;

        iifname lo accept

        ct state {established, related } accept

        ct state invalid drop

        iifname $internal_nic ip saddr 10.0.0.0/24 accept

        ip protocol icmp accept
        ip protocol igmp accept

        ip6 nexthdr icmpv6 accept
        icmpv6 type {echo-request,echo-reply,nd-neighbor-solicit,nd-neighbor-advert,nd-router-solicit,nd-router-advert} accept
        icmpv6 type {mld-listener-query, destination-unreachable, packet-too-big, time-exceeded, parameter-problem} accept

        ##amplifi ports##
        tcp dport 8080 accept
        udp dport 5353 accept
        udp dport 10001 accept
        tcp dport 53 accept
        udp dport 67 accept
        tcp dport 67 accept

        reject with icmp type port-unreachable
    }

    chain forward {
        type filter hook forward priority 0;

        iifname $external_nic oifname $internal_nic ct state {related, established } accept

        iifname $internal_nic oifname $external_nic accept

        drop
    }


}

table ip nat {
    chain prerouting {
        type nat hook prerouting priority 0
    }

    chain postrouting {
        type nat hook postrouting priority 100;

        oifname $external_nic masquerade
    }
}

#uncomment and run nft monitor trace to debug nftable rules
#table ip filter {
#    chain trace_chain {
#        type filter hook prerouting priority -301; policy accept;
#        nftrace set 1
#    }
#}

```


update 2: 2 days into this and i have ipv4 internet!. still want ipv6 though.

update day 3 unfortunately wifi has completely flopped over and refused to cooperate. and ipv6 refuses to go past eth0.

update day 4: changed to debian 10.9.0-amd64 same configuration files and setup problem persisted. . . 

update day 6: with much help from the experts in #Netfilter over on freenode, the wifi finally gets internet credit to @Thermi for the solution apparently 10.0.0.0 is the net identifier and having it as the bridge address had unintended consequences solution was to change 10.0.0.0 in br0 file to 10.0.0.1 (yes really -_- )

will update this post as i continue along this journey slowly figuring this sh*t out over 18+ years after i last bungled my way through this

---

### Post by fishbait on 2021-04-25
UPDATE!!!!!!! the solution was to change the br0 bridge static address from 10.0.0.0 to 10.0.0.1

---

### Post by fishbait on 2021-04-25
for future reference here a layout of the network as intended[ATTACH=CONFIG]288373[/ATTACH]

---

