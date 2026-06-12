---
title: "Softether VPN, dnsmasq and IPv6: Failing to get ipv6 gateway/forwarding"
date: 2015-11-23
forum: Networking &amp; Wireless
---

### Post by tehdartherer on 2015-11-23
I'm desperately trying to set up my VPN VPS to deliver also ipv6 along with the already working ipv4.
Unfortunately there seems to be a problem with the ipv6 forwarding and advertising the default gateway.

I'm trying to setup a private VPN server with internal services as well as ipv4/v6 forwarding to the open internet.
The internal net is accessible over 10.0.1.0/24 and my VPS has an assigned ipv6 block, e.g. 2001:aaaa:bbbb:cccc::/64, and a static ipv4, e.g. 101.101.101.101.
From the VPS I am able to ping ipv4 and ipv6 addresses.

eth0 has 101.101.101.101 and 2001:aaaa:bbbb:cccc::1 assigned.

The network is managed by the following software:
[LIST]
[*]Softether VPN server
[LIST]
[*]Bridged to a tap device 
[*]e.g. tap_vpn: 10.0.1.1 and 2001:aaaa:bbbb:cccc::2 
[/LIST]
  
[*]Dnsmasq
[LIST]
[*]Running on tap_vpn 
[*]ipv4 (dhcp): 10.0.1.10 - 10.0.1.200 
[*]ipv6: 2001:aaaa:bbbb:cccc::/64 
[/LIST]
  
[*]UFW
[LIST]
[*]Setup to allow traffic on tap_vpn and do ipv4 NAT to the outside ipv4 world 
[/LIST]
      
[/LIST]

