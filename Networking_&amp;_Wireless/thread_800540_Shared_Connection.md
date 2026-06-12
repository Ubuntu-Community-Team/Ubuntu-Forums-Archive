---
title: "Shared Connection"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by Rayne7 on 2008-05-19
I've been using Ubuntu for a bit now, and am quite liking Hardy. However, a friend of mine showed me he can share internet he is getting from a cable via a ad-hoc wireless network from his computer. I know Linux can do this, but I haven't found out how... It is really bothering me that I can do something in Windows and not in Linux, especially when it comes to networking. I have tried the tutorials found in numerous other threads, and tried Firestarter. None of them work, I have gotten it to create the ad-hoc network, and can connect to it, but no shared connection to the internet as of yet. Ideas? What configs do you need me to post?

---

### Post by helgman on 2008-05-20
If you've got the wireless working you should now look into IP forwarding (there should be a bunch of Linux guides out there). Have you tried this?

Regards,
Helgman

---

### Post by AnRa on 2008-05-20
You should search about NAT (Network Address Translation). Quick way: [http://ubuntuforums.org/showpost.php?p=2456624&postcount=5](http://ubuntuforums.org/showpost.php?p=2456624&postcount=5)

---

### Post by Rayne7 on 2008-05-20
Tried those, and neither works. After trying that, the internet shuts down on this computer while the wireless is active. No internet on either.

[PHP]lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"blahblah"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.427 GHz  Cell: 36:B6:28:93:1A:E9   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/PHP]

eth0 is the hardline, wlan0 is the wireless

---

### Post by Rayne7 on 2008-05-20
I also now have a process called 'ksoftirqd/0' that is using all of CPU1. What is that? I looked it up and it referenced to a problem with iptables... I have a feeling my iptables is all fubar-ed.

---

### Post by Rayne7 on 2008-05-20
Bump


Anyone? Fixed the wierd issue with CPU being taken up, just restarted. Still no shared internet though.

---

### Post by helgman on 2008-05-20
So you have investigated both IP forward and NAT/PAT?

What is your setup (addresses etc) and how have you tried to fix it?

Regards,
Helgman

---

### Post by Rayne7 on 2008-05-20
I've tried the methods described above and others in the Ubuntu tutorials on setting up a shared internet. As well as Firestarter. 

Internet comes in on a static IP from a hardline (eth0) say: 192.168.1.10, 255.255.255.0, 192.168.1.1

Trying to use ad-hoc created by wifi (wlan0) to use DHCP with those who connect and use the shared internet. Tried using a static here as well, but no luck.

---

### Post by Rayne7 on 2008-05-20
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
exit

tried that one


sudo iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE 
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

and that one for example

Often times, i end up with the hardline no longer working on the host computer... very frustrating

---

### Post by lisati on 2008-05-20
For a while I connected my laptop to my desktop via wireless in order to share the desktop's internet connection, but gave up on that because apart from the need for having the desktop switched on, the laptop was unable to reliably access the internet when the desktop was busy (e.g. when rendering a video file). I eventually solved it by purchasing a wireless router that accessed my DSL modem directly via a dedicated ethernet port, my desktop by a regular ethernet port, and my laptop by wireless. Perhaps something similar might be worthwhile if your budget permits....

---

### Post by helgman on 2008-05-20
Right ...

