---
title: "Forward UDP to second LAN interface"
date: 2019-04-14
forum: Networking &amp; Wireless
---

### Post by patrick.f on 2019-04-14
hey,
i'm really struggling setting up my teamspeak config. First a short Network-Description:


Host #1
eth1: 10.10.2.33/24
Teamspeak 3: Listening UDP 9987


Host #2 (Ubuntu 16.04 LTS)
ens192: 10.10.2.41/24
ens224: 198.41.214.140 (obviously fake)


I can connect to 10.10.2.33 directly. Teamspeak wis running.
Now i do want to make the service public available, so offering the service on 198.41.214.140:9987


So this is about setting up the Proxy on Host #2.
What i've done so far:




detailed Network interfaces on Host #2
```

## LAN
auto ens192


#iface ens192 inet dhcp
iface ens192 inet static
  address   10.10.2.41
  netmask   255.255.255.0
  network   10.10.2.0
  broadcast 10.10.2.255
  gateway   10.10.2.1
  dns-nameservers 8.8.8.8




## WAN
auto ens224


iface ens224 inet static
  address   198.41.214.140
  netmask   255.255.255.192
  network   198.41.214.128
  broadcast 198.41.214.191
  dns-nameservers 8.8.8.8
  # WE CANT HAVE A SECOND GATEWAY. USE ROUTE INSTEAD




## ROUTING TABLES
##
up ip route add 10.10.2.0/24 dev ens192 table rt_lan
up ip route add default via 10.10.2.1 dev ens192 table rt_lan


up ip route add 198.41.214.128/26 dev ens224 table rt_wan
up ip route add default via 198.41.214.129 dev ens224 table rt_wan


## IP RULES
##
up ip rule add from 10.10.2.41/32 table rt_lan priority 100
up ip rule add from 198.41.214.140/32 table rt_wan priority 200


down ip rule del from 198.41.214.140/32 table rt_wan
down ip rule del from 10.10.2.41/32 table rt_lan

```


Ipv4 Forwarding is activated by:
/etc/sysctl.config
net.ipv4.ip_forward=1
```

$ cat /proc/sys/net/ipv4/ip_forward
1

```




Now i have set iptables NAT to Forward the pakets to Host #1.
```

sudo iptables -t nat -A PREROUTING -p udp --dport 9987 -j DNAT --to 10.10.2.33:9987
sudo iptables -t nat -A POSTROUTING -o ens192 -j MASQUERADE

```



Full ip-tables Setup:
```

$ sudo iptables -L -n -v --line-numbers
Chain INPUT (policy ACCEPT 1382 packets, 142K bytes)
num   pkts bytes target     prot opt in     out     source               destination


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
num   pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 651 packets, 81718 bytes)
num   pkts bytes target     prot opt in     out     source               destination

```


```

$ sudo iptables -L -n -v --line-numbers -t nat
Chain PREROUTING (policy ACCEPT 212 packets, 31327 bytes)
num   pkts bytes target     prot opt in     out     source               destination
1       93 12521 DNAT       udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:9987 to:10.10.2.33:9987


Chain INPUT (policy ACCEPT 154 packets, 22530 bytes)
num   pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 16 packets, 1097 bytes)
num   pkts bytes target     prot opt in     out     source               destination


Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
num   pkts bytes target     prot opt in     out     source               destination
1       20  1387 MASQUERADE  all  --  *      ens192  0.0.0.0/0            0.0.0.0/0

```




And now the Problem:
This does work if i connect to 10.10.2.41 with teamspeak. Then the traffic is forwarded to Host #1.
The MASQUERADE does enable the "return-path" and currently is just there to fully verfiy the functionality.




But it does NOT work, if i connect to 198.41.214.140.
Then the packets does NOT leave Host#2 on ens192 and no therefore no packets are received on Host#1. Tested by:


Host #2: tcpdump -v -i ens192 -n udp port 9987
Host #1: tcpdump -v -i eth1 -n udp port 9987

And now i'm stuck and really need some help/advice :)
Thanks in advance


