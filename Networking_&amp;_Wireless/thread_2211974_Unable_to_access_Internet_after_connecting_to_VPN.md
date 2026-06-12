---
title: "Unable to access Internet after connecting to VPN"
date: 2014-03-18
forum: Networking &amp; Wireless
---

### Post by cadogenwest on 2014-03-18
Searching the forums discovers similar issues, but each are too unique to be applied in a genral scenario. My vpn provider, *vpnbook*, is setup on Xubuntu 13.04. I have downloaded the openvpn files (zip) and tried it out by doing:
```
sudo openvpn --config <downloadedFile.ovpn>
```

It asks for username and password which when entered proceeds to  connect, makes changes to the routing table and establishes a tunnel. At  this point Internet becomes inaccessible and no IPs could be resolved  anymore. So, I've terminated the vpn connection and connected to the  internet again; things went back to normal. After learning from the very  insightful posts here, I have disabled (and finally removed) my  firewall config tool *ufw*. Checked if there were any other  firewalls still running (apart from the one built in to the kernel), and  flushed all such settings from the iptables.

[COLOR=#008080][I]Note: Mine is a cable modem and thereby not a  router. My ISP has a keep-alive login page that connects me to the  internet. I mentioned it here because if I am able to manage this  current issue, this ISP-login-destination needs to be separately added  to the table through its default gateway (not through the tunnel).

[/I][/COLOR]So here's my routing table before establishing the vpn:```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         116.68.108.1    0.0.0.0         UG    0      0        0 eth0
116.68.108.0    0.0.0.0         255.255.252.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
```

And afterwards:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.10.0.189     128.0.0.0       UG    0      0        0 tun2
0.0.0.0         116.68.108.1    0.0.0.0         UG    0      0        0 eth0
10.10.0.1       10.10.0.189     255.255.255.255 UGH   0      0        0 tun2
10.10.0.189     0.0.0.0         255.255.255.255 UH    0      0        0 tun2
46.23.68.180    116.68.108.1    255.255.255.255 UGH   0      0        0 eth0
116.68.108.0    0.0.0.0         255.255.252.0   U     1      0        0 eth0
128.0.0.0       10.10.0.189     128.0.0.0       UG    0      0        0 tun2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
```

And the results of [COLOR=#ff8c00]ifconfig eth0[/COLOR] to get the settings applied to the network adapter after the vpn is established.
```
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:b9:94:43  
          inet addr:116.68.110.181  Bcast:116.68.111.255  Mask:255.255.252.0
          inet6 addr: fe80::beae:c5ff:feb9:9443/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24812465 (24.8 MB)  TX bytes:2515058 (2.5 MB)
```

I have had the same issue with many free vpns. I have recently tried a paid service to check the same thing, but much to my surprise, it worked!. After comparing the routing table in both cases, I couldn't notice any difference whatsoever. I don't have a windows PC to test these on. Please ask me if any further information needs to be provided. I have also tried pinging the vpn server, google server etc after connecting to the vpn; it just gave nothing - just a blank line awaiting to resolve host.

---

### Post by ant2ne on 2014-03-18
I notice that on my VPN after establishing a connection I have another interface. Try "ifconfig" instead of "ifconfig eth0".

Also, an 169 address is a self assigned address. And if memory serves me, it isn't a routable address. google up on APIPA. How are you getting that routing address/network?

This> 
0.0.0.0         10.10.0.189     128.0.0.0       UG    0      0        0 tun2
0.0.0.0         116.68.108.1    0.0.0.0         UG    0      0        0 eth0Says you have 2 default gateways. And that 10. has a REAL weird netmask. Who owns the 10. network?

---

### Post by cadogenwest on 2014-03-18
The 10. everything is setup by the vpn. The 169 address is assigned  automatically by the ISP as soon as the modem is turned on. My ISP might  be doing this since they are very *windows* oriented (and APIPA  seems to be a windows feature). Those 2 defaults are there because this  vpn doesn't remove the previous default. I manually remove them usually,  incase the vpn fails and everything falls back to the previous default.

Here's the [COLOR=#008080]ifconfig[/COLOR] after vpn is connected
```

eth0      Link encap:Ethernet  HWaddr bc:ae:c5:b9:94:43  
          inet addr:116.68.110.181  Bcast:116.68.111.255  Mask:255.255.252.0
          inet6 addr: fe80::beae:c5ff:feb9:9443/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:317017 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:465046093 (465.0 MB)  TX bytes:13172241 (13.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:690 errors:0 dropped:0 overruns:0 frame:0
          TX packets:690 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68532 (68.5 KB)  TX bytes:68532 (68.5 KB)

tun2      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.10.0.22  P-t-P:10.10.0.21  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:372 (372.0 B)

```

---

### Post by bashiergui on 2014-03-18
Does the ISP require a password to join the internet? I'm leaning towards "yes" because you probably get the 169.254 address (which isn't publicly routable) when you don't authenticate.

---

### Post by cadogenwest on 2014-03-19
Yes, it does. This login server comes under another IP though. So I'm not directly contacting their main server. I guess they are activating the internet by assigning the cable modem mac address an 'ok to connect' status after I login.

---

### Post by ant2ne on 2014-03-19
> Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.10.0.189     128.0.0.0       UG    0      0        0 tun2This genmask doesn't look right to me.

> inet addr:10.10.0.22  P-t-P:10.10.0.21  Mask:255.255.255.255I'm no VPN expert, but this netmask doesn't look right either. This means that if I'm not communicating with myself then send it out the default gateway.

---

### Post by cadogenwest on 2014-03-19
Then it must be a problem with the vpn configuring itself, right? Is it possible to manually change them?

---

### Post by ant2ne on 2014-03-19
Only if you knew what it was supposed to be.

---

### Post by cadogenwest on 2014-03-19
I've just tried another vpn and this time only google works! So strange :confused:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         173.0.10.1      0.0.0.0         UG    0      0        0 tun0
116.68.108.0    0.0.0.0         255.255.252.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
173.0.10.0      0.0.0.0         255.255.255.0   U     0      0        0 tun0
173.0.14.249    116.68.108.1    255.255.255.255 UGH   0      0        0 eth0


eth0      Link encap:Ethernet  HWaddr bc:ae:c5:b9:94:43  
          inet addr:116.68.111.116  Bcast:116.68.111.255  Mask:255.255.252.0
          inet6 addr: fe80::beae:c5ff:feb9:9443/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37462360 (37.4 MB)  TX bytes:3188813 (3.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104843 (104.8 KB)  TX bytes:104843 (104.8 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:173.0.10.203  P-t-P:173.0.10.203  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1860007 (1.8 MB)  TX bytes:374756 (374.7 KB)

```

---

### Post by ant2ne on 2014-03-19
That all looks much better.

---

### Post by cadogenwest on 2014-03-19
But why only google? I can't access any other sites. Is this a common issue?

---

### Post by varunendra on 2014-03-21
DISCLAIMER : I have zero practical, and almost zero theoretical experience with VPN, so please pardon stupid assumptions/comments if any.

> **cadogenwest said:**
> ```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
**0.0.0.0         173.0.10.1      0.0.0.0         UG    0      0        0 [COLOR="#FF0000"]tun0[/COLOR]** *[COLOR="#0000CD"]# Route to the internet[/COLOR]*
**[COLOR="#008000"]116.68.108.0    0.0.0.0         255.255.252.0   U     1      0        0 eth0[/COLOR]** *[COLOR="#0000CD"]# Route to local network[/COLOR]*
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
173.0.10.0      0.0.0.0         255.255.255.0   U     0      0        0 tun0
[COLOR="#B22222"]**173.0.14.249    116.68.108.1    255.255.255.255 UGH   0      0        0 eth0**[/COLOR] *[COLOR="#0000CD"]# Looks like the route to the VPN server to me[/COLOR]*

```
I don't know how to explain above, but this is what seems quite clear to me with respect to above routing table -

* All but local traffic is currently gatewayed through your VPN gateway, using the virtual interface "**[COLOR="#FF0000"]tun0[/COLOR]**". It means all your requests to connect to internet are sent to the VPN gateway.

* Considering the above, it is clearly your VPN who is deciding what you can or can't access.

Assuming you want to use the VPN to access only some specific resources, and need to access Internet normally (VPN not involved), please try this when the VPN is connected -

```
sudo route del default
sudo route add default gw 116.68.108.1 eth0
```
Can you browse the internet afterwards? Is the VPN still working what you needed it for?

If this is the situation you want, you may try making it permanent in Network Manager by clicking "Routes" button under "VPN > IPv4" tab, and checking both (or just one, if the other one is disabled) check-boxes to ensure the VPN connection is used only for "local resources", not as a route for Internet.

---

### Post by ant2ne on 2014-03-21
cadogenwest,
You can access the entire internet with the second VPN setup, right? It was only on the screwy one with the 10. network garbage that you couldn't. Right? 

varunendra,
No, do not remove your default route.

Red says for network 173.0.14.249 (which is a single IP) use router at 116.68.108.1. 
Green says for network 116.68.108.0 (which is where the above mentioned router lives) use default gateway
Black (bold) says I'm default route for all other unspecified below, use me. Which is the VPN tunnel.

So, suppose you wanted to contact 173.0.14.249, you'd use the router at 116.68.108.1. In order to contact that router you'd need to get routed to the default gateway of 173.0.10.1.

I think what you are seeing here is routing of all traffic to and form interface eth0 through tun0. I'm no VPN expert, but I bet 173.0.14.249 is an interface on the local host or its gateway or something like that.

---

### Post by varunendra on 2014-03-21
> **ant2ne said:**
> varunendra,
No, do not remove your default route.
If the intention is to reach the internet via the usual gateway (the one that was working before connecting to gateway), then Yes, the current default route needs to be deleted. Note that the second command then adds a new "default route", which would be the usual one using the usual (eth0) interface.

> Green says for network 116.68.108.0 (which is where the above mentioned router lives) use default gateway
In the present routing table, the "default gateway" is "173.0.10.1". Besides, the route in green does not have any gateway defined at all. All it has is a Network, a subnet (defining the network) and an interface name. So it just says - *"Use **eth0** to access **_anything_** on the network **116.68.108.0**"* - nothing more, nothing less.

> So, suppose you wanted to contact 173.0.14.249, you'd use the router at 116.68.108.1. In order to contact that router [COLOR="#FF0000"]you'd need to get routed to the default gateway of 173.0.10.1.[/COLOR]
Nope! The route to reach the (non-default) gateway 116.68.108.1 is already defined - the route in green. So that route, and therefore that interface (eth0) will be used, not the default gateway.

I don't know if this is what the OP wants, but I do know that deleting the current default route, then adding the previous one (before connecting to VPN) *should* let them connect to internet normally again.

What I'm not sure about is what they are using the VPN for, and if this is what they really want (to access internet via normal interface/route/gateway, and only some specific stuff over VPN).

---

### Post by ant2ne on 2014-03-21
> So it just says - "Use eth0 to access anything on the network 116.68.108.0" - Nope. 
> So that route, and therefore that interface (eth0) will be used, not the default gateway. Nope. The purpose to a routing table isn't to spew data out of an interface. **It has to know a router.** The purpose of the "use iface" section would be so that the system knows which wire* that network is on so it doesn't try to contact that router on the wrong interface. But it still needs to know the router.

I'm certain the routing table is read bottom up. The first match it has it will use that route. Ending with the default route.  For the Green you see the gateway specified as 0.0.0.0, We don't know 0.0.0.0 yet, but as we progress up the table we get to 0.0.0.0 which does **specify a router**.

I think you are on the right track in that the issue is with the default route. But if you remove the default route, and add back the other default route before connecting to the VPN (as you specified) you are right in that he will be using his original ISP as his default gateway router. But I think he will break his tunnel.

If I can remember I will check my routing stuff before and after tunneling when I get home tonight. Problem is, I brain dump when I get home and forget these things.

* in the event of eth0 eth1 routing - which is same concept here, sort of. Just abstracted with eth0 and tun0

---

### Post by varunendra on 2014-03-21
Since I haven't read such any explanations which are both authentic and clear about how routing tables are interpreted and implemented, I have neither a rock-solid confidence, nor any prejudice about my own interpretations of that.

How I explain these are purely my own assumptions/interpretations from what I have seen so far, and I admit I haven't seen much. :p

I'd be curious to see how it goes with the OP, because I know a few threads where the posters used VPN, while keeping their default gateway (the one that was created before connecting to VPN). I don't remember their routing table (if they posted at all), but it seems to me that this line in the case here -
```
173.0.10.0      0.0.0.0         255.255.255.0   U     0      0        0 tun0
```
..should be able to keep the tunnel communication.

I hope the OP is still with us and can further enlighten me with their feedback.

---

### Post by ant2ne on 2014-03-21
I'm not saying you are wrong. I'm saying your reasoning is wrong. :D  It could very well be the default gateway. I will have to check how my routing table changes when I connect to my VPN.

In my mind it makes sense for the tunnel to become the gateway for the tun0, But it should still need a default gateway for eth0 too.

---

### Post by ant2ne on 2014-03-21
google has IPs on the 173. and you have routing entries for 173. So that maybe why you can access google still. Although, that doesn't make much sense either.

---

### Post by bapoumba on 2014-03-21
Moved to Networking and Wireless.

---

### Post by ant2ne on 2014-03-21
BEFORE VPN
> ant2ne@ant2ne-desktop ~ $ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.1.1.1        0.0.0.0         UG    0      0        0 eth0
10.1.1.0        *               255.255.255.0   U     1      0        0 eth0

AFTER VPN
> ant2ne@ant2ne-desktop ~ $ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.16.0.69      0.0.0.0         UG    0      0        0 tun0
10.1.1.0        *               255.255.255.0   U     1      0        0 eth0
10.16.0.1       10.16.0.69      255.255.255.255 UGH   0      0        0 tun0
10.16.0.69      *               255.255.255.255 UH    0      0        0 tun0
host.colocrossi 10.1.1.1        255.255.255.255 UGH   0      0        0 eth0

Notice I'm not connected directly to the internet (modem, DSL) but I go through a router. So my routing table isn't as complicated.

---

### Post by varunendra on 2014-03-22
Would have been much more legible had it been within **'Code'** tags. :p

Hard to believe you need it, but you can find a quick 'HowTo' in my signature below if your really need it!

---

### Post by ant2ne on 2014-03-22
Was in a hurry.

---

### Post by cadogenwest on 2014-04-05
Sorry I couldn't reply to you folks' posts for the last couple of weeks. I have tried a new VPN (a paid one) and things worked out really well. To summarize the stuff that I was trying to do (and why I started this thread):
1. Route all traffic through the vpn tunnel
2. Except for one IP (my ISP login server)
3. My new vpn does not remove the default gateway that existed before tunneling.
4. I manually remove them from the routing table so that a vpn server fail won't cause cause the applications to default back to the previous one.
5. Some vpns only gives me access to a limited number of sites (google).
6. Now that I've paid for a service and they can do all these by simple config changes, I believe the matter is somewhat settled.

---

### Post by varunendra on 2014-04-05
Glad you got it sorted, and thanks for taking time to get back to us. :)

I think you should mark the thread as [SOLVED] now, using the "Thread Tools" link above the top post on this page.

---

