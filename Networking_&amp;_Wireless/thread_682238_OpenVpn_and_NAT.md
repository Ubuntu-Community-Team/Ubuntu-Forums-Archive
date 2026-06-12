---
title: "OpenVpn and NAT"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by chrisdavid_175 on 2008-01-29
For my router, I use a linuxbox as a router that is using OpenVPN. How would I go about setting up iptables w/ masquerade to allow the other hosts on the network to use the vpn connection?

I've tried using the following:

iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o tun0 -j MASQUERADE

192.168.1.0/24 - internal network on eth0
eth1 is external interface to the internet
tun0 is vpn connection

---

### Post by Yhetti on 2008-01-30
First, you have to make sure the packets are actually getting routed out tun0 and not out eth1.  What does the routing table look like with OVPN up?

---

### Post by chrisdavid_175 on 2008-01-30
The following is the routing table after OpenVPN has been run:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
211.127.115.22  192.168.15.1    255.255.255.255 UGH   0      0        0 eth1
10.8.0.9        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
10.8.0.0        10.8.0.9        255.255.255.0   UG    0      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.15.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         10.8.0.10       0.0.0.0         UG    0      0        0 tun0

This linuxbox is the router and OpenVPN client. It connects through the vpn quite ok and accesses the Internet using the OpenVPN server as the default gateway. To clarify, I'm trying to get this linuxbox to NAT the network traffic on 192.168.1.0/24. 

The following is output from tcpdump -vvv -i tun0 -n when pinging from the linuxbox (OpenVPN client) to the OpenVPN server:

18:42:57.270917 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto ICMP (1), length 84) 10.8.0.10 > 10.8.0.1: ICMP echo request, id 49169, seq 19, length 64
18:42:57.452318 IP (tos 0x0, ttl 64, id 4157, offset 0, flags [none], proto ICMP (1), length 84) 10.8.0.1 > 10.8.0.10: ICMP echo reply, id 49169, seq 19, length 64
18:42:58.270913 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto ICMP (1), length 84) 10.8.0.10 > 10.8.0.1: ICMP echo request, id 49169, seq 20, length 64
18:42:58.453033 IP (tos 0x0, ttl 64, id 4158, offset 0, flags [none], proto ICMP (1), length 84) 10.8.0.1 > 10.8.0.10: ICMP echo reply, id 49169, seq 20, length 64

The following is the same command on eth0 when pinging from a host in the LAN (192.168.1.5) to 211.127.115.22 (OpenVPN server):

tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
18:44:39.296745 IP (tos 0x0, ttl 128, id 1799, offset 0, flags [none], proto ICMP (1), length 60) 192.168.1.5 > 211.127.115.22: ICMP echo request, id 512, seq 23045, length 40

The linuxbox will receive the ping request on the inside but it won't receive a reply from the opposite direction.

Using the same command on tun0 when pinging from the other host on the inside LAN has no output so iptables isn't forwarding it from eth0 to tun0 at all.

I've tried using the following two commands separately:
iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o tun0 -j MASQUERADE
iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o 10.8.0.10 -j MASQUERADE

---

### Post by Yhetti on 2008-01-31
Don't hate me, I just have to check.  IP Forwarding is turned on, correct?  I forget it frequently. 

If forwarding is on, the next thing I would try is a standard SNAT instead of masq.  I like masq, but I think it might be causes problems in this case.  Something like

iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o tun0 -j SNAT --to 10.8.0.10

I'm also afraid it's trying to route out eth1 for some reason (certainly possible) and since the routing decision is already made, that never takes effect anyway.   Can you follow a few pings through the entire routing decision (tcpdump all interfaces)

---

### Post by chrisdavid_175 on 2008-02-01
I have IP set to forward:

root@ubuntu7-10s1:/home/cdavid# cat /proc/sys/net/ipv4/ip_forward
1

Using iptables with SNAT didn't really do anything for me. I'd have to create the reverse connections with that as well along with port forwarding to pass the packets to another host on the network.

The following are the results to the tcpdump command for eth0, eth1, and tun0 respectively:

root@ubuntu7-10s1:/home/cdavid# tcpdump -vvv -n -i eth0
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
22:24:40.644360 IP (tos 0x0, ttl 128, id 7718, offset 0, flags [none], proto ICMP (1), length 60) 192.168.1.5 > 211.127.115.22: ICMP echo request, id 512, seq 24602, length 40
22:24:46.143964 IP (tos 0x0, ttl 128, id 7719, offset 0, flags [none], proto ICMP (1), length 60) 192.168.1.5 > 211.127.115.22: ICMP echo request, id 512, seq 24858, length 40

(tcpdump -vvv -n -i eth1)
22:25:08.070348 IP (tos 0x0, ttl 128, id 15211, offset 0, flags [DF], proto TCP (6), length 40) 192.168.15.3.59805 > 192.168.15.2.22: ., cksum 0x7132 (correct), 39989:39989(0) ack 7879696 win 251
22:25:08.070457 IP (tos 0x10, ttl 64, id 54204, offset 0, flags [DF], proto TCP (6), length 268) 192.168.15.2.22 > 192.168.15.3.59805: P 7879924:7880152(228) ack 39989 win 685
22:25:08.070664 IP (tos 0x10, ttl 64, id 54205, offset 0, flags [DF], proto TCP (6), length 460) 192.168.15.2.22 > 192.168.15.3.59805: P 7880152:7880572(420) ack 39989 win 685
22:25:08.070825 IP (tos 0x10, ttl 64, id 54206, offset 0, flags [DF], proto TCP (6), length 268) 192.168.15.2.22 > 192.168.15.3.59805: P 7880572:7880800(228) ack 39989 win 685
22:25:08.070981 IP (tos 0x10, ttl 64, id 54207, offset 0, flags [DF], proto TCP (6), length 268) 

root@ubuntu7-10s1:/home/cdavid# tcpdump -vvv -n -i tun0
tcpdump: WARNING: arptype 65534 not supported by libpcap - falling back to cooked socket
tcpdump: listening on tun0, link-type LINUX_SLL (Linux cooked), capture size 96 bytes

0 packets captured
0 packets received by filter
0 packets dropped by kernel
(after running for a few minutes)

For whatever reason, the packets won't go from eth0 to tun0.

---

