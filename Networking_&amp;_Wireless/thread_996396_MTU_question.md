---
title: "MTU question"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by kingleviathan on 2008-11-28
Ive just done a fresh install of 8.10 ubuntu.

I've connected to the internet usin pppoe no problem (connect via ethernet) no problem.

But I have got this message: Interface eth0 has mtu of 576 -- should be 1500. You may have serious connection problem.

No idea what this means but searching around. It sounds like I have to change /etc/network/interface to fix this permantly.

In the /etc/network/interface file i currently have

auto lo
iface lo inet loopback

no idea what that means but if I simpl add the line "mtu 1492" and save the file will the problem be removed?

---

### Post by caljohnsmith on 2008-11-28
Before you set your MTU, how about following the first part of [this tutorial]("http://ubuntuforums.org/showthread.php?t=872346") to check what your MTU should be. Also, Intrepid's network manager unfortunately no longer uses the /etc/network/interfaces file, so it won't help if you put the mtu line in that file. I'm not sure what the most elegant solution is now, but one way you could set the MTU automatically on start up is to put:
```
ifconfig eth0 mtu <value>
```
In your /etc/rc.local file. But how about first finding out what your MTU should be, based on the tutorial, and let me know what you come up with.

---

### Post by kingleviathan on 2008-11-28
Thanks for your help.

It looks like my total packet size is 546 (+28 ). 

So maybe I dont need to change anything. 

Bit confusd though because I have ADSL PPPOE and searching on the internet suggests that PPPOE is 1492 whilst Im at a dial up level. Does this affect performance?

---

### Post by kingleviathan on 2008-11-29
Ok...Now it get really weird

I thought I would run this equivalent test on my windows laptops in cmd.exe

And I am able to ping successfully up to 1464

same bigpond adsl pppoe network but with a wireless care

So why cant I ping successfully any higher on my ubuntu PC?

---