I'm gonna do a test here (and document it right in this post). The setup is simple (if I get everything working). I've got a laptop (COMP A) connected to the Internet (the one I'm writing on) via an Ethernet cable (network 192.168.1.0/24) and the same laptop has a wireless card that I will use for the Ad-hoc network (10.0.0.0/8). I then have a second laptop (COMP B) that I will try to get connected to the Internet via the Ad-hoc network.

COMP A (Intel Corporation PRO/Wireless 2200BG Network Connection):
```
iwconfig eth1 mode ad-hoc
iwconfig eth1 essid "TestAdHoc"
iwconfig eth1 channel 10
ifconfig eth1 10.0.0.1
```

COMP B (Atheros Communications, Inc. AR5413 802.11abg NIC):
```
ifconfig ath0 down
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode adhoc
iwpriv ath0 mode 3 # set is to use 802.11G (used A by default)
iwconfig ath0 essid "TestAdHoc"
ifconfig ath0 10.0.0.100
```

Successful ping both ways.

COMP A:
```
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

COMP B:
```
route add default gw 10.0.0.1
ping www.google.com

PING www.l.google.com (66.249.93.99) 56(84) bytes of data.
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=1 ttl=241 time=43.2 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=2 ttl=241 time=41.3 ms
```

And tshark on COMP A verifies that the connection uses PAT:
```
  0.009762 192.168.1.12 -> 66.249.93.99 ICMP Echo (ping) request
  0.048173 66.249.93.99 -> 192.168.1.12 ICMP Echo (ping) reply
```

Regards,
Helgman

---

### Post by Rayne7 on 2008-05-20
That is an easier solution, however I can do this in windows... and it bothers me that I can in linux. Kinda got a bet running with my buddy that I can do it in linux...

---

### Post by Rayne7 on 2008-05-20
Comp B in my case is running Windows XP. Not sure if that seriously effects anything.

---

### Post by helgman on 2008-05-20
> **Rayne7 said:**
> Comp B in my case is running Windows XP. Not sure if that seriously effects anything.

I don't have a computer running XP so I can't try it but it shouldn't be a problem. Just make sure to get the gateway and the DNS-server in the configuration.

As for connecting to the network ... that all depends on what client the computer is using.

Regards,
Helgman

---

### Post by Rayne7 on 2008-05-20
Okay, I got the client computer with the same gateway and dns numbers as the host, and got the ip set as you did... trying

---

### Post by Rayne7 on 2008-05-20
Okay, when I force a static IP, the XP crapper wont connect. Is 10.0.0.100 always going to be the ip the client should use? Or is there a way to tell what the host is expecting?

---

### Post by helgman on 2008-05-20
> **Rayne7 said:**
> Okay, I got the client computer with the same gateway and dns numbers as the host, and got the ip set as you did... trying

Just want to make sure I don't misunderstand you cause if I don't then you misunderstand me, sort of ...

The gateway on COMP B should be COMP A, nothing else. The gateway is used as a means for the computer to know where on the local network it should send packages destined elsewhere. So COMP B should have the IP address of COMP A as it's default gateway, nothing else. And then you should use the same DNS server on both hosts.

Just want to make that clear.

Regards,
Helgman

---

### Post by helgman on 2008-05-20
> **Rayne7 said:**
> Okay, when I force a static IP, the XP crapper wont connect. Is 10.0.0.100 always going to be the ip the client should use? Or is there a way to tell what the host is expecting?

The host should not be expecting anything, it should gladly take whatever it is given. Depending on how match time you are willing to spend you can always set up a DHCP server on COMP A ... I wouldn't do it, but it's one way of easing the pain I guess.

When you say it won't connect ... it won't connect to the wireless network, it won't accept the IP address or it won't communicate? Also make sure to get the subnets right. The usually default to "the default" subnet mask, so for 10.0.0.0 it's 255.0.0.0. Both computers should have the same setup there.

If you use the default subnet mask the COMP B can use any address between 10.0.0.2 and 10.255.255.254 as long as no other computer is using it.

Regards,
Helgman

---

### Post by Rayne7 on 2008-05-20
> **helgman said:**
> The host should not be expecting anything, it should gladly take whatever it is given. Depending on how match time you are willing to spend you can always set up a DHCP server on COMP A ... I wouldn't do it, but it's one way of easing the pain I guess.

When you say it won't connect ... it won't connect to the wireless network, it won't accept the IP address or it won't communicate? Also make sure to get the subnets right. The usually default to "the default" subnet mask, so for 10.0.0.0 it's 255.0.0.0. Both computers should have the same setup there.

If you use the default subnet mask the COMP B can use any address between 10.0.0.2 and 10.255.255.254 as long as no other computer is using it.

Regards,
Helgman

It spends a long time "connecting" to the network. Then just says "Not Connected" to the network that I selected for it. But still has a "disconnect" button.

---

### Post by Rayne7 on 2008-05-20
oh, in XP, I configured the wireless connection TCp/IP properties as following:

IP: 10.0.0.100
Subnet: 255.0.0.0
Default Gateway: 10.0.0.1

DNS

(set to same as host)

---

### Post by helgman on 2008-05-20
[Here](http://www.microsoft.com/windowsxp/using/networking/setup/adhoc.mspx#3) is the Microsoft guide for connecting a computer (XP) to an Ad Hoc network, don't know if it helps.

The IP settings looks good.

You said you had it working before (the Ad Hoc part), what is different now from last time?

Regards,
Helgman

PS I won't reply for some time now, but I'll be back in a couple of hours DS

---

### Post by Rayne7 on 2008-05-21
I can connect to the ad-hoc, that isnt an issue. The problem is the internet is not getting passed on to the XP computer. Before I did not define a set IP and let the computer handle it (must be DHCP I guess).

---

### Post by helgman on 2008-05-21
Ok ...

Just to make sure that every setting is where it is supposed to be post the following:

COMP A:
```
ifconfig
iwconfig
cat /proc/sys/net/ipv4/ip_forwardit
iptables --verbose --list
iptables --verbose --list --table nat
ping <IP of COMP B>
```

COMP B:
```
ipconfig /all
ping <IP of COMP A>
tracert <66.249.93.99>
nslookup www.google.com
```

In Vista there is a wlan "extension" to netsh but I'm not sure that it's built into XP ... you could try *netsh wlan show all* and print the output if you feel like it. I've heard that SP 3 have some stuff packed over from Vista but I don't think the wlan part of netsh is one of them (can't find any information about that).

Let's just take if from there,
Helgman

---

### Post by AnRa on 2008-05-21
> **Rayne7 said:**
> iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
exitYou should replace [FONT="Courier New"]ppp0[/FONT] for [FONT="Courier New"]eth0[/FONT], and don't forget about "[FONT="Courier New"]sudo -i[/FONT]" first. It's also worth noting that this would work until you reboot the PC.

---

### Post by Rayne7 on 2008-05-21
For these I did not specify the IP, I let it do its own thing to establish the ad-hoc connection.


**_COMP A_**

ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:38:97:4b  
          inet addr:192.168.1.116  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe38:974b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1805546 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1659086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:989581182 (943.7 MB)  TX bytes:621114678 (592.3 MB)
          Interrupt:251 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13978 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13978 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:531509 (519.0 KB)  TX bytes:531509 (519.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:4a:d5:4f  
          inet6 addr: fe80::21f:3bff:fe4a:d54f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:576 (576.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3B-4A-D5-4F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig


```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"tester"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.457 GHz  Cell: F2:D7:CA:33:1C:62   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:0123-45
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

cat /proc/sys/net/ipv4/ip_forward
```
1
```

iptables --verbose --list
```

Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
13977  531K ACCEPT     all  --  lo     any     anywhere             anywhere            
    0     0 LOG        all  --  !lo    any     127.0.0.0/8          anywhere            LOG level warning 
    0     0 DROP       all  --  !lo    any     127.0.0.0/8          anywhere            
  469 20323 ACCEPT     all  --  eth0   any     anywhere             255.255.255.255     
1697K  947M ACCEPT     all  --  eth0   any     anywhere             192.168.1.116       
21544 6170K ACCEPT     all  --  eth0   any     anywhere             192.168.1.255       
  490 15676 DROP       all  --  any    any     anywhere             ALL-SYSTEMS.MCAST.NET 
  816  127K LOG        all  --  any    any     anywhere             anywhere            LOG level warning 
  816  127K DROP       all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  any    any     anywhere             ALL-SYSTEMS.MCAST.NET 
    0     0 LOG        all  --  any    any     anywhere             anywhere            LOG level warning 
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
13977  531K ACCEPT     all  --  any    lo      anywhere             anywhere            
    0     0 ACCEPT     all  --  any    eth0    anywhere             255.255.255.255     
1660K  593M ACCEPT     all  --  any    eth0    192.168.1.116        anywhere            
    0     0 ACCEPT     all  --  any    eth0    192.168.1.255        anywhere            
    0     0 DROP       all  --  any    any     anywhere             ALL-SYSTEMS.MCAST.NET 
    0     0 LOG        all  --  any    any     anywhere             anywhere            LOG level warning 
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain INBOUND (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 LSI        all  --  any    any     anywhere             anywhere            

Chain LOG_FILTER (2 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  any    any     anywhere             anywhere            
    0     0 LOG        tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
    0     0 DROP       tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
    0     0 LOG        tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
    0     0 DROP       tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
    0     0 LOG        icmp --  any    any     anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
    0     0 DROP       icmp --  any    any     anywhere             anywhere            icmp echo-request 
    0     0 LOG        all  --  any    any     anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  any    any     anywhere             anywhere            
    0     0 LOG        all  --  any    any     anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
    0     0 REJECT     all  --  any    any     anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     all  --  any    any     anywhere             anywhere            

```

iptables --verbose --list --table nat
```
Chain PREROUTING (policy ACCEPT 8107 packets, 1122K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 51147 packets, 2278K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 51147 packets, 2278K bytes)
 pkts bytes target     prot opt in     out     source               destination         

```

ping 169.254.22.142
```
PING 169.254.22.142 (169.254.22.142) 56(84) bytes of data.
From 192.168.1.116 icmp_seq=1 Destination Host Unreachable
From 192.168.1.116 icmp_seq=2 Destination Host Unreachable
From 192.168.1.116 icmp_seq=3 Destination Host Unreachable
From 192.168.1.116 icmp_seq=4 Destination Host Unreachable
From 192.168.1.116 icmp_seq=5 Destination Host Unreachable
From 192.168.1.116 icmp_seq=6 Destination Host Unreachable
From 192.168.1.116 icmp_seq=7 Destination Host Unreachable
From 192.168.1.116 icmp_seq=8 Destination Host Unreachable
From 192.168.1.116 icmp_seq=9 Destination Host Unreachable
From 192.168.1.116 icmp_seq=10 Destination Host Unreachable

```

**_COMP B_**

ipconfig /all
```
Windows IP Configuration
Host Name: Hoe
Primary DNS Suffix:
Node Type: Mixed
IP Routing Enabled: No
WINS Proxy Enabled: No

Ethernet adapet Wireless Network Connection:

Connection-specific DNS suffix:
Description: Intel(R) PRO/Wireless 3945ABG Network Connection
Physical Address: 00-13-02-A8-00-D6
DHCP Enabled: Yes
Autoconfiguration Enabled: Yes
Autoconfiguration IP Address: 169.254.22.142
Subnet Mask: 255.255.0.0
Default Gateweay: 169.254.22.142

Ethernet adapted Local Area Connection:

Media State: media disconnected
Description: Intel(R) PRO/100 VM Network Connection
Physical Address: 00-16-D4-26-85-1D

```

Cant seem to find IP for wlan0 for COMP A

tracert (66.249.93.99)
```
Unable to resolve target system name (66.249.93.99).
```

nslookup [www.google.com](www.google.com)
```
*** Default servers are not available
Server: Unkown
Address: 127.0.0.1

*** UKnown can't find www.google.com: No response from server
```

---

### Post by helgman on 2008-05-21
OK ... they are not making there own thing so they won't be able to connect. The wireless card on COMP A most be in the same network as the wireless on COMP B. The wireless on COMP A don't have an IP address and the one on COMP B has one that it's given automatically when it's not configured to use any and can't find a DHCP server.

I also see that you don't have any output from the *iptables --verbose --list --table nat* command ... there should be a line saying something like:
```
 pkts bytes target     prot opt in     out     source               destination         
  434 23029 MASQUERADE  all  --  any    eth0    anywhere             anywhere
```
Also make sure to have the wireless network configured before you do anything else (make sure COMP B can ping COMP A).

Regards,
Helgman

---

### Post by Rayne7 on 2008-05-21
Okay I got this output now:

```
Chain POSTROUTING (policy ACCEPT 55613 packets, 2476K bytes)
 pkts bytes target     prot opt in     out     source               destination         
21565  952K MASQUERADE  all  --  any    eth0    anywhere             anywhere            

```

And I can get COMP B to "Connect" with 10.0.0.100 and everything, using static IPs... but the damn things still cant ping each other. COMP A gives me this response:

```
ping: sendmsg: Operation not permitted

```

---

### Post by helgman on 2008-05-22
> **Rayne7 said:**
> And I can get COMP B to "Connect" with 10.0.0.100 and everything, using static IPs... but the damn things still cant ping each other. COMP A gives me this response:

```
ping: sendmsg: Operation not permitted

```

In the post where you gave the output of ifconfig (COMP A) wlan0 didn't have an IP address, and per the previous configuration wlan0 should have an IP address of 10.0.0.1 with a subnet mask of 255.0.0.0 (default).

Regards,
Helgman

---

