---
title: "OpenVPN Not Working - no traffic through tun0"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by notpace on 2008-02-10
Hi!

I'm trying to connect to my corporate VPN on a machine that is now dual-booting Windows XP and Ubuntu Gutsy.  Using OpenVPN GUI on the Windows Box, I can get in no problem.  On the Ubuntu box, however, it doesn't seem to be working.  Note: I've replaced my company name with "work"

Our VPN is set up so that clients connect with pkcs12 certificates (which AFAIK are not supported by network-manager yet), so I'm trying to connect with openvpn via the command line:

```
 sudo openvpn /home/notpace/work.ovpn
```

The Configuration file is as follows:
```
#OpenVPN Server conf
tls-client
client
dev tun
proto udp
tun-mtu 1500
remote vpn.work.com 1194
pkcs12 /home/notpace/work.p12
cipher DES-EDE-CBC
comp-lzo
verb 3
```

The openvpn completes successfully:
```
Initialization Sequence Completed
```

...but I can't ping the DHCP server:
```
notpace@notpace-laptop:~$ ping 172.10.11.21
PING 172.10.11.21 (172.10.11.21) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

```

Also, looking at ifconfig, it seems as if the tunnel is up, but no traffic is going through it...at all:
```
eth0      Link encap:Ethernet  HWaddr 00:1A:6B:38:27:A0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x1840 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32662 (31.8 KB)  TX bytes:32662 (31.8 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:172.10.11.22  P-t-P:172.10.11.21  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:13:E8:57:0E:3F  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe57:e3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12199 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8870907 (8.4 MB)  TX bytes:1724421 (1.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-57-0E-3F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Has anyone run into this before [slash] does anyone have any ideas?

Thanks!
-notpace

---

### Post by The Cog on 2008-02-10
Operation not permitted is odd. I have no idea what that's all about. A couple of questions though:
Can you ping 172.10.11.22?
Do you have any routes to the 172.10 area? Post the output from **route -n**

---

### Post by joebeasley on 2008-02-10
You have to tell the vpn what traffic to route.  For example,  if network 10.2.3.0/24 and host 10.4.5.6 are on the other side, you would add the following to your config file.

route 10.2.3.0 255.255.255.0
route 10.4.5.6 255.255.255.255



The other side has to route back to your network.

---

### Post by notpace on 2008-02-11
Thanks guys!  I really appreciate the response.  Unfortunately, I'm not out of the woods just yet:

Here's the output for route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.10.11.21    0.0.0.0         255.255.255.255 UH    0      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
172.10.10.0     172.10.11.21    255.255.255.0   UG    0      0        0 tun0
172.10.11.0     172.10.11.21    255.255.255.0   UG    0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```

The routes to 172.10.10.0/24 and 172.10.11.0/24 aren't in my configuration file, but they must be in my .p12 file, because they show up in the routing table.

