---
title: "Publishing the NVR on the VDS’ white IP via remote 4G router with modem through an L2"
date: 2014-03-20
forum: Networking &amp; Wireless
---

### Post by encor44 on 2014-03-20
Hello community! 
[SIZE=3]**:confused: NEED HELP with forwarding multiple ports from a service, running on a l2tp VPN client to the eth0 interface of the VPN Server!!**[/SIZE]
I&#8217;m struggling with a network scheme for video surveillance with remote access (see picture)
[ATTACH=CONFIG]251343[/ATTACH]
The only internet available at the _NVR_&#8217; point is a 3G\LTE. The provider gives only a &#8216;gray dynamic&#8217; IP (actually under NAT) at the _MODEM_, so DynDNS doesn&#8217;t work. So, I want to use a _VDS_ with the white public IPv4 (x.x.x.x) to access the _NVR_ through a L2TP VPN channel established between _ROUTER_ and _VDS_.

Need your help with these 2 problems: 
**_Problem1_**: I *can&#8217;t load a * NVR&#8217;s web interface page, when behind SQUID or company&#8217;s firewall. (If I use a modem connected to the laptop directly, I can load NVR&#8217;s web interface and I can login and I can watch the video). 
How can it be? Is this an MTU issue or some REDIRECT that is rejected? 
*Symptom*:  The endless &#8220;Waiting for [http://x.x.x.x](http://x.x.x.x) ..&#8221; and spinning round in IE 8 ..10. No ERROR MESSAGE, white screen. 
Pls, see squid.conf attached. I can surf the regular web, skype, ssh etc. begind this squid, but can&#8217;t load my [http://x.x.x.x](http://x.x.x.x) page. 
May this squid.conf cause this problem (it has allow all)?
```
:~$ sudo grep -v '^$'  /etc/squid3/squid.conf  |grep -v '^ *#'
 
http_access allow all
acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
acl localnet src 10.0.0.0/8     # RFC1918 possible internal network
acl localnet src 172.16.0.0/12  # RFC1918 possible internal network
acl localnet src 192.168.217.0/16       # vmWare net
acl SSL_ports port 443
acl SSL_ports port 21
acl SSL_ports port 1024-65535
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl CONNECT method CONNECT
http_access allow all
http_access allow localnet
http_access allow manager localhost
acl open_ports port 21
http_access allow open_ports
http_access allow localhost
http_port 3128
cache_dir ufs /var/spool/squid3 100 16 256
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0     0%      0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .               0       20%     4320
error_directory /usr/share/squid-langpack/Russian-1251
http_access allow all
```
 
**_[U]Problem_2[/U]**: The mobile software iVMS-4500 (adroid, iOS) &#8211; doesn&#8217;t play the video, even it can login.

[SIZE=4]Please, help me with iptables, port forwarding and routing! I&#8217;ve totally messed up with it!!![/SIZE]   :confused: :confused: :confused:

Most articles googled describes how to access some IT service behind the VPN, but in my case, I need to publish the IT service running on the VPN-client&#8217; side, and publish that service on the external IP of the VPN-server.
I can man iptables and man route but I don&#8217;t clearly understand what exactly do I need to do for my purpose. 

**Scheme detailed description and tests (described from target to the remote client)**: 

_**1. **_The _locally connected client_ and locally running iVMS-4500 on the 192.168.1.0/24 network can see the video and ping both _NVR_ with no problems:
```
ping 192.168.1.108      -> ping works
ping google.com    -> ping works
[http://192.168.1.108:80](http://192.168.1.108:80) -> the page loads and the video works
[http://www.google.com](http://www.google.com) -> internet works
```
 
**_2. _**There is a l2tp VPN server set up and running on the _VDS_ (as described in p.3). 
On the _ROUTER_ there is a l2tp VPN client connection is set up and running OK:

```
Server address: x.x.x.x
Login name: fb10usr2
Password: *********
Authentication algorithm: auto
Enable encryption: NO 
Enable CCP (PPP Compression Control): NO
Configure IP: Auto
DNS 1: 8.8.8.8
Adjust TCP-MSS automatically: Yes  
 
fb100   L2TP0
Status: Standing by
IP address:        10.152.2.2
IP subnet Mask:    255.255.255.255
Server address:    10.152.2.1
```
 