I used [http://az.cokh.net/softether-vpn-server-on-a-nat-server/](http://az.cokh.net/softether-vpn-server-on-a-nat-server/) to get an idea of the configuration.
When I connect to the VPN server, I get a ipv4 and and two ipv6 addresses. For ipv4 I also get the gateway 10.0.1.1. Forwarding over ipv4 is working nicely, giving me the ipv4 of my VPS.

For ipv6 I get an ip and can ping other hosts on tap_vpn, i.e. all hosts with prefix 2001:aaaa:bbbb:cccc::/64. Except the eth0 interface 2001:aaaa:bbbb:cccc::1. So ipv6 forwarding doesn't seem to work.
I also don't get a gateway and can't ping other hosts, e.g. ipv6.google.com, from the clients. If I set the gateway manually to 2001:aaaa:bbbb:cccc::2 I still have no connection to the outside world.

If I disconnect and use my local ipv6 connection on the client, I can ping 2001:aaaa:bbbb:cccc::1 but no other hosts with prefix 2001:aaaa:bbbb:cccc::/64.

So I have one or two problems here:
[LIST=1]
[*]I don't get a ipv6 gateway from dnsmasq 
[*]ipv6 forwarding doesn't seem to work 
[/LIST]

So at the moment I'm trying to find out what I'm doing wrong. Since I'm new to ipv6, it is most probably that I misconfigured something. Also opening UFW for all traffic doesn't solve anything and there are no UFW blocking messages in the logs.

dnsmasq.conf
```

interface=tap_vpn
except-interface=eth0
listen-address=10.0.1.1
bind-interfaces

dhcp-range=tap_vpn,10.0.1.10,10.0.1.200,48h

dhcp-option=tap_vpn,3,10.0.1.1

dhcp-authoritative

enable-ra

expand-hosts

strict-order

dhcp-no-override

dhcp-range=2001:aaaa:bbbb:cccc::,constructor:tap_vpn,ra-names,ra-stateless,slaac,64,48h

proxy-dnssec

domain-needed

bogus-priv

stop-dns-rebind
rebind-localhost-ok

dns-forward-max=300

no-resolv
no-poll

dhcp-option=252,"\n"

server=10.0.1.1
server=8.8.4.4
server=8.8.8.8

server=2001:aaaa:bbbb:cccc::2
server=2620:0:ccd::2
server=2001:4860:4860::8844

dhcp-option=option:dns-server,10.0.1.1,8.8.4.4

dhcp-option=option6:dns-server,[2001:aaaa:bbbb:cccc::2],[2620:0:ccd::2]

cache-size=10000

neg-ttl=80000
local-ttl=3600

dhcp-option=23,64

dhcp-option=vendor:MSFT,2,1i

dhcp-option=47

log-async=5

log-dhcp
quiet-dhcp6

```
/etc/ufw/sysctl.conf
```

net/ipv4/ip_forward=1
net/ipv6/conf/default/forwarding=1
net/ipv6/conf/all/forwarding=1


net/ipv4/conf/default/rp_filter=0
net/ipv4/conf/all/rp_filter=1

net/ipv4/conf/default/accept_source_route=0
net/ipv4/conf/all/accept_source_route=0
net/ipv6/conf/default/accept_source_route=0
net/ipv6/conf/all/accept_source_route=0

net/ipv4/conf/default/accept_redirects=1
net/ipv4/conf/all/accept_redirects=1
net/ipv6/conf/default/accept_redirects=1
net/ipv6/conf/all/accept_redirects=1

net/ipv4/icmp_echo_ignore_broadcasts=1
net/ipv4/icmp_ignore_bogus_error_responses=1
net/ipv4/icmp_echo_ignore_all=0

net/ipv4/conf/default/log_martians=0
net/ipv4/conf/all/log_martians=0

net/ipv4/tcp_syncookies=0

net/ipv4/tcp_sack=1

net/ipv6/conf/tap_vpn/accept_ra=2
net/ipv6/conf/eth0/accept_ra=2
net/ipv6/conf/all/accept_ra=2
net/ipv6/conf/default/accept_ra=2

```
/etc/default/ufw
```

IPV6=yes

DEFAULT_INPUT_POLICY="DROP"

DEFAULT_OUTPUT_POLICY="ACCEPT"

DEFAULT_FORWARD_POLICY="ACCEPT"

DEFAULT_APPLICATION_POLICY="SKIP"

MANAGE_BUILTINS=no

IPT_SYSCTL=/etc/ufw/sysctl.conf

IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_netbios_ns"

```
ifconfig
```

eth0      Link encap:Ethernet  HWaddr XXX
          inet addr:101.101.101.101  Bcast:XXX  Mask:255.255.254.0
          inet6 addr: 2001:aaaa:bbbb:cccc::1/64 Scope:Global
          inet6 addr: fe80::1111:2222:3333:4444/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89003 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:28551068 (28.5 MB)  TX bytes:26588370 (26.5 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:533 errors:0 dropped:0 overruns:0 frame:0
          TX packets:533 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:54173 (54.1 KB)  TX bytes:54173 (54.1 KB)

tap_bridge Link encap:Ethernet  HWaddr XXX
          inet addr:10.0.1.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: 2001:aaaa:bbbb:cccc::2/64 Scope:Global
          inet6 addr: fe80::2222:3333:4444:5555/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:2882860 (2.8 MB)  TX bytes:7562718 (7.5 MB)

```
ip -6 route show
```

2001:aaaa:bbbb:cccc::/64 dev eth0  proto kernel  metric 256
2001:aaaa:bbbb:cccc::/64 dev tap_vpn  proto kernel  metric 256
fe80::/64 dev eth0  proto kernel  metric 256
fe80::/64 dev tap_vpn  proto kernel  metric 256
default via fe80::1111:2222:3333:4444 dev eth0  proto ra  metric 1024  expires 1682sec hoplimit 64

```
ip -4 route show
```

default via 101.101.101.1 dev eth0
10.0.0.0/8 dev tap_vpn  proto kernel  scope link  src 10.0.1.1
101.101.101.0/23 dev eth0  proto kernel  scope link  src 101.101.101.101
101.102.0.0/16 dev eth0  scope link

```

I'm trying know for serveral days to get this up and running, but until now I had no luck. I appreciate any hint! :)

---

