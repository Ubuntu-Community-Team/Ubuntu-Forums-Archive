---
title: "UFW/iptables HTTP Working but HTTPS Isn't on Transparent Proxy Box"
date: 2013-09-28
forum: Networking &amp; Wireless
---

### Post by temp1029 on 2013-09-28
I am trying to setup a transparent proxy (using squid3) for my home network.  Currently I have this setup:

LAN PCs -> Switch -> Proxy Server -> Router -> Modem -> Internet

The proxy server has two NIC card.  eth0 (192.168.1.x) connects to the router and gets an IP address from the router's DHCP.  eth1 (192.168.0.1) is running DHCP.  This is defined in the interfaces file in the following way.

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.0.1
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255
```

Based on various tutorials I have found I used the following iptables rules to route requests from the PCs through the proxy server, catching port 80 requests and pushing them through squid.

```
-P FORWARD ACCEPT
-t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination 192.168.0.1:8128
-t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8128
-t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

I also have the following UFW rules in place (notice the fourth rule which, I believe, should allow all local traffic to proceed to anywhere).

```
To                         Action      From
--                         ------      ----
80/tcp                   ALLOW       192.168.0.0/24
53/udp                   ALLOW       192.168.0.0/24
8128/tcp                ALLOW       192.168.0.0/24
Anywhere               ALLOW       192.168.0.0/24
443/tcp                 ALLOW       192.168.0.0/24
```

In this setup I have no issues, I am able to access the internet (via http and https) and squid does its thing without a problem.

Where I am running into an issue is when I take the router out of the mix and hook the proxy server directly up to the modem.  All port http requests still work, but https requests fail.  I look in the UFW logs and get the following.

```

Sep 28 20:22:26 Server-1 kernel: [ 1312.081464] [UFW BLOCK] IN=eth0 OUT=eth1 MAC=a0:b3:cc:e4:ec:07:00:23:69:40:bf:f8:08:00 SRC=173.194.76.125 DST=192.168.0.11 LEN=52 TOS=0x00 PREC=0x20 TTL=46 ID=2939 PROTO=TCP SPT=443 DPT=60848 WINDOW=1002 RES=0x00 ACK URGP=0
Sep 28 20:23:14 Server-1 kernel: [ 1359.963552] [UFW BLOCK] IN=eth1 OUT=eth0 MAC=68:05:ca:1a:ce:46:9c:eb:e8:0c:ca:00:08:00 SRC=192.168.0.11 DST=74.125.228.73 LEN=41 TOS=0x00 PREC=0x00 TTL=127 ID=6156 DF PROTO=TCP SPT=60849 DPT=443 WINDOW=256 RES=0x00 ACK URGP=0

```

I have no idea what could be causing this.  I think the problem is with the iptables rules pushing port 80 to squid (or lack of similar pass through rule for port 443), but I can't figure out how to fix it (or what rules to add to allow it to go through).  I have tried skipping proxying altogether (making the server just act like an internet gateway) but to no avail.  Even totally turning off UFW doesn't help, https still won't work.

Any help would be appreciated and if there is any other information I can provide I will.

Stephen

---

### Post by 7182818 on 2013-09-29
It seems likely that NAT isn't working, although from the information you posted it seems like everything should be correct.  You can verify this by running tcpdump on eth0 to see whether the packets leaving the machine have the correct source IP address.  If the source IP address is still 192.168.0.x, maybe try verifying that the iptables rules listed above are the only ones present by running 'iptables -t nat -L'.

---

### Post by temp1029 on 2013-09-30
Thanks for the response and suggestion 7182818.

I tried running the command below, with the included results (over and over again).

```

tcpdump -i eth0 host 192.168.0.11

20:44:45.028623 IP 192.168.0.11.60531 > [DNS_server].[isp].net.domain: 35856+ A? talk.google.com. (33)
20:44:45.028659 IP 192.168.0.11.60531 > [DNS_server].[isp].net.domain: 35856+ A? talk.google.com. (33)
20:44:45.028669 IP 192.168.0.11.60531 > google-public-dns-a.google.com.domain: 35856+ A? talk.google.com. (33)

```

I believe this is the browser on the machine at 192.168.0.11 trying the three different DNS servers (I removed the full urls for my ISPs DNS servers) I defined in my DHCP setup.

I don't see any other rules in the NAT table of iptables.  Running the command below I get the included results.

```

iptables -t nat -L

Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  all  --  anywhere             anywhere

```

Anything else anyone could think of for me to try?

---

### Post by 7182818 on 2013-09-30
I could be mistaken, but I believe that since you see packets with a source of 192.168.0.11 leaving your eth0 interface that NAT is not happening, which is why the DNS responses never come back to you (since the 192.168.0.0/16 address range is not routable.)  Maybe ensure that your eth0 interface is successfully getting an IP from the modem using ifconfig?  Other than that, the only thing I can think of is to list the rules in the other iptables tables and make sure there isn't anything weird there.  Hopefully someone else will have some more suggestions!

---