On the _ROUTER_ I can ping the VPN Server:
[HTML]Ping host: 10.152.2.1 
Ping host:count:size:
Sending ICMP ECHO request to 10.152.2.1
PING 10.152.2.1 (10.152.2.1) 100 (128) bytes of data.
128 bytes from 10.152.2.1: icmp_req=1, ttl=64, time=100.47 ms.
. . . . . 
128 bytes from 10.152.2.1: icmp_req=5, ttl=64, time=59.70 ms.
--- 10.152.2.2 ping statistics ---
5 packets transmitted, 5 packets received, 0% packet loss,[/HTML]

 
_**3. **_There is a L2TP VPN server set up and running on the _VDS_.
Interface configuration the _VDS_:
Ifconfig:
```
~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:3c:df:e6:af
          inet addr x.x.x.x  Bcast:144.76.141.95  Mask:255.255.255.224
          inet6 addr: fe80::216:3cff:fedf:e6af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11085 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:964511 (964.5 KB)  TX bytes:245538 (245.5 KB)
 
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
ppp0      Link encap point-to-Point Protocol
          inet addr:10.152.2.1  P-t-P:10.152.2.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:3178 (3.1 KB)  TX bytes:417 (417.0 B)
```
 
I have  a script to run on the ppp0 is up: [FONT=courier new]/etc/ppp/ip-up.d/startvpnroute[/FONT]
```
#!/bin/sh
 
PATH=/sbin:/bin:/usr/sbin:/usr/bin
 
echo "Flushing ip tables.."
 
iptables -F
iptables -F -t nat
iptables -F -t mangle
iptables -X
iptables -X -t nat
iptables -X -t mangle
 
#################################################################
# reset the default policies in the filter table.               #
#################################################################
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
#################################################################
# reset the default policies in the nat table.                  #
#################################################################
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -P POSTROUTING ACCEPT
iptables -t nat -P OUTPUT ACCEPT
#################################################################
# reset the default policies in the mangle table.               #
#################################################################
iptables -t mangle -P PREROUTING ACCEPT
iptables -t mangle -P OUTPUT ACCEPT
#################################################################
# flush all the rules in the filter and nat tables.             #
#################################################################
iptables -F
iptables -t nat -F
iptables -t mangle -F
#################################################################
# erase all chains that's not default in filter and nat table.  #
#################################################################
iptables -X
iptables -t nat -X
iptables -t mangle -X
 
echo "Listing ip tables:"
iptables -L -n -v -t nat
 
echo "repairing route table .."
 
# Delete auto created route for VPN with def gw:
route del -host 10.152.2.2 gw 0.0.0.0 dev ppp0
 
# Add the route w\ correct gw
route add -net 192.168.1.0/24 gw 10.152.2.1
# setting may drop after reboot
echo 1 > /proc/sys/net/ipv4/ip_forward
sysctl -p /etc/sysctl.conf
 
echo "Finally, LISTING route table:"
route
 
# &#1055;&#1088;&#1086;&#1076;&#1072;&#1082;&#1096;&#1085; :::
EXT_IP="x.x.x.x" 
INT_IP="10.152.2.1"           
EXT_IF=eth0                   
INT_IF=ppp0                            
LAN_IP="192.168.1.108"    
SRV_PORT=80                  
 
iptables -t nat -A PREROUTING --dst $EXT_IP -p tcp --dport $SRV_PORT -j DNAT --to-destination $LAN_IP
iptables -t nat -A POSTROUTING --dst $LAN_IP -p tcp --dport $SRV_PORT -j SNAT --to-source $INT_IP
iptables -t nat -A OUTPUT --dst $EXT_IP -p tcp --dport $SRV_PORT -j DNAT --to-destination $LAN_IP
iptables -I FORWARD 1 -i $EXT_IF -o $INT_IF -d $LAN_IP -p tcp -m tcp --dport $SRV_PORT -j ACCEPT
 
# Router&#8217; admin page :::
iptables -t nat -I PREROUTING -p tcp --dport 8085 -j DNAT --to-destination  192.168.1.1:80
 
# Alter port for NVR to login::
iptables -t nat -I PREROUTING -p tcp --dport 81 -j DNAT --to-destination  192.168.1.108:80
 
# Masquarading
iptables -t nat -I POSTROUTING -j MASQUERADE
 
############
# RTSP - TCP
EXT_IP="x.x.x.x" 
INT_IP="10.152.2.1"           
EXT_IF=eth0                   
INT_IF=ppp0                   
LAN_IP="192.168.1.108"    
SRV_PORT=554              
# Sorry, don&#8217;t know how to make a GOTO call in a bash script :-/
iptables -t nat -A PREROUTING --dst $EXT_IP -p tcp --dport $SRV_PORT -j DNAT --to-destination $LAN_IP
iptables -t nat -A POSTROUTING --dst $LAN_IP -p tcp --dport $SRV_PORT -j SNAT --to-source $INT_IP
iptables -t nat -A OUTPUT --dst $EXT_IP -p tcp --dport $SRV_PORT -j DNAT --to-destination $LAN_IP
iptables -I FORWARD 1 -i $EXT_IF -o $INT_IF -d $LAN_IP -p tcp -m tcp --dport $SRV_PORT -j ACCEPT
 
############
# RTSP - UDP
EXT_IP="x.x.x.x" 
INT_IP="10.152.2.1"           
EXT_IF=eth0                   
INT_IF=ppp0                            
LAN_IP="192.168.1.108"    
SRV_PORT=554                  
 
iptables -t nat -A PREROUTING --dst $EXT_IP -p udp --dport $SRV_PORT -j DNAT --to-destination $LAN_IP
iptables -t nat -A POSTROUTING --dst $LAN_IP -p udp --dport $SRV_PORT -j SNAT --to-source $INT_IP
iptables -t nat -A OUTPUT --dst $EXT_IP -p udp --dport $SRV_PORT -j DNAT --to-destination $LAN_IP
iptables -I FORWARD 1 -i $EXT_IF -o $INT_IF -d $LAN_IP -p udp -m udp --dport $SRV_PORT -j ACCEPT
 
############
# PORT 8000 - TCP
EXT_IP="x.x.x.x" 
INT_IP="10.152.2.1"           
EXT_IF=eth0                   
INT_IF=ppp0                            
LAN_IP="192.168.1.108"    
SRV_PORT=8000                  
 
iptables -t nat -A PREROUTING --dst $EXT_IP -p tcp --dport $SRV_PORT -j DNAT --to-destination $LAN_IP
iptables -t nat -A POSTROUTING --dst $LAN_IP -p tcp --dport $SRV_PORT -j SNAT --to-source $INT_IP
iptables -t nat -A OUTPUT --dst $EXT_IP -p tcp --dport $SRV_PORT -j DNAT --to-destination $LAN_IP
iptables -I FORWARD 1 -i $EXT_IF -o $INT_IF -d $LAN_IP -p tcp -m tcp --dport $SRV_PORT -j ACCEPT
 
echo "FINALLY, LISTING ip tables:"
iptables -L -n -v -t nat
 
exit 0
 
```
--------------------------
 
