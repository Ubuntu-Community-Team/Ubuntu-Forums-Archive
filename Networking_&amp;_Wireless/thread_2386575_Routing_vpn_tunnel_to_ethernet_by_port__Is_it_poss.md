---
title: "Routing vpn tunnel to ethernet by port ? Is it possible?"
date: 2018-03-07
forum: Networking &amp; Wireless
---

### Post by fxdave on 2018-03-07
Hi! I have got an openVPN. Its interface is ***tun0***. I have got an Ethernet interface too (***enp2s0***).

My computer is connected to a proxy via ***enp2s0***,  which allows these ports: 
20
80
88
443
1863
5190
5222
5223
6891
6892
6893
6894
6895
6896
6897
6898
6899
6900
6901
8000
8080
8081
8991
8992
25000
32400

These are working fine, so I don't want to use VPN for these ports cause VPN is much slower.
When I connect to VPN all the traffic will go to ***tun0. ***
So how can I implement a firewall, that forward the traffic that uses that port is listed above, to the ethernet interface (***enp2s0***[I]).

I am very newby on networking.
[/I]I'd appreciate any help.
David

---

### Post by TheFu on 2018-03-07
You can control routing based on IPs.  Source or target.

I use both openvpn and an ssh-proxy (SOCKS) from time to time.  The openvpn connection takes priority.  Both are used to access parts of my internal LAN.  ssh is used for only web traffic, but if I need more, then I'll bring up openvpn.  That seldom happens.

---

### Post by fxdave on 2018-03-07
The most of the time I don't know which ip addresses will I use.

---

### Post by TheFu on 2018-03-07
> **fxdave said:**
> The most of the time I don't know which ip addresses will I use.

That's what scripting is for, but certainly you'll know either the server or client IP.

---

### Post by The Cog on 2018-03-07
First, create a new routing table with a default route via your normal enp2s0 gateway (I used 192.168.0.254 in my example). This table won't actually be used by anything yet.
I used table number 100 but that's an arbitrary choice:
```
sudo ip route add default via 192.168.0.254 table 100
```
Then add a routing rule that says any packets marked with firewall mark 200 (another arbitrary choice) should use table 100 as its routing table. So any marked packets will go via the enp2s0 gateway:
```
ip rule add fwmark 200 table 100
```
Now use iptables firewall rules to mark the packets you want to route via enp2s0 with mark 200
```
iptables -A OUTPUT -t mangle -p tcp --dport 20 -j MARK --set-mark 200
iptables -A OUTPUT -t mangle -p tcp --dport 80 -j MARK --set-mark 200
iptables -A OUTPUT -t mangle -p tcp --dport 88 -j MARK --set-mark 200
etc...
```
EDIT: My post originally said -A PREROUTING -i eth0. Have corrected that to -A OUTPUT. 

My reference: [http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.netfilter.html](http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.netfilter.html)

---

### Post by fxdave on 2018-03-07
Thank you, but I can't make it to work.

First I connected to the VPN.
I set these:
sudo ip route add default via 10.0.0.1 table 100
sudo ip rule add fwmark 200 table 100
sudo iptables -A PREROUTING -i enp2s0 -t mangle -p tcp --dport 80 -j MARK --set-mark 200
sudo iptables -A PREROUTING -i enp2s0 -t mangle -p tcp --dport 443 -j MARK --set-mark 200

I tried with wget [www.google.hu]("http://www.google.hu") , but this still wants to go via VPN.

Some other information about the config:
before the VPN connection:
**sudo ip route**
default via 10.0.0.1 dev enp2s0  proto static  metric 100 
10.0.0.0/16 dev enp2s0  proto kernel  scope link  src 10.0.1.14  metric 100 
169.254.0.0/16 dev enp2s0  scope link  metric 1000 

after the VPN connection:
**sudo ip route**
default via 10.8.0.1 dev tun0  proto static  metric 50 
default via 10.0.0.1 dev enp2s0  proto static  metric 100 
10.0.0.0/16 dev enp2s0  proto kernel  scope link  src 10.0.1.14  metric 100 
10.8.0.0/24 dev tun0  proto kernel  scope link  src 10.8.0.2  metric 50 
37.221.213.72 dev tun0  proto static  scope link  metric 50 
64.233.167.16 dev tun0  proto static  scope link  metric 50 
74.125.206.16 dev tun0  proto static  scope link  metric 50 
80.249.168.94 dev tun0  proto static  scope link  metric 50 
169.254.0.0/16 dev enp2s0  scope link  metric 1000 
172.217.18.69 dev tun0  proto static  scope link  metric 50 
193.6.40.55 via 10.0.0.1 dev enp2s0  proto static  metric 100

---

### Post by The Cog on 2018-03-08
I messed up my first post, sorry. It should be the OUTPUT chain and not the PREROUTING chain, and should not have been checking the incoming interface. I tested a line from the article I linked, and fixed up my commands. But then when posting, I was a little distracted (x-files on tv) and copy/pasted the article commands rather than the modified ones by mistake. Sorry again. I have corrected my previous post now.

You will be able to see the count of [packets:bytes] that have been marked with the command "sudo iptables-save -t mangle -c".

---

