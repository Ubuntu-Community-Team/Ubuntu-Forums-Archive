---
title: "How to have two DHCP servers LTSP &amp; router"
date: 2014-08-07
forum: Networking &amp; Wireless
---

### Post by johnycage on 2014-08-07
I'm setting up an LTSP server for 3-4 client-PCs at my home. Run-rerun many installations & read many tutorials. It seems obvious to have Edubuntu for the setup. 
I must use DHCP for home network on D-Link DSL router (which connects to the internet) for mobile devices. But LTSP conflicts with my routers DHCP & have to use DHCP server from Ubuntu (isc-dhcp-server).
I've 2x 10GbE ethernet port on my LTSP server with Intel's Xeon Quad-core & server-grade motherboard.

Ideally I should be able to use my tablets/smartphones which rely on Dlink router's DHCP. and LTSP clients simultaneously. 

[LIST]
[*]How can I leverage two ehternet ports on my server-motherboard? 
[*]How to have two DHCP services (1 DSL router. 2 LTSP-server) without conflicting?
[*]Do I need different IP range? 
[*]How it's done with 1 internet connection? 
[/LIST]

PS: 
I am sorry for not being clear at first post. Let me elaborate the situation.
My modem-router is ON 24x7 and has built-in DHCP option. And everything was worked well. (until LTSP server came)

But for my LTSP clients I have to disable DHCP of my router. That's where the problem begins. I dont want my home-office computers (LTSP clients & server) to be running after 7 pm. So I may turn the LTSP system OFF in the night. (saving electricity, huh!)
I think it's clear that I'll need two DHCP services.
What should be the right settings for my situation? 
Thank you.

---

### Post by bab1 on 2014-08-07
> **johnycage said:**
> I'm setting up an LTSP server for 3-4 client-PCs at my home. Run-rerun many installations & read many tutorials. It seems obvious to have Edubuntu for the setup. 
I must use DHCP for home network on D-Link DSL router (which connects to the internet) for mobile devices. But LTSP conflicts with my routers DHCP & have to use DHCP server from Ubuntu (isc-dhcp-server).
I've 2x 10GbE ethernet port on my LTSP server with Intel's Xeon Quad-core & server-grade motherboard.

Ideally I should be able to use my tablets/smartphones which rely on Dlink router's DHCP. and LTSP clients simultaneously. 

[LIST]
[*]How can I leverage two ehternet ports on my server-motherboard? 
[*]How to have two DHCP services (1 DSL router. 2 LTSP-server) without conflicting?
[*]Do I need different IP range? 
[*]How it's done with 1 internet connection? 
[/LIST]

Thank you.
You can't force the use of any particular DHCP server operating in a subnet.  The routine is: *the client requests (via broadcast of the LAN) -->the DHCP sever offers up an address->the client accepts the first valid offer*.  Having 2 DHCP servers on the subnet means whichever DHCP server offers first determines which address range is used.  The general rule is: 1 DHCP server per subnet.

You can't use the servers multiple Ethernet ports on the same subnet .  All hosts (computers) should have only one IP address per subnet. 

Answering your questions directly:
[LIST=1]
[*]In your context you **can't use** both Ethernet ports
[*]In your situation you **can't use** 2 DHCP server in a single subnet
[*]Yes you do -- One for your private network and one for guests
[*]I assume you mean a common gateway.  You can use a default route instead of a default gateway on the new subnet of your network.
[*]
[/LIST]

---

### Post by johnycage on 2014-08-07
Thank you for your reply @BAB1. 
Excuse me for my limited knowledge. 

Moving on, and continuing from Q#4 Yes, a common gateway via DSL router (which has 192.168.1.1 as IP address)
My Ubuntu Server is on 192.168.1.2 (which also has isc-dhcp-server & ltsp-server-standalone running)

The scenario: 
1. Home devices (smartphones, tablets, xbox etc.)
Now I'd like to allot IP addresses 192.168.1.3 to 1.30 for my home devices/smartphones/laptops/tablets etc which has nothing to do with ubuntu server. These devices should be connected to the internet irrespective to the Ubuntu-server-status. 
Having said that, I should be able to access my http, ftp, smb/ samba files (multimedia, data & backups) located at ubuntu server 192.168.1.2 whenever it's switch ON.