To add to the weirdness, when I ping 172.10.11.22, I get 100% packet loss (but at least it doesn't give me the ping: sendmsg: Operation not permitted error that I get with every other IP in that range).

So...I'm not really sure why the traffic isn't routing correctly.  Any more ideas?

Thanks!
-notpace

---

### Post by The Cog on 2008-02-13
OK, i tried a tunnel here. I can ping my own tunnel end address.I can't ping the far end address. But I can ping the .1 address which is the tunnel address of the VPN server. So I guess you should be able to ping 172.10.11.1.  Give that a try. 

Also, when I ping the server (.1) I see the packet counters on the tunnel interface increase. You should certainly see tx packets counted if you try and ping something on 172.10.10.x.

---

### Post by notpace on 2008-02-15
Unfortunately, I'm still getting an error message when I ping 

```
notpace@notpace-laptop:~$ ping 172.10.11.1
PING 172.10.11.1 (172.10.11.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

```

172.10.10.1 gives the same error message.

I'm really stuck here - it doesn't make any sense that the routes are there, but there's no traffic going through them.

---

### Post by The Cog on 2008-02-16
Are you running a firewall? Can you post the output from this command:
sudo iptables-save -c

---

### Post by notpace on 2008-02-16
Here's the output:
```
notpace@notpace-laptop:~$ sudo iptables-save -c
# Generated by iptables-save v1.3.6 on Sat Feb 16 19:49:21 2008
*nat
:PREROUTING ACCEPT [150:44087]
:POSTROUTING ACCEPT [2369:179267]
:OUTPUT ACCEPT [2369:179267]
COMMIT
# Completed on Sat Feb 16 19:49:21 2008
# Generated by iptables-save v1.3.6 on Sat Feb 16 19:49:21 2008
*mangle
:PREROUTING ACCEPT [11221:7071965]
:INPUT ACCEPT [11189:7060903]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [13413:4073582]
:POSTROUTING ACCEPT [13410:4072916]
COMMIT
# Completed on Sat Feb 16 19:49:21 2008
# Generated by iptables-save v1.3.6 on Sat Feb 16 19:49:21 2008
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [1:207]
:INBOUND - [0:0]
:LOG_FILTER - [0:0]
:LSI - [0:0]
:LSO - [0:0]
:OUTBOUND - [0:0]
[0:0] -A INPUT -s 68.87.71.226 -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -j ACCEPT 
[44:4934] -A INPUT -s 68.87.71.226 -p udp -j ACCEPT 
[0:0] -A INPUT -s 68.87.73.242 -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -j ACCEPT 
[0:0] -A INPUT -s 68.87.73.242 -p udp -j ACCEPT 
[0:0] -A INPUT -i lo -j ACCEPT 
[204:14852] -A INPUT -p icmp -m limit --limit 10/sec -j ACCEPT 
[0:0] -A INPUT -d 255.255.255.255 -i wlan0 -j DROP 
[0:0] -A INPUT -d 192.168.1.255 -j DROP 
[0:0] -A INPUT -s 224.0.0.0/255.0.0.0 -j DROP 
[0:0] -A INPUT -d 224.0.0.0/255.0.0.0 -j DROP 
[0:0] -A INPUT -s 255.255.255.255 -j DROP 
[0:0] -A INPUT -d 0.0.0.0 -j DROP 
[24:960] -A INPUT -m state --state INVALID -j DROP 
[0:0] -A INPUT -f -m limit --limit 10/min -j LSI 
[10917:7040157] -A INPUT -i wlan0 -j INBOUND 
[0:0] -A INPUT -j LOG_FILTER 
[0:0] -A INPUT -j LOG --log-prefix "Unknown Input" --log-level 6 
[0:0] -A FORWARD -p icmp -m limit --limit 10/sec -j ACCEPT 
[0:0] -A FORWARD -j LOG_FILTER 
[0:0] -A FORWARD -j LOG --log-prefix "Unknown Forward" --log-level 6 
[0:0] -A OUTPUT -s 192.168.1.103 -d 68.87.71.226 -p tcp -m tcp --dport 53 -j ACCEPT 
[44:2791] -A OUTPUT -s 192.168.1.103 -d 68.87.71.226 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A OUTPUT -s 192.168.1.103 -d 68.87.73.242 -p tcp -m tcp --dport 53 -j ACCEPT 
[0:0] -A OUTPUT -s 192.168.1.103 -d 68.87.73.242 -p udp -m udp --dport 53 -j ACCEPT 
[0:0] -A OUTPUT -o lo -j ACCEPT 
[0:0] -A OUTPUT -s 224.0.0.0/255.0.0.0 -j DROP 
[12:1814] -A OUTPUT -d 224.0.0.0/255.0.0.0 -j DROP 
[0:0] -A OUTPUT -s 255.255.255.255 -j DROP 
[0:0] -A OUTPUT -d 0.0.0.0 -j DROP 
[0:0] -A OUTPUT -m state --state INVALID -j DROP 
[13357:4068872] -A OUTPUT -o wlan0 -j OUTBOUND 
[0:0] -A OUTPUT -j LOG_FILTER 
[0:0] -A OUTPUT -j LOG --log-prefix "Unknown Output" --log-level 6 
[9609:6781668] -A INBOUND -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT 
[1180:224109] -A INBOUND -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT 
[128:34380] -A INBOUND -j LSI 
[128:34380] -A LSI -j LOG_FILTER 
[0:0] -A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6 
[0:0] -A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -j DROP 
[0:0] -A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK RST -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6 
[0:0] -A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK RST -j DROP 
[0:0] -A LSI -p icmp -m icmp --icmp-type 8 -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6 
[0:0] -A LSI -p icmp -m icmp --icmp-type 8 -j DROP 
[85:19040] -A LSI -m limit --limit 5/sec -j LOG --log-prefix "Inbound " --log-level 6 
[128:34380] -A LSI -j DROP 
[0:0] -A LSO -j LOG_FILTER 
[0:0] -A LSO -m limit --limit 5/sec -j LOG --log-prefix "Outbound " --log-level 6 
[0:0] -A LSO -j REJECT --reject-with icmp-port-unreachable 
[0:0] -A OUTBOUND -p icmp -j ACCEPT 
[10295:3833025] -A OUTBOUND -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT 
[289:28773] -A OUTBOUND -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT 
[2773:207074] -A OUTBOUND -j ACCEPT 
COMMIT
# Completed on Sat Feb 16 19:49:21 2008
```

I've got Firestarter installed, but AFAIK it's not running.

---

### Post by The Cog on 2008-02-17
Your firewall has no rules for dealing with interface tun0. Your own firewall is blocking the outgoing pings. It would also block pretty-much anything coming back in over the tunnel too.

Turning off your firewall shoudl prove the point. 
Manually running these two lines should (if I got it right) allow your VPN the same rights as you allow your wireless connection, but you really need to address your firewall configuratiion and get that corrected.```

sudo iptables -I INPUT 16 -i tun0 -j INBOUND
sudo iptables -I OUTPUT 12 -o tun0 -j OUTBOUND

```

---

