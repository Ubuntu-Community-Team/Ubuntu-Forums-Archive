---
title: "Ubuntu - dynamically set default gateway - how?"
date: 2017-12-11
forum: Networking &amp; Wireless
---

### Post by wowiesy2 on 2017-12-11
my understanding is that.. we can have multiple gateways setup.. but it is always the DEFAULT GATEWAY first that gets first try.. 

this is the setting:

SERVER SIDE LAN:

WAN link IP1: xxx.xxx.xxx.xxx
WAN1 gateway: 192.168.100.2

WAN link IP2: yyy.yyy.yyy.yyy
WAN2 gateway: 192.168.100.5

this is done to sort of failover / redundancy purpose

I do have setup an OpenVPN server box at 192.168.100.253, its default gateway is setup to be 192.168.100.5

when I try to connect a vpn client thru yyy.yyy.yyy.yyy, i am able to successfuly connect the vpn client... 

when I try to connect the vpn client thru xxx.xxx.xxx.xxx, I can not get the client to connect successfully... 

my hunch is that.. the VPN box default gateway is set to 100.5... but the packets are coming in from 100.2... VPN box, since its default gateway is setup to be 100.5, will always be returning packets to 100.5... effectively.. with this setup... I can not use the 2 WAN links for redundancy in so far as vpn redundancy is concerned...  unless i can change the default gateway dynamically at the VPN box... 

is my understanding correct? 

if yes.. then what's a good way to implement dynamic gateway for this?  

I thought about implementing this using fwmark in iptables...   very similar to MultiWAN load balancing / failover setup (iptables portion)...   any other alternatives i can use?

if i use fwmark in iptables... similar to MultiWAN setup.. I should also use source based policy routing... ..  I should scan source IP based on which gateway it passed through then determine from there which gateway to forward it to?  in MultiWAN setup..  the packets are being marked to identify which interface (WAN1 or WAN2) it should come out... but in this case..   there is only 1 interface, a LAN interface...   I will just play with the gateway...  is this doable?  as far as the VPN box.. there is still 1 LAN interface... iit only has to choose which gateway to use...

---

### Post by TheFu on 2017-12-12
The route used is selected using the "metric" value and subnets.  Lower metric values have priority.  It really is that simple.

Post the output from **route -n** if you want help. Long descriptions don't cover what that output would clearly tell us.

As far as dynamically changing those things, the routing table can certainly be modified as needed for the system. Doing it on a process-to-process or userid-to-userid level isn't supported.  Routing is system-wide, but there are other techniques which can be used, if you have the stomach for the added complexity.

---

### Post by The Cog on 2017-12-12
I think that NAT is your problem here. You are right, I think there is asymmetric routing going on. This wouldn't normally be a problem except that I guess the two routers do not discuss and coordinate their NAT translations. So your client connects to the VPN server through x.x.x.x by connecting to x.x.x.x's IP address. I guess it then gets a response from address y.y.y.y which it ignores because this isn't the server it's trying to connect to. And in fact because the packet from y.y.y.y is an outgoing call (as far as the router is concerned), it is quite possible that the source port number is being changed by the router, disguising things even more.

I don't think you will be able to overcome the fact that the two routers are operating different NAT translation tables - asymmetric routing will not be possible. You will have to connect through whichever router is your server's default gateway. If that gateway fails, your clients will then have to change your default gateway and have the clients use the other gateway address.

So even changing the default gateway automatically (not that simple) wouldn't help.

---

### Post by wowiesy2 on 2017-12-13
at the OpenVPN box :

ifconfig: 
```

**kss1x@UBUNTUVPN**:**~**$ ifconfig
eno1      Link encap:Ethernet  HWaddr 94:c6:91:13:63:d8  
          inet addr:192.168.100.253  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::96c6:91ff:fe13:63d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:180291 errors:0 dropped:100329 overruns:0 frame:0
          TX packets:11759 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26428072 (26.4 MB)  TX bytes:1337940 (1.3 MB)
          Interrupt:16 Memory:dc100000-dc120000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:11987 (11.9 KB)  TX bytes:11987 (11.9 KB)


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.1  P-t-P:10.8.0.1  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:108641 (108.6 KB)  TX bytes:165644 (165.6 KB)

```


ip route show

```
**kss1x@UBUNTUVPN**:**~**$ ip route show
default via 192.168.100.5 dev eno1 onlink 
10.8.0.0/24 dev tun0  proto kernel  scope link  src 10.8.0.1 
169.254.0.0/16 dev eno1  scope link  metric 1000 
192.168.100.0/24 dev eno1  proto kernel  scope link  src 192.168.100.253 
192.168.111.0/24 via 10.8.0.2 dev tun0 
192.168.254.0/24 via 10.8.0.2 dev tun0 

```