2. LTSP Clients: 3 to 5 machines 
These should run under LTSP server 192.168.1.2 (ranging from 1.31 to 1.250) 
(above IP address doesnt matter they are just sake of clarity)
Can I achieve such setup? I mean can my LTSP setup co-exist with my existing LAN? using same gateway ie. 192.168.1.1 

Please suggest me the right subnet & IP range settings for each DHCPs.
Thank you.

---

### Post by johnycage on 2014-08-07
Thank you for your reply @BAB1. 
Excuse me for my limited knowledge. 

Moving on, and continuing from Q#4 Yes, a common gateway via DSL router (which has 192.168.1.1 as IP address)
My Ubuntu Server is on 192.168.1.2 (which also has isc-dhcp-server & ltsp-server-standalone running)

The scenario: 
1. Home devices (smartphones, tablets, xbox etc.)
Now I'd like to allot IP addresses 192.168.1.3 to 1.30 for my home devices/smartphones/laptops/tablets etc which has nothing to do with ubuntu server. These devices should be connected to the internet irrespective to the Ubuntu-server-status. 
Having said that, I should be able to access my http, ftp, smb/ samba files (multimedia, data & backups) located at ubuntu server 192.168.1.2 whenever it's switch ON.

2. LTSP Clients: 3 to 5 machines 
These should run under LTSP server 192.168.1.2 (ranging from 1.31 to 1.250) 
(above IP address doesnt matter they are just sake of clarity)
Can I achieve such setup? I mean can my LTSP setup co-exist with my existing LAN? using same gateway ie. 192.168.1.1 

Please suggest me the right subnet & IP range settings for each DHCPs.
Thank you.

---

### Post by bab1 on 2014-08-07
> **johnycage said:**
> Thank you for your reply @BAB1. 
Excuse me for my limited knowledge. 

Moving on, and continuing from Q#4 Yes, a common gateway via DSL router (which has 192.168.1.1 as IP address)
My Ubuntu Server is on 192.168.1.2 (which also has isc-dhcp-server & ltsp-server-standalone running)

The scenario: 
1. Home devices (smartphones, tablets, xbox etc.)
Now I'd like to allot IP addresses 192.168.1.3 to 1.30 for my home devices/smartphones/laptops/tablets etc which has nothing to do with ubuntu server. These devices should be connected to the internet irrespective to the Ubuntu-server-status. 
Having said that, I should be able to access my http, ftp, smb/ samba files (multimedia, data & backups) located at ubuntu server 192.168.1.2 whenever it's switch ON.

2. LTSP Clients: 3 to 5 machines 
These should run under LTSP server 192.168.1.2 (ranging from 1.31 to 1.250) 
(above IP address doesnt matter they are just sake of clarity)
Can I achieve such setup? I mean can my LTSP setup co-exist with my existing LAN? using same gateway ie. 192.168.1.1 

Please suggest me the right subnet & IP range settings for each DHCPs.
Thank you.
If you don't care that all of these devices are on the same subnet (i.e. 192.168.1.0/24 (255.255.255.0)) then why is it important that you have the 2 DHCP servers in the first place?  On a host (LTSP clients, smartphones, tablets, xbox etc.) is assigned an IP address (e.g. 192.168.1.1 to 254) is is a pier to all the others.  There is no priority given to any of the addresses.  They all have the same status.

If all the devices can live in the same subnet (192.168.1.0/24) then you would need one DHCP server that is on all the time.  You can set reserved IP addresses for each of the devices that are home devices (smartphones, tablets, xbox etc.).  These would be part of the DHCP pool but since each of these is reserved for a specific device it will only be handed out to that device.  All of the other devices will other devices will have access to the rest of the pool of IP addresses on a randomized basis. 

All of the devices share the same IP subnet and the DHCP serve has a pool of addresses that includes both the[COLOR="#0000FF"] reserved addresses 3 to 30[/COLOR]  and the[COLOR="#008000"] random addresses 31 to 250.[/COLOR].  Since these are all handled by the same DHCP server you can use the same settings for the same gateway.  As that ip addresses are all in the same subnet, the gateway is the same.

I have a similar configuration.  I have a range for fixed IP addresses and a range for random IP addresses, all in the same subnet.

One last thought; If you wanted to divide your network into to distinct sub-networks (192.168.0/25 and 192.168.128/25) you could do that.  Each sub-network would be separate and distinct.  But I don't see any advantage for you to do that.

---