Update to clarify:
* UDP Traffic hits Host #2 from the public ip (tcpdump)
* Nat rule is applied even on public ip access (iptables paket-count increases)
* udp connection between Host #1 and Host #2 works. (proxy on private lan works; nmap udp works)

---

### Post by The Cog on 2019-04-14
I suspect the problem is reverse path forwarding filter in host #2. I am hazy on how reverse path filter copes with having multiple policy routing tables - parhaps it only checks the default table?
Anyway, it may be worth turning rp_filter off and see if that helps.
[https://www.slashroot.in/linux-kernel-rpfilter-settings-reverse-path-filtering](https://www.slashroot.in/linux-kernel-rpfilter-settings-reverse-path-filtering)

BTW, it can be easier to see all the iptables config if you just run the command **sudo iptables-save** which will print all tables and rules in a format that you would use to re-enter them. You can add a -c flag to also print the counters for each line.

If above doesn't fix it, it may help to post the actual rules and tables, which you can get from these two commands:
```
ip ru
ip r l t all
```

Don't forget you can do **ip route get** to verify your rules and tables config. This may help debugging.

---

### Post by patrick.f on 2019-04-14
[s]Unfortunatly turning of Reverse Path Filtering didn't help.[/s]
But thanks for giving it a try. At least someting i didn't stumple accross until now


Thanks for the hint to better display all settings.
As a result for you 


```
$ sudo iptables-save
# Generated by iptables-save v1.6.0 on Sun Apr 14 14:24:18 2019
*raw
:PREROUTING ACCEPT [10580:1052656]
:OUTPUT ACCEPT [5734:2748388]
COMMIT
# Completed on Sun Apr 14 14:24:18 2019
# Generated by iptables-save v1.6.0 on Sun Apr 14 14:24:18 2019
*filter
:INPUT ACCEPT [3572:365844]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [2172:246585]
COMMIT
# Completed on Sun Apr 14 14:24:18 2019
# Generated by iptables-save v1.6.0 on Sun Apr 14 14:24:18 2019
*nat
:PREROUTING ACCEPT [232:35304]
:INPUT ACCEPT [169:25810]
:OUTPUT ACCEPT [2:152]
:POSTROUTING ACCEPT [0:0]
-A PREROUTING -p udp -m udp --dport 9987 -j DNAT --to-destination 10.10.2.33:9987
-A POSTROUTING -o ens192 -j MASQUERADE
COMMIT
# Completed on Sun Apr 14 14:24:18 2019

```


```
$ ip ru
0:      from all lookup local
100:    from 10.10.2.41 lookup rt_lan
200:    from 198.41.214.140 lookup rt_wan
32766:  from all lookup main
32767:  from all lookup default

```


```
$ ip r l t all
default via 10.10.2.1 dev ens192  table rt_lan
10.10.2.0/24 dev ens192  table rt_lan  scope link
default via 198.41.214.129 dev ens224  table rt_wan
198.41.214.128/26 dev ens224  table rt_wan  scope link
default via 10.10.2.1 dev ens192 onlink
10.10.2.0/24 dev ens192  proto kernel  scope link  src 10.10.2.41
198.41.214.128/26 dev ens224  proto kernel  scope link  src 198.41.214.140
broadcast 10.10.2.0 dev ens192  table local  proto kernel  scope link  src 10.10.2.41
local 10.10.2.41 dev ens192  table local  proto kernel  scope host  src 10.10.2.41
broadcast 10.10.2.255 dev ens192  table local  proto kernel  scope link  src 10.10.2.41
broadcast 127.0.0.0 dev lo  table local  proto kernel  scope link  src 127.0.0.1
local 127.0.0.0/8 dev lo  table local  proto kernel  scope host  src 127.0.0.1
local 127.0.0.1 dev lo  table local  proto kernel  scope host  src 127.0.0.1
broadcast 127.255.255.255 dev lo  table local  proto kernel  scope link  src 127.0.0.1
broadcast 198.41.214.128 dev ens224  table local  proto kernel  scope link  src 198.41.214.140
local 198.41.214.140 dev ens224  table local  proto kernel  scope host  src 198.41.214.140
broadcast 198.41.214.191 dev ens224  table local  proto kernel  scope link  src 198.41.214.140
fe80::/64 dev ens192  proto kernel  metric 256  pref medium
fe80::/64 dev ens224  proto kernel  metric 256  pref medium
unreachable default dev lo  table unspec  proto kernel  metric 4294967295  error -101 pref medium
local ::1 dev lo  table local  proto none  metric 0  pref medium
local <hide ***> dev lo  table local  proto none  metric 0  pref medium
local <hide ***> dev lo  table local  proto none  metric 0  pref medium
ff00::/8 dev ens192  table local  metric 256  pref medium
ff00::/8 dev ens224  table local  metric 256  pref medium
unreachable default dev lo  table unspec  proto kernel  metric 4294967295  error -101 pref medium

```

---

### Post by patrick.f on 2019-04-14
sorry @TheCog,
you were right. It was the Reverse-Path-Filtering. But had to reboot, althought 
```
$ cat [FONT=inherit]/proc/sys/net/ipv4/conf/all/rp_filter[/FONT]
```[FONT=inherit] already showed 0.

[/FONT]Thank you so so much for this hint!
Pakets are received now on Host #1. Now it's time to find a way back to the source for our little packages.

I did remove
```
sudo iptables -t nat -A POSTROUTING -o ens192 -j MASQUERADE
```
now, since i don't really understand it well at the moment.

More help is welcome :)

