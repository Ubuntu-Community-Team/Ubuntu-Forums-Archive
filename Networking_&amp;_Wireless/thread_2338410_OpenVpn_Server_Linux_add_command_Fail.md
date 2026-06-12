---
title: "OpenVpn Server Linux add command Fail"
date: 2016-09-28
forum: Networking &amp; Wireless
---

### Post by malice95 on 2016-09-28
Hello all,

I have Ubuntu Server 16.04 installed on one laptop, and a normal version of ubuntu 16.04 on another. I recently configured an openvpn server on my Ubuntu, using this guide:  [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-16-04) . Painstakingly got through the process, and when I try running it through my latop it seems to intialize, but my ip address does not change. I think the cause of the problem might be the one line reporting and error status  2.
I hope part of this log post isn't redundant, but here it is: 

Wed Sep 28 00:36:32 2016 ROUTE_GATEWAY 192.168.1.1/255.255.255.0 IFACE=wlp2s0 HWADDR=70:77:81:6c:2c:5f
Wed Sep 28 00:36:32 2016 TUN/TAP device tun0 opened
Wed Sep 28 00:36:32 2016 TUN/TAP TX queue length set to 100
Wed Sep 28 00:36:32 2016 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Wed Sep 28 00:36:32 2016 /sbin/ip link set dev tun0 up mtu 1500
Wed Sep 28 00:36:32 2016 /sbin/ip addr add dev tun0 local 10.8.0.6 peer 10.8.0.5
Wed Sep 28 00:36:32 2016 /etc/openvpn/update-resolv-conf tun0 1500 1570 10.8.0.6 10.8.0.5 init
dhcp-option DNS 208.67.222.222
dhcp-option DNS 208.67.220.220
Wed Sep 28 00:36:32 2016 /sbin/ip route add 192.168.1.13/32 dev wlp2s0
RTNETLINK answers: File exists
Wed Sep 28 00:36:32 2016 ERROR: Linux route add command failed: external program exited with error status: 2
Wed Sep 28 00:36:32 2016 /sbin/ip route add 0.0.0.0/1 via 10.8.0.5
Wed Sep 28 00:36:32 2016 /sbin/ip route add 128.0.0.0/1 via 10.8.0.5
Wed Sep 28 00:36:32 2016 /sbin/ip route add 10.8.0.1/32 via 10.8.0.5
Wed Sep 28 00:36:32 2016 GID set to nogroup
Wed Sep 28 00:36:32 2016 UID set to nobody
Wed Sep 28 00:36:32 2016 Initialization Sequence Completed

My server.conf file:
port 1194
proto udp
dev tun
ca ca.cert
cert server.crt
key server.key
dh dh2048.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.10.0 255.255.255.0"
push "route 192.168.20.0 255.255.255.0"
push "dhcp-option DNS 208.67.222.222"
push "dhcp-option DNS 208.67.228.220"
keepalive 10 120
tls-auth ta.key 0
key-direction 0
cipher AES-128-CBC
auth SHA256
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb3

I tried looking up this error message, end I saw alot of the comments going towards changing the iptables in the /etc/sbin directory which confuses me because it's binary of course. The comments were saying to append with were similiar to the MASQUERADE option I set up in the ufw/before.rules file. 
And lastly here is my route pathway for my Ubuntu connecting laptopn(Note the interface here is different than the one I have on ubuntu server:enp6s0)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.8.0.5        128.0.0.0       UG    0      0        0 tun0
default         192.168.1.1     0.0.0.0         UG    600    0        0 wlp2s0
10.8.0.1        10.8.0.5        255.255.255.255 UGH   0      0        0 tun0
10.8.0.5        *               255.255.255.255 UH    0      0        0 tun0
128.0.0.0       10.8.0.5        128.0.0.0       UG    0      0        0 tun0
link-local      *               255.255.0.0     U     1000   0        0 wlp2s0
192.168.1.0     *               255.255.255.0   U     600    0        0 wlp2s0
192.168.1.13    *               255.255.255.255 UH    0      0        0 wlp2s0
 
Thank yall so much for any following advice, I have been trying to fix this for too long and it's frying my brain.

---