### Post by fxdave on 2018-03-08
It does the same.[B]

sudo iptables -L -t mangle[/B]
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
MARK       tcp  --  anywhere             anywhere             tcp dpt:http MARK set 0xc8
MARK       tcp  --  anywhere             anywhere             tcp dpt:http MARK set 0xc8
MARK       tcp  --  anywhere             anywhere             tcp dpt:https MARK set 0xc8

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination

---

### Post by The Cog on 2018-03-08
Can you post the output of ```
sudo iptables-save -t mangle -c
``` please?

---

### Post by fxdave on 2018-03-08
Of course

```

# Generated by iptables-save v1.6.0 on Fri Mar  9 00:21:56 2018
*mangle
:PREROUTING ACCEPT [126585:147294605]
:INPUT ACCEPT [114222:146636673]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [85521:109227406]
:POSTROUTING ACCEPT [85539:109230055]
[1121:265153] -A OUTPUT -p tcp -m tcp --dport 80 -j MARK --set-xmark 0xc8/0xffffffff
[1121:265153] -A OUTPUT -p tcp -m tcp --dport 80 -j MARK --set-xmark 0xc8/0xffffffff
[2821:571638] -A OUTPUT -p tcp -m tcp --dport 443 -j MARK --set-xmark 0xc8/0xffffffff
COMMIT
# Completed on Fri Mar  9 00:21:56 2018

```

---

### Post by The Cog on 2018-03-10
Sorry for the delay in replying. 

I have set up as close as I can to your setup and found that althought the routing works, the PC tends to use the wrong source address so for instance it will use the source address of its tunnel interface when the routing rules are guiding the packets directly to the physical interface. That very likely won't work at all. If it did (i.e. no NAT anywhere) then the return path would be via the VPN which is not what you want. I found that this additional iptables rule corrected that by ensuring that packets leaving the physical interface use the physical interface's address:
```
iptables -t nat -A POSTROUTING -o enp2s0 -j MASQUERADE
```

---

### Post by fxdave on 2018-03-14
I am sorry too. I was trying to understand, why it isn't working, and why it should.
I found something about MASQUERADE: 
"It is an algorithm dependant on the iptables implementation that allows  one to route traffic without disrupting the original traffic."
( source: [https://askubuntu.com/questions/466445/what-is-masquerade-in-the-context-of-iptables](https://askubuntu.com/questions/466445/what-is-masquerade-in-the-context-of-iptables) )

That's interesting because it says I will use both the tunnel and the ethernet too.
What happens if I issue the wget [www.google.hu](www.google.hu).
As I think, The packets with the proxy information will go to the tun0, and enp2s0 too.
The tun0 interface will respond an error message so that It can't connect to the proxy server.
But what about the incoming traffic from the ethernet?

---

### Post by The Cog on 2018-03-14
It seems that I don't fully understand your setup. I thought that you wanted the ports listed (20, 80...) to connect out via the ethernet, and other ports to connect out via the VPN tunnel. 

Masquerade is something that does address translation. It ensures that all packets leaving the masquerading interface use the address of that interface as their source address - using address translation if necessary. So that connections that use tun0's address as their source but that get redirected out via enp2s0 end up using enp2s0's address as their source. This is necessary to ensure that the reply packets return to enp2s0 rather than taking a completely different path and arriving back at the tun0 interface (which probably wouldn't work due to firewalls or NAT elsewhere in the network).

I'm not sure what a proxy has to do with this. If you mean that your browser is using a proxy, then I would expect the browser's connection to the proxy to be subject to that port list and routing - which way the connection to the proxy goes depends on which port the connection to the proxy uses.

Incoming traffic from the internet is problematic. Replies to your outgoing connections should be OK, but you can't easily control which address/port pair incoming connections will choose to connect to. The only way to be able to handle incoming connections reliably would be if both the tun0 and enp2s0 addresses were public addresses. In that case you would not need the masquerade to fix up the address, but you would have no control over which path the incoming packets took, or at least, you would not be able to tell the internet to route some ports along one path and some ports along the other path. Using masquerade, you essentially choose the path by choosing which of two addresses the connection is using.

---

### Post by fxdave on 2018-03-19
I think you understood correctly my setup.

I have got HTTP proxy setting.
If I am connecting through VPN then the proxy setting will be a barrel to the traffic.
And that is what I saw when I was trying to reach google.hu.

```

wget www.google.hu
--2018-03-19 22:17:16--  http://www.google.hu/
Resolving proxy.something.hu (proxy.something.hu)... failed: Name or service not known.
wget: unable to resolve host address &#8216;proxy.something.hu&#8217;

```

On the other hand, I don't want to use VPN for HTTP.
I have got no idea why is it going via VPN if I have set up those rules that you gave me.
Isn't it needed to turn something on? Or is it automatically?

If it would go to Ethernet then should be something like:
```

--2018-03-19 22:21:15--  http://www.google.hu/
Resolving proxy.something.hu (proxy.something.hu)... 193.6.40.1, 193.6.40.55
Connecting to proxy.something.hu (proxy.something.hu)|193.6.40.1|:3128... connected.
Proxy request sent, awaiting response... 200 OK

```

---