### Post by J172 on 2008-11-29
Well, you're running two different cards in two different machines with two different platforms to test this issue (which CAN work, but of course it is better if you're atleast using the same platform). Are there any similarities in the network configurations that might be causing this (grasping at straws and I'm Net+ working on CCNA) I've never seen an MTU below 1500 (or above infact) unless there is some specialized configuration, protocol, or interface type. (But I don't usually offer gobs of attention to things at home [that sounds way worse than it is]).

---

### Post by kingleviathan on 2008-11-29
I hope im not sounding like an idiot but i just tried mtu pinging again on ubuntu and could get as hight as 1436 whilst earlier on i could on get to 530 or so. 

Can mtu vary through the day?

---

### Post by kingleviathan on 2008-11-29
Similarities? no idea. I just did a sudo of the NIC card and its set to 1492.

But otherwise its just a simple setting for connection nothing fancy.

---

### Post by J172 on 2008-11-29
MTU shouldn't vary (much) (if) at all. It is Maximum Transmission Unit. The maxiumum size of a packet. Have you checked the network configuration file?

---

### Post by caljohnsmith on 2008-11-29
> **kingleviathan said:**
> I hope im not sounding like an idiot but i just tried mtu pinging again on ubuntu and could get as hight as 1436 whilst earlier on i could on get to 530 or so. 

Can mtu vary through the day?
MTU is set by the each networking device in the chain between you and your destination, and the device with the lowest MTU limits your overall connection. So you have an ADSL modem? Do you connect to the ADSL modem in Ubuntu via a standard ethernet connection using DHCP or do you have the ADSL modem set in "bridged" mode so that you have to connect via PPPoE in Ubuntu? If you didn't deliberately set your ADSL modem to use "bridged" mode, most ADSL modems use the "PPPoE is on modem" option by default so that you connect to the modem via a standard DHCP ethernet connection. If you look at the bottom of the ADSL modem, usually it gives its local IP address, often "192.168.0.1", so you can access its settings from your web browser by simply going to [http://192.168.0.1](http://192.168.0.1) as the web address. Let me know what you find. :)

---

### Post by J172 on 2008-11-29
Excellent description. Definitely better than mine. And a bit less confusing probably.

Are you saying that the issue is probably router side?

---

### Post by caljohnsmith on 2008-11-29
> **J172 said:**
> Excellent description. Definitely better than mine. And a bit less confusing probably.

Are you saying that the issue is probably router side?
Well, since he says the MTU seems to vary depending on when he tests it, that's not a good sign, because the MTU should be fixed by the device with the smallest MTU in the networking chain between him and the internet; therefore, MTU should be 1492, which is the MTU of a standard PPPoE connection. So to answer your question, yes, I think maybe his problem could be with how he has his ADSL modem set up, and how he connects to it with Ubuntu. I think we need more info from him though in order to pinpoint the problem. :)

---

### Post by J172 on 2008-11-29
Agreed. This is an interesting problem though.

OP: Can you give us the MTU, device type, and maybe model of each of the networking devices on the network? Maybe there will be a Eureka moment. I bet its someting simple. The most complex problesm usually are.

---

### Post by uldo on 2008-12-09
so the idea is that if my router can hadle only packages of size 576 i should leave it like that on my pc? or can i change the size of router mtu somehow?

p.s. i have the same problem - i have MTU 576 and i'm using eth0 connection and i'm behind router (cable connection)
```
eth0      Link encap:Ethernet  HWaddr 00:19:d1:5a:72:9a  
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:475425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:713950 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:149833388 (149.8 MB)  TX bytes:236928103 (236.9 MB)
          Memory:93200000-93220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3439296 (3.4 MB)  TX bytes:3439296 (3.4 MB)

pan0      Link encap:Ethernet  HWaddr 2e:6c:bb:94:b6:37  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by caljohnsmith on 2008-12-09
> **uldo said:**
> so the idea is that if my router can hadle only packages of size 576 i should leave it like that on my pc? or can i change the size of router mtu somehow?

Did you try running the ping test in the [tutorial]("http://ubuntuforums.org/showthread.php?t=872346") that I linked to at the beginning of the thread? Before doing the ping test, you should first set your local MTU to 1500 by doing:
```
sudo ifconfig eth0 mtu 1500
```
And also access your router and change the MTU to 1500. You'll have to check your documentation to find out how to get access to your router, but you might try these addresses in your web browser:

[http://192.168.2.0](http://192.168.2.0)
[http://192.168.2.1](http://192.168.2.1)
[http://192.168.1.0](http://192.168.1.0)
[http://192.168.1.1](http://192.168.1.1)
[http://192.168.0.0](http://192.168.0.0)
[http://192.168.0.1](http://192.168.0.1)

One of those addresses might work. Once you have your local MTU and router MTU set to 1500 bytes, try doing the ping test in that tutorial and let me know what the results are.

---

### Post by uldo on 2008-12-10
well, i have to change router because i can't change mtu for this model. I contacted router manufacters support and got this answer:
```
On the WAN connection, you can specify the MTU size (For PPPoE or PPTP connections). However, if it is static IP, this value will be determine by your ISP and be automatically set.
```
My isp (havent called yet, but i suppose) doesnt suport PPPoE or PPTP. But anyway it should be set to 1500 by the ISP - about that i'm about to talk with them!!!!
Also i tried to connect directly without router - automaticly it gets 576, but when i switch to 1500 and try to ping it goes ok. And actually that doesnt fix the main problem..... :(

---

### Post by KillaB7 on 2008-12-16
After hours of troubleshooting a colleague and I found a solution to one particular MTU 576 scenario.

NetworkManager is an excellent tool but there are definite bugs with the current implementation in 8.10.
After a reboot, NetworkManager forgets static IP addressing as well as static MTU settings.

Setting the MTU manually with "sudo ifconfig eth0 mtu 1500" also proved futile as long as NetworkManager is still running the show.

The issue in our case ended up being with the DHCP client (dhcp3).  The client default settings request "interface-mtu" from the server and our ISP's DHCP server is set to 576.
You may or may not find this info via "/var/lib/dhcp3/dhclient.eth0.leases" or "/var/lib/dhcp3/dhclient.leases"


To correct this problem, find the following line in "/etc/dhcp3/dhclient.conf":
```

request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope[COLOR="Red"], interface-mtu[/COLOR];

```

and edit out the "interface-mtu" option:
```

request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope;

```

---

