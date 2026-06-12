---
title: "wired dsl problem"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by tyk on 2008-09-09
Hi all,
I have a real slooow internet connection on my t23 laptop with any version of ubuntu. On the same line, my other computer running xubuntu hardy sails smoothly. interestingly they can ping each other with 0% packet loss, but the laptop cannot ping the dsl modem without at least 80% packet loss. therefore, while the internet works on it, it is extremely slow. both computers are set to manual ip addresses and pppoeconf on the laptop says that it cannot find the 'concentrator' or another pppoe process might be using the lan card.
i would like my laptop to have xubuntu as it seems to be the 'one for me' :)
any suggestions, please?

---

### Post by fs3rp4 on 2008-09-09
> **tyk said:**
> Hi all,
I have a real slooow internet connection on my t23 laptop with any version of ubuntu. On the same line, my other computer running xubuntu hardy sails smoothly. interestingly they can ping each other with 0% packet loss, but the laptop cannot ping the dsl modem without at least 80% packet loss. therefore, while the internet works on it, it is extremely slow. both computers are set to manual ip addresses and pppoeconf on the laptop says that it cannot find the 'concentrator' or another pppoe process might be using the lan card.
i would like my laptop to have xubuntu as it seems to be the 'one for me' :)
any suggestions, please?

Hello!


Post the screen of this 2 commands:

sudo ifconfig

sudo route

---

### Post by tyk on 2008-09-09
sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:d0:59:34:90:91  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fe34:9091/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1522 errors:0 dropped:0 overruns:1545 frame:1545
          TX packets:3475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:778407 (760.1 KB)  TX bytes:408464 (398.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:401 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32492 (31.7 KB)  TX bytes:32492 (31.7 KB)

sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

small correction
my xubuntu comp (which has a good internet connection) can also NOT ping the laptop which is set to ip 192.168.1.200

---

### Post by fs3rp4 on 2008-09-09
I presume your other PC is 192.168.1.3. Your network configuration look like fine. 

Please, what is the your modem model?

---

### Post by tyk on 2008-09-09
here's the full situation:
two comps running xubuntu 8.04
static ip addresses 192.168.1.100 and 192.168.1.200
gateway = 192.168.1.1
dns = service provider's

ping on comp ip 100 = 
alright to itself, dns and gateway, bad to comp ip200
ping on comp ip 200 = 
alright to comp ip100, bad to itself, dns and gateway.

so it seems to be a problem with the hardware on the comp with ip 192.168.1.200 (t23 thinkpad laptop), at least to me thats what it looks like. have tried dhcp and no difference in either comps. though i prefer static for port forwarding etc.

thanks for listening.

edit: modem model is 'beetel' 220 BX1 adsl2 + modem

---

### Post by fs3rp4 on 2008-09-09
> **tyk said:**
> here's the full situation:
two comps running xubuntu 8.04
static ip addresses 192.168.1.100 and 192.168.1.200
gateway = 192.168.1.1
dns = service provider's

ping on comp ip 100 = 
alright to itself, dns and gateway, bad to comp ip200
ping on comp ip 200 = 
alright to comp ip100, bad to itself, dns and gateway.

so it seems to be a problem with the hardware on the comp with ip 192.168.1.200 (t23 thinkpad laptop), at least to me thats what it looks like. have tried dhcp and no difference in either comps. though i prefer static for port forwarding etc.

thanks for listening.

edit: modem model is 'beetel' 220 BX1 adsl2 + modem


I would try two things:

First install a wireshark in the PC with problems and see if there is to many packets with problems in the communications among it and the modem. 

Second I would change the modem setup. I think your modem is able to authenticate alone. You don't need to authenticate from your PC. It's a guess...

---

### Post by tyk on 2008-09-09
dear fs3rp4
:)
thanks a lot really but i didn't understand either of the suggestions.
i mean errr.. whats a wireshark?
and by change the modem setup you mean the drivers? and by authenticate alone you mean what exactly?
i always thought that i was not a noob but it seems i am. i would like to add that this problem is not new and i have long ago posted about this but yours is the first suggestion which seems to guess the problem correctly. the command outputs i pasted were from the laptop which was running a live cd of xubuntu but has the same problem with the installed ubuntu 7.04. in the sense that it seems better on ubuntu but the connection mostly slows down and either dies or works in very short spurts at low speeds.
interestingly: if i ping any place from this comp with a smaller packet size (ping -s 32 google.com) it zips with zero packet loss. so to me the connectivity is there but it doesnt seem to be able to handle larger packet sizes.. does this make sense?
much thanks again.

---

