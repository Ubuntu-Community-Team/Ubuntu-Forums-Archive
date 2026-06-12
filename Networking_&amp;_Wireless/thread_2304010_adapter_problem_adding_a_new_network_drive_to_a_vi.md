---
title: "adapter problem adding a new network drive to a virutal ubuntu server"
date: 2015-11-23
forum: Networking &amp; Wireless
---

### Post by eric97 on 2015-11-23
Hello ubuntuforums,

I have been trying to familiarize myself with linux server environment and came across a problem when i started messing with networking setting. I changed the IP address of eth0 to static on a host only adapter to communicate to a ubuntu desktop machine. That went well i was able to get them on the same local network. I added another NAT adapter and added changes to /etc/network/interfaces. This adapter shows up fine in ifconfig but i cannot connect to the internet. I can ping the local VM but not google for example.

/etc/network/interfaces setting
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.0.1
network 10.0.0.0
netmask 255.255.255.0
broadcast 10.0.0.255
gateway 10.0.0.1
dns-nameserver 10.0.0.254

auto eth1
iface eth1 inet dhcp

```

ifconfig output
```

eth0 inet addr:10.0.0.1 Bcast:10.0.0.255 Mask:255.255.255.0
       inet6 addr (                                      ) Scope:Link
       UP BROADCASTRUNNING MULTICAST MTU:1500 Metric:1
       RX packets:945 erros:0 dropped:0 overruns:0 Frame:0
       TX packets:147 erros:0 dropped:0 overruns:0 carrier:0 
       collsions:0 txqueuelen:1000
       RX bytes:58290 (58.2KB)    TX bytes:9064 (9.0 KB)

eth1 Link encap:Ethernet   Hwaddr 08:00:27:60:6f:76
       inet addr:10.0.3.15 Bcast:10.0.3.255 Mask:255.255.255.0
       inet6 addr (                                       ) Scope:Link
       UP BROADCASTRUNNING MULTICAST MTU:1500 Metric:1
       RX packets:2 errors:0 dropped:0 overruns:0 Frame:0
       TX packets:10 erros:0 dropped:0 overruns:0 carrier:0
       collsions:0 txqueuelen:1000
       RX bytes:1180 (1.1 KB) TX bytes:1332 (1.3KB)

lo Link encap:local Loopback
   inet addr:127.0.0.1 Mask:255.0.0.0
   inet6 addr: ::1/128 Scope:Host
   UP LOOPBACK RUNNUING MTU:65532 Metric:1
   RX packets:85 errors:0 dropped:0 overruns:0 Frame:0
   TX packets:85 errors:0 dropped:0 overruns:0 Carrier:0
   collisions:0 txqueuelen:0

```

---

### Post by Hadaka on 2015-11-23
Hi, your gateway and static addresses are the same
```
auto lo 
iface lo inet loopback

auto eth0 
iface eth0 inet static 
address [COLOR=#ff0000]10.0.0.1 ->[/COLOR][COLOR=#000000]**10.0.0.254 **[/COLOR] 
network 10.0.0.0 
netmask 255.255.255.0 
broadcast 10.0.0.255 
gateway [COLOR=#ff0000]10.0.0.1[/COLOR] 
dns-nameserver 10.0.0.254 ->**8.8.8.8 8.8.4.4   replace with**

auto eth1 
iface eth1 inet dhcp
```

---

### Post by eric97 on 2015-11-23
Changed it, doesnt solve the problem. i still get "destination host unreachable" of i ping google. eth0 is my local network so that wouldnt make a difference with getting on the internet.

---

### Post by Hadaka on 2015-11-23
OK, It would probably be better to use 10.0.0.100 instead of .254 for the static addr,
also if your router is .1 as in gateway..10.0.0.1 then your server cant be .1 also.
are you useing network manager or wcid as well???
please post the output of..
```
cat /etc/NetworkManager/NetworkManager.conf
```
thanks

---

### Post by eric97 on 2015-11-23
cat: /etc/NetworkManager/NetworkManager.conf : No such file or directory

---

### Post by Hadaka on 2015-11-23
what is with the snakebites?
```
cat[COLOR=#ff0000]:[/COLOR] /etc/NetworkManager/NetworkManager.conf[COLOR=#ff0000]:[/COLOR]
```
try it again...biteless and what about the other questions? network manager???
wcid????

---

### Post by ozzie1 on 2015-11-23
if there is no internet on the eth0 network, drop/comment the gateway from the config altogether, restart that network interface, and it should use eth1's connection for internet access.

---

### Post by eric97 on 2015-11-23
snakebites? and same output trying it again, I am not using a network manager.

---

### Post by ozzie1 on 2015-11-23
when you ping google does it resolve an ip?

and wtf are snakebites?

---

### Post by Hadaka on 2015-11-23
My error, sorry about that, i have never noticed those before...odd.
These are snake bites. -> **:     **, ballbat -> **!     **,splat -> ***** and a bunch of other verbage from
days gone by, when code was chiseled into stone.
With that, I am running out of ideas and my knowledge of virtual stuff is limited.
please do..
```
 modinfo ath9k | grep "0036"
```
just report if it is there or not,
thanks.

---

### Post by eric97 on 2015-11-23
a lot of stuff showed up with the modinfo cmd

---

### Post by eric97 on 2015-11-24
UPDATE: I changed the adapter from NAT to bridged and i can not ping my host computer but still cant reach the internet.

---