THE OUTPUT OF THIS SCRIPT if run mannually:
```
~# ./startvpnroute
Flushing ip tables..
Listing ip tables:
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
 
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
 
Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
 
Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
repairing route table ..
Finally, LISTING route table:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         vds24.net       0.0.0.0         UG    0      0        0 eth0
144.76.141.64   *               255.255.255.224 U     0      0        0 eth0
192.168.1.0     10.152.2.1      255.255.255.0   UG    0      0        0 ppp0
FINALLY, LISTING ip tables:
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:81 to:192.168.1.108:80
    0     0 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8085 to:192.168.1.1:80
    0     0 DNAT       tcp  --  *      *       0.0.0.0/0            x.x.x.x        tcp dpt:80 to:192.168.1.108
    0     0 DNAT       tcp  --  *      *       0.0.0.0/0            x.x.x.x        tcp dpt:554 to:192.168.1.108
    0     0 DNAT       udp  --  *      *       0.0.0.0/0            x.x.x.x        udp dpt:554 to:192.168.1.108
    0     0 DNAT       tcp  --  *      *       0.0.0.0/0            x.x.x.x        tcp dpt:8000 to:192.168.1.108
 
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
 
Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DNAT       tcp  --  *      *       0.0.0.0/0            x.x.x.x        tcp dpt:80 to:192.168.1.108
    0     0 DNAT       tcp  --  *      *       0.0.0.0/0            x.x.x.x        tcp dpt:554 to:192.168.1.108
    0     0 DNAT       udp  --  *      *       0.0.0.0/0            x.x.x.x        udp dpt:554 to:192.168.1.108
    0     0 DNAT       tcp  --  *      *       0.0.0.0/0            x.x.x.x        tcp dpt:8000 to:192.168.1.108
 
Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 MASQUERADE  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 SNAT       tcp  --  *      *       0.0.0.0/0            192.168.1.108        tcp dpt:80 to:10.152.2.1
    0     0 SNAT       tcp  --  *      *       0.0.0.0/0            192.168.1.108        tcp dpt:554 to:10.152.2.1
    0     0 SNAT       udp  --  *      *       0.0.0.0/0            192.168.1.108        udp dpt:554 to:10.152.2.1
    0     0 SNAT       tcp  --  *      *       0.0.0.0/0            192.168.1.108        tcp dpt:8000 to:10.152.2.1
 
```