---

### Post by The Cog on 2019-04-14
On host #2 Assume the client is 1.1.1.1 (for want of a public address)
Incoming on ens224 : 1.1.1.1 -> 198.41.214.140:9987
NAT mangles the dest address: 1.1.1.1 -> 10.10.2.33:9987
Now this needs routing. Neither rule 100 or 200 apply (wrong source address). Table main (tablle not named in the line) has an entry for 10.10.2.0/24 via ens192.
The NAT MASQUERADE rule mangles the source address: 10.10.2.41 -> 10.10.2.33:9987

I can't think what the problem might be. I'll keep it in mind but I have to go out now. Sorry.

---

### Post by patrick.f on 2019-04-14
np. You helped me out greatly.

---

### Post by patrick.f on 2019-04-14
With 
```
-A POSTROUTING -o ens224 -p udp -m udp --dport 9987 -j MASQUERADE
``` enabled, here is the current state.
I've made a paket-tracing for a connection-attempt.

[COLOR=#008000]HOST #2, WAN INCOMING[/COLOR]
```
tcpdump: listening on ens224, link-type EN10MB (Ethernet), capture size 262144 bytes
15:44:23.055332 IP (tos 0x0, ttl 123, id 45891, offset 0, flags [none], proto UDP (17), length 62)
    1.1.1.1.54034 > 198.41.214.140.9987: UDP, length 34
15:44:23.055622 IP (tos 0x0, ttl 123, id 45892, offset 0, flags [none], proto UDP (17), length 212)
    1.1.1.1.54034 > 198.41.214.140.9987: UDP, length 184


```

[COLOR=#008000]HOST #2, LAN OUTGOING[/COLOR]
```
tcpdump: listening on ens192, link-type EN10MB (Ethernet), capture size 262144 bytes
15:44:23.055471 IP (tos 0x0, ttl 122, id 45891, offset 0, flags [none], proto UDP (17), length 62)
    10.10.2.41.54034 > 10.10.2.33.9987: UDP, length 34
15:44:23.055642 IP (tos 0x0, ttl 122, id 45892, offset 0, flags [none], proto UDP (17), length 212)
    10.10.2.41.54034 > 10.10.2.33.9987: UDP, length 184

```

[COLOR=#008000]HOST #1, LAN INCOMING[/COLOR]
```
tcpdump: listening on eth1, link-type EN10MB (Ethernet), capture size 262144 bytes
15:44:23.057040 IP (tos 0x0, ttl 122, id 45891, offset 0, flags [none], proto UDP (17), length 62)
    10.10.2.41.54034 > 10.10.2.33.9987: UDP, length 34
15:44:23.057547 IP (tos 0x0, ttl 122, id 45892, offset 0, flags [none], proto UDP (17), length 212)
    10.10.2.41.54034 > 10.10.2.33.9987: UDP, length 184

```

[COLOR=#008000]HOST #1, LAN OUTGOING[/COLOR]
```
tcpdump: listening on eth1, link-type EN10MB (Ethernet), capture size 262144 bytes
15:44:23.057716 IP (tos 0x0, ttl 63, id 18321, offset 0, flags [DF], proto UDP (17), length 60)
    10.10.2.33.9987 > 10.10.2.41.54034: UDP, length 32


```

[COLOR=#008000]HOST #2, LAN INCOMING[/COLOR]
```
tcpdump: listening on ens192, link-type EN10MB (Ethernet), capture size 262144 bytes
15:44:23.056254 IP (tos 0x0, ttl 63, id 18321, offset 0, flags [DF], proto UDP (17), length 60)
    10.10.2.33.9987 > 10.10.2.41.54034: UDP, length 32

```

[COLOR=#ff0000]HOST #2, LAN OUTGOING (needs to be WAN)[/COLOR]
```
tcpdump: listening on ens192, link-type EN10MB (Ethernet), capture size 262144 bytes

15:44:23.056310 IP (tos 0x0, ttl 62, id 18321, offset 0, flags [DF], proto UDP (17), length 60)
    198.41.214.140.9987 > 1.1.1.1.54034: UDP, length 32

```


My conclusion is, everything is fine. Except: The last response is sendet out on the WRONG interface.

Help still welcome.
I'm trying to read further myself.

---

### Post by The Cog on 2019-04-15
Tricky. 
The return packet passing through host#1 is passing through a reverse masquerade, converting 10.10.2.33 -> 10.10.2.41 into 10.10.2.33 -> 1.1.1.1 (DNAT is done before routing). 
Then the packet is routed. Rule 100 applies and uses table rt_lan. Game Over!
After choosing the routing, the packet undergoes SNAT (reversing the original DNAT) converting 10.10.2.33 -> 10.1.1.1 into 198.41.214.140 -> 1.1.1.1, which is what you see finally.

So your problem appears to be because the host does DNAT before routing, and SNAT after routing. I think you need to re-thing the rules slightly to account for this. 
I will come back later, but I'm out of time again right now. Hopefully you have enough info to fix it now though.

---

### Post by patrick.f on 2019-04-15
One solution i got is, when return packages coming back from
HOST#1 ==> HOST #2.

```

sudo iptables -t mangle -A PREROUTING -i ens192 -p udp -s 10.10.2.33 --sport 9987 -j MARK --set-mark 1
sudo ip rule add fwmark 1 table rt_wan priority 1

```

Marking them, and then create another rule to send out the marked packages via the correct interface.
This does work. So at this point i've got a running setup!

---

### Post by patrick.f on 2019-04-15
But it doesn't feel right for me.
For example, it doesnt work if i connect via the LAN IP ([COLOR=#000000][FONT=&quot]10.10.2.41)[/FONT][/COLOR], then the mark sends out on the wrong interface again.
The whole "mark" stuff in general feels a little bit russian for me too :) Should i have bad feelings using it?

I'm going to try to understand all the stuff a bit better and find the setup in general.
Post #8 show's me, that i'm not where i should be with my understanding :D

---

### Post by The Cog on 2019-04-15
I think marking and routing is a reasonable thing to do. I've done it before, marking based on source address in my case, and also using SNAT.

Another possibility would be to apply rules based on source interface rather than by IP addresses. So packets arriving on the LAN that you don't have a local route for (i.e. not for yourself) use the wan table. It's probably a good idea to filter as well, or you will be letting the whole LAN use you as a bypass.

---

### Post by patrick.f on 2019-04-15
> [COLOR=#000000]Another possibility would be to apply rules based on source interface rather than by IP addresses
May i ask you to specify that a little? i understand what you mean, but missing the idea where i can set rules for a source-interface.[/COLOR]

---

### Post by The Cog on 2019-04-15
man ip-rule
look for **iif** just below **from** and **to**.
e.g. ```
ip rule add priority 50 iif ens192 table rt_wan
```
I'm not sure which I prefer. iif is simpler but a bit of a blunt instrument - fwmark is more precise and surgical.

---