default gateway was set here thru /etc/network/interfaces


now.. the solution i was thinking about.. was to use the pattern used in MultiWAN load balancing / failover - source based policy routing... 

first setup iptables to mark packets depending on where the packets came from (100.2 -> which is the gateway used when WAN1 IP is used, or 100.5 which is the gateway used when WAN2 IP is used)...  

something like: 

```
iptables -A PREROUTING -t mangle -j CONNMARK --restore-mark
iptables -A PREROUTING -t mangle --match mark --mark 1 -j ACCEPT
iptables -A PREROUTING -t mangle -i eno1 -d xxx.xxx.xxx.xxx -j MARK --set-mark 1
iptables -A PREROUTING -t mangle --match mark --mark 2 -j ACCEPT
iptables -A PREROUTING -t mangle -i eno1 -d yyy.yyy.yyy.yyy -j MARK --set-mark 2
iptables -A PREROUTING -t mangle -j CONNMARK --save-mark

```


say mark 1 is used for gateway 100.2, while mark 2 for gateway 100.5.. 

I used -i eno1  (input interface) -d xxx.xxx.xxx.xxx with destination ip address WAN1  (although this was DNAT'd to my machine at this point).. I'm not sure if at this point the destination ip is still "seen" or this is already replaced by the router into the router's address  

```


:/etc/iproute2# more rt_tables
#
# reserved values
#
255     local
254     main
253     default
0       unspec
#
# local
#
1       gw_one
2       gw_two/etc/iproute2# ip route show table gw_one
xxx.xxx.xxx.xxx/24 dev eno1  scope link
default via 192.168.100.2 dev eno1

/etc/iproute2# ip route show table gw_two
yyy.yyy.yyy.yyy/24 dev eno1  scope link
default via 192.168.100.5 dev eno1


ip rule add fwmark 1 table gw_one prio 1024
ip rule add fwmark 2 table gw_two prio 1025

```

there may be packets not that are not vpn client connected (say, ssh into the vpn box within the server side LAN)..  I can just set a default route for unmarked packets..

---

### Post by The Cog on 2017-12-13
Sweet. I wasn't aware of CONNMARK. That will very likely do the trick for you: you've done good research there. 

However, packets arriving at the OpenVPN server from your clients will have a destination address of the OpenVPN server, not the gateway public addresses x.x.x.x or y.y.y.y (NAT will have replaced those addresses). You only want to mark connections initiated by packets addresses to your server's OpenVPN port, and I think you will have to use the source MAC address to identify which of the two gateways sent the packet to you. Something like this perhaps (not tried, and made-up MAC addresses):
```
iptables -A PREROUTING -t mangle -j CONNMARK --restore-mark
iptables -A PREROUTING -t mangle --match mark --mark 1 -j ACCEPT
iptables -A PREROUTING -t mangle --match mark --mark 2 -j ACCEPT
iptables -A PREROUTING -t mangle -d 192.168.100.253 -p tcp --dport 1194 -m mac --mac-source 11:22:33:44:55:66 -j MARK --set-mark 1
iptables -A PREROUTING -t mangle -d 192.168.100.253 -p tcp --dport 1194 -m mac --mac-source 11:22:33:44:55:77 -j MARK --set-mark 2
iptables -A PREROUTING -t mangle -j CONNMARK --save-mark
```
Your use of ip rules for policy routing looks good to me. I think this will work.

P.S. Reference for others reading this thread: [https://home.regit.org/netfilter-en/netfilter-connmark/](https://home.regit.org/netfilter-en/netfilter-connmark/)

P.P.S. The article linked above tends to do all its work in the POSTROUTING chain, not the PREROUTING chain. I think in this case we need to use the OUTPUT chain at least for the restore-mark rule because the restored mark is then used in the routing decision. It may be that the set/restored mark causes incoming packets to be routed back to the gateway rather than allowed into the VPN server, so you may have to make sure you only do a restore-mark on outgoing packets, and only do the set-mark and save-mark on input packets. So the rules might end up being like this:
```
iptables -A INPUT -t mangle -p tcp --dport 1194 -m mac --mac-source 11:22:33:44:55:66 -j MARK --set-mark 1
iptables -A INPUT -t mangle -p tcp --dport 1194 -m mac --mac-source 11:22:33:44:55:77 -j MARK --set-mark 2
iptables -A INPUT -t mangle -p tcp --dport 1194 -j CONNMARK --save-mark
iptables -A OUTPUT -t mangle -p tcp --sport 1194 -j CONNMARK --restore-mark

```

---

