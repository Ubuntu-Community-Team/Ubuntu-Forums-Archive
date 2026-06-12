---
title: "Network Unreachable"
date: 2015-05-16
forum: Networking &amp; Wireless
---

### Post by mmethw2003 on 2015-05-16
Hi Guys,

Please refer the following setup where I have a Server with Ubuntu OS.


[IMG]http://i62.tinypic.com/wkli4o.jpg[/IMG]

[SIZE=4]**My issue is as follow.**[/SIZE]

Server Gateway is set to " **X** " [ X , Y & Server IP is in same subnet ]. When I try to mtr Z first hop it goes to " **Y** " [ Y doesn't have routing towards Z so packet drops. ].
Strange thing is if I mtr next IP belongs to Z network it goes to " **X** " without any issue :(

_**Findings.**_

cat /proc/net/arp --> 
Y ---> 00:00:00:00:00:00
Z ---> 00:00:00:00:00:00

I removed the " Z " arp entry but issue is still the same and then I tried to remove " Y "'s arp entry but system doesn't removed it.

[COLOR=#ff0000]**Appreciate If some one can help me to resolve this issue  **[/COLOR]


Server Detail

Server OS = Ubuntu 12.04.4 LTS \n \l

---

### Post by mmethw2003 on 2015-05-17
[SIZE=4]**Any Advice ???**[/SIZE]

---

### Post by SeijiSensei on 2015-05-17
Let's start with the results of ifconfig and "route -n".  All this obfuscation about "X" and "Y" is just too confusing.  

Can you ping the upstream router that is the designated default gateway?

---

### Post by mmethw2003 on 2015-05-17
yes I can reach my default gateway.

Let me convert X & Y in to numbers.

X = 192.168.100.36/24
Y = 192.168.100.22/24

Server = 192.168.100.135/24
     Server GW = 192.168.100.36 // Gateway is reachable.

SWT 01 = 192.168.100.201/24
SWT 02 = 192.168.100.205/24

For the info I have tried clearing the Server ARP " ip -s -s neigh flush all " but it didn't worked. Finally I have restarted my network and now it's working.

---