Iptables-save output:
 
```
# iptables-save
# Generated by iptables-save v1.4.18 on Thu Mar 20 16:26:48 2014
*mangle
:PREROUTING ACCEPT [578:276180]
:INPUT ACCEPT [221:127889]
:FORWARD ACCEPT [357:148291]
:OUTPUT ACCEPT [213:45489]
:POSTROUTING ACCEPT [570:193780]
COMMIT
# Completed on Thu Mar 20 16:26:48 2014
# Generated by iptables-save v1.4.18 on Thu Mar 20 16:26:48 2014
*nat
:PREROUTING ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
-A PREROUTING -p tcp -m tcp --dport 81 -j DNAT --to-destination 192.168.1.108:80
-A PREROUTING -p tcp -m tcp --dport 8085 -j DNAT --to-destination 192.168.1.1:80
-A PREROUTING -d x.x.x.x/32 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.1.108
-A PREROUTING -d x.x.x.x/32 -p tcp -m tcp --dport 554 -j DNAT --to-destination 192.168.1.108
-A PREROUTING -d x.x.x.x/32 -p udp -m udp --dport 554 -j DNAT --to-destination 192.168.1.108
-A PREROUTING -d x.x.x.x/32 -p tcp -m tcp --dport 8000 -j DNAT --to-destination 192.168.1.108
-A OUTPUT -d x.x.x.x/32 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.1.108
-A OUTPUT -d x.x.x.x/32 -p tcp -m tcp --dport 554 -j DNAT --to-destination 192.168.1.108
-A OUTPUT -d x.x.x.x/32 -p udp -m udp --dport 554 -j DNAT --to-destination 192.168.1.108
-A OUTPUT -d x.x.x.x/32 -p tcp -m tcp --dport 8000 -j DNAT --to-destination 192.168.1.108
-A POSTROUTING -j MASQUERADE
-A POSTROUTING -d 192.168.1.108/32 -p tcp -m tcp --dport 80 -j SNAT --to-source 10.152.2.1
-A POSTROUTING -d 192.168.1.108/32 -p tcp -m tcp --dport 554 -j SNAT --to-source 10.152.2.1
-A POSTROUTING -d 192.168.1.108/32 -p udp -m udp --dport 554 -j SNAT --to-source 10.152.2.1
-A POSTROUTING -d 192.168.1.108/32 -p tcp -m tcp --dport 8000 -j SNAT --to-source 10.152.2.1
COMMIT
# Completed on Thu Mar 20 16:26:48 2014
# Generated by iptables-save v1.4.18 on Thu Mar 20 16:26:48 2014
*filter
:INPUT ACCEPT [219:127725]
:FORWARD ACCEPT [307:142525]
:OUTPUT ACCEPT [214:45608]
-A FORWARD -d 192.168.1.108/32 -i eth0 -o ppp0 -p tcp -m tcp --dport 8000 -j ACCEPT
-A FORWARD -d 192.168.1.108/32 -i eth0 -o ppp0 -p udp -m udp --dport 554 -j ACCEPT
-A FORWARD -d 192.168.1.108/32 -i eth0 -o ppp0 -p tcp -m tcp --dport 554 -j ACCEPT
-A FORWARD -d 192.168.1.108/32 -i eth0 -o ppp0 -p tcp -m tcp --dport 80 -j ACCEPT
COMMIT
# Completed on Thu Mar 20 16:26:48 2014
```
 