### Post by johnycage on 2014-08-08
Thank you for the reply. I've same conf/setting what you described. 
But, here consider the case: 
My LTSP/Ubuntu server is ON only during office hours. (I'm not intended to keep it ON 24x7.)
However I assign all my machines static IP whenever possible, some machines, such as WindowsPhone (Nokia Lumia ) do not allow me to keep static IP relies on DHCP server. 
I case of guests, friends stop by I should be able to share my wifi/internet with them. 
Therefore when my router's DHCP service is disabled & when I switch OFF my ubuntu machine. I cannot join connect to the LAN or internet from mobile devices.

---

### Post by bab1 on 2014-08-09
> **johnycage said:**
> ...
However I assign all my machines static IP whenever possible, some machines, such as WindowsPhone (Nokia Lumia ) do not allow me to keep static IP relies on DHCP server. 

I case of guests, friends stop by I should be able to share my wifi/internet with them. 
Therefore when my router's DHCP service is disabled & when I switch OFF my ubuntu machine. I cannot join connect to the LAN or internet from mobile devices.

If you want DHCP service 24/7 then you need to have a host that is on 24/7.  My impression was that you have 2 host (devices) that are DHCP capable.  Either one should be capable of servicing the entire LAN.

I don't understand your problem at this point.

---

### Post by johnycage on 2014-08-10
I am sorry for not being clear at first post. Let me elaborate the situation. 
My modem-router is ON 24x7 and has built-in DHCP option. And everything was worked well. (until LTSP server came)

But for my LTSP clients I have to disable DHCP of my router. That's where the problem begins. I dont want my home-office computers (LTSP clients & server) to be running after 7 pm. So I may turn the LTSP system OFF in the night. (saving electricity, huh!)
I think it's clear that I'll need two DHCP services. 
What should be the right settings for my situation? 
Thank you.

---

### Post by bab1 on 2014-08-10
> **johnycage said:**
> I am sorry for not being clear at first post. Let me elaborate the situation. 
My modem-router is ON 24x7 and has built-in DHCP option. And everything was worked well. (until LTSP server came)

But for my LTSP clients I have to disable DHCP of my router. That's where the problem begins. I dont want my home-office computers (LTSP clients & server) to be running after 7 pm. So I may turn the LTSP system OFF in the night. (saving electricity, huh!)
I think it's clear that I'll need two DHCP services. 
What should be the right settings for my situation? 
Thank you.
If you must have differing DHCP servers then you will need 2 completely different LAN networks.  You can have an upstream router (maybe the modem-router) for one network and a router to separate the LTSP network.  In this case the LTSP network data would transit the fist network to reach the Internet.

If the LTSP network is off it really doesn't matter as it doesn't interfere with the original network.  See below```

Internet-->**modem-router**-->[COLOR="#800080"]original network<<<[/COLOR]---**new-router**--[COLOR="#0000FF"]>>>LTSP network[/COLOR]

```

Notice that the "new router" has an interface in both networks.  This router limits all LTSP broadcasts for DHCP service to the LTSP network.

The network will be completely different; say 10.0.0.0 /24 for the LTSP network and 192.168.1.0 /24 for the original network.

Thus your network is is really 2 networks with one of them transiting the other.  Will there be problems to work out?  You bet.  You will have to make sure the new router will actually route these "Private IP Networks".  Most professional routers will not without some reconfiguration.  The default is to NOT route [private network ]("http://en.wikipedia.org/wiki/Private_network")addresses on the Internet.

---

### Post by nix_weasel on 2014-08-11
or use virtualbox  install ubuntu then try this [http://ubuntuforums.org/showthread.php?t=2173749](http://ubuntuforums.org/showthread.php?t=2173749) its how i got around the same problem , and as far as i know it doesn't matter if it not your gateway machine  (it happens to be now on mine but i tested on a laptop) i have this setup running 4 thin clients (old 1ghz laptops set to boot from lan)

sorry reread the post "[COLOR=#000000]*That's where the problem begins. I dont want my home-office computers (LTSP clients & server) to be running after 7 pm" you could skip the virtual box part if you have a machine dedicated but in that case reread what instructions you have taken so far to reverse what you have done (or fresh install) then try the link, note i got tripped up on that part myself something previously tried gave me problems so i chose the fresh install route via virtualbox plus you can export the new working install so you got a instant(ish) recovery *[/COLOR][I]back to a working state
[/I][COLOR=#000000][I](considerably quicker than a reinstall your mileage may vary depending on how quick your machine is but i exported it from the laptop to server and had it running still in under the time it took for a reinstall, longest time was copying the file from one machine to the other) 

another thing bout the virtualbox route make sure the network settings are bridged to ethX not nat [/I][/COLOR]

---

### Post by johnycage on 2014-08-13
I still have not figured out the right solution & struggling with trial and errors. I would not go with virtualbox because I dont want to split my server even more. 
> **bab1 said:**
> 

One last thought; If you wanted to divide your network into to distinct sub-networks (192.168.0/25 and 192.168.128/25) you could do that.  Each sub-network would be separate and distinct.  But I don't see any advantage for you to do that. Do you think this should work for me? I think I should try. 
Again, how can I liverage two NIC ethernet ports if my server-motherboard provides it?

---

### Post by bab1 on 2014-08-13
> **johnycage said:**
> I still have not figured out the right solution & struggling with trial and errors. I would not go with virtualbox because I dont want to split my server even more. 
 Do you think this should work for me? I think I should try. 
Again, how can I liverage two NIC ethernet ports if my server-motherboard provides it?The example above has no advantage over using 192.168.1.0/24 and 192.168.100.0/24.  That earlier example has a distinct disadvantage in that each network only has 126 usable addresses instead of the typical 254.

Here are 2 equally viable methods of configuration to accommodate your need for 2 subnets.  The first is```

Internet<------->24/7 network modem-router[COLOR="#FF0000"]<--192.168.1.0/24 24/7 Net --->[/COLOR]|LTSP Server |[COLOR="#0000FF"]<---10.0.0.0/24 LTSP Net[/COLOR] 

``` 

In this network the LTSP Sever is also *_configured to function as a router and a DHCP server_*.  You could ***use the 2nd network card on the server ***but you still need a switch for this to work.  Your shutdown would include the LTSP Server and its workstations.

The second option we have discussed before.  It would be adding a second consumer router.  These routers are actually a router and a switch.  It looks like this```

Internet<----->24/7 network modem-router|[COLOR="#FF0000"]<--192.168.1.0/24 24/7 Net --->[/COLOR]|2nd router/switch|[COLOR="#0000FF"]<---10.0.0.0/24 LTSP Net[/COLOR]

```
This setup uses a off the shelf router/switch.  It has exactly topology (configuration) as the first solution.  Only the equipment differs.

All other network numbering schemes would use the same equipment.  It doesn't matter which you use.  It is more important you select the topology you will use rather than the numbering scheme.

---

### Post by nix_weasel on 2014-08-15
> *you could skip the virtual box part if you have a machine dedicated but in that case reread what instructions you have taken so far to reverse what you have done (or fresh install) then try the link* 

as i see it you want the end result of 
<router (dhcp)>--<homenetwork (phones guests etc)>--- <ltsp server>---<thin client 1,2,3,4>


note: make sure you don't plug eth0 & eth1 into the same Physical network it must be <switch(home network)>--<server ETH0>-nat/bridged-<server ETH1>--<switch thin client>---<thin client 1,2,3,4>

Option one: same ip range ie 192.168.0.0\24  and Eth0 & Eth1 single ip ie:192.168.0.10  (thin clients able to see whole network including shares on home network)

follow the guide [http://ubuntuforums.org/showthread.php?t=2173749](http://ubuntuforums.org/showthread.php?t=2173749) and this guide necessary for internet connection of the thin clients  [https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge) to bridge the two 10gbe Ethernet ports on server

--OR--

Option 2: dual dhcp servers two ip ranges eth0 192.168.0.0\24 home network -->>thin client setup eth1 192.168.1.0\24 (thin clients not able to see whole network limited to server and other thin clients)

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) then [http://www.havetheknowhow.com/Configure-the-server/Install-LTSP.html](http://www.havetheknowhow.com/Configure-the-server/Install-LTSP.html)

either way how to you plan on connecting the thin clients? most ive seen have a max of 1gbe ethernet so 4 x 1gbe ethernet = 4gbe total bandwith needed and your server has 10gbe ethernet port so thats fine BUT then if you only use a 10/100/1000 switch you are limited to the 1gbe max to the server leaving you short 3gbe unless it has a 10gbe uplink or you use a fully 10/100/1000/10000 switch, just a thought


good luck

---