**_4. _**On the VDS with the VPN connection established I can ping the NVR and ROUTER :
 ```
~# ping 192.168.1.108
PING 192.168.1.108 (192.168.1.108) 56(84) bytes of data.
64 bytes from 192.168.1.108: icmp_seq=1 ttl=63 time=114 ms
64 bytes from 192.168.1.108: icmp_seq=2 ttl=63 time=175 ms
. . . . 
 
~# ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=63 time=214 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=63 time=135 ms
. . . . 
^C
```
 
**_5. _**On the _VDS_ I can also wget the web page of _NVR_:
The _NVR_ main web interface page:
```
~# wget [http://192.168.1.108:80](http://192.168.1.108:80)
--2014-03-13 16:29:10--  [http://192.168.1.108/](http://192.168.1.108/)
Connecting to 192.168.1.108:80... connected.
HTTP request sent, awaiting response... 302 Redirect
Location: [http://192.168.1.108/index.asp](http://192.168.1.108/index.asp) [following]
--2014-03-13 16:29:10--  [http://192.168.1.108/index.asp](http://192.168.1.108/index.asp)
Connecting to 192.168.1.108:80... connected.
HTTP request sent, awaiting response... 
^C
 
```
At this point I never can  wget the web page, can this be a cause for _P1_? If it is a problem here, how can I ever seen the page on a laptop? 
 
**_6. _**The _ROUTER_ admin page:
```
~# wget [http://192.168.1.1:80](http://192.168.1.1:80)
--2014-03-13 16:29:26--  [http://192.168.1.1/](http://192.168.1.1/)
Connecting to 192.168.1.1:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
```
 
**_7. _**And, finally, I can access the NVR main web interface page from a computer connected to the internet &#8216;directly&#8221;:
[http://x.x.x.x:80](http://x.x.x.x:80)
This loads the page, I can login and see the _NVR&#8217;s_ main interface web page and I can see the video.
When the laptop behind the squid or some corporate firewall I get the P1 problem (see above).
I can also see the stream on a laptop with VLC, connecting to the RTSP stream of the NVR via public IP : ([FONT=courier new]rtsp: //login: pass@x.x.x.x:554/PSIA/streaming/channels/101/[/FONT]) .
To check the ports open I can successfully:
```
telnet x.x.x.x 554 
```
 
**_Problem2: _**The mobile software [FONT=courier new]iVMS-4500 [/FONT](adroid, iOS) &#8211; doesn&#8217;t how the video, even it can login.
Symptom:  After I tap a &#8216;save&#8217; button, it shows there are 5 channels, and attempts to display a stream. I get NO ERROR, just an endless black screen. 
iVMS-4500 uses _port 8000_, to check the ports open I can successfully:
```
telnet x.x.x.x 8000 
```

_**Question**_: is that possible that P2 has the same source as P1?
 
[SIZE=5]Dear guru! Please help!!![/SIZE] 
Thank you in advance! 

I also tried to run several network sniffing with [FONT=courier new]tcpdump [/FONT]and [FONT=courier new]MS Network Monitor 3.4[/FONT] where I can see some [FONT=courier new]RESET [/FONT]returned to the rtsp requests (can also post here).

---

