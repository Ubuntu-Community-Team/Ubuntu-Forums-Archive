---
title: "network issues, DNS"
date: 2005-11-13
forum: Networking &amp; Wireless
---

### Post by raven on 2005-11-13
I have a router hacked as client (since linux not so famous on wireless)
and my access point on the top floor (original), it was working perfectly
than we decided to get a VOIP router, DLINK DVG-1120M
than problems started
I can ping all my gateways I can log on all my routers
I can ping google.com or yahoo.com very fast (by name or IP)
I just cannot surf on all browsers (opera. FF, konqueror) very slow 5 min to get a page but the page will come up, it's rare that it will time out
and sometime for no reason I will get a fast response ex:ubuntu forums
than 5 min later I have to wait again for 5 min to get a page
when I use my XP (swap HD) and is configured with the same network, even have the same static IP 192.168.2.2 cause I have to take out linux (I have 1 PC) it works fine (a bit slower than when no VOIP router) but acceptable

*my resolv.conf have my gateways
nameserver 192.168.2.200
nameserver 192.168.1.1
nameserver 192.168.15.1

*route
Kernel IP routing table
Destination.....Gateway...........Genmask..........Flags Metric..Ref.....Use Iface
localnet.............*...............255.255.255.0.........U.......0......0.......0..eth0
default.........192.168.2.200...0.0.0.0...................UG.....0......0.......0..eth0

*cat /etc/networks/interfacess
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet static
	address 192.168.2.2
	netmask 255.255.255.0
	network 192.168.2.0
	broadcast 192.168.2.255
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.2.200 192.168.1.1 192.168.15.1
	gateway 192.168.2.200

auto eth0



here is the configuration of my network
1st linksys router hacked as client (WRT54G)
2nd linksys router original (WRT54G)
VOIP router DLINK DVG-1120M
* all subnets are 255.255.255.0

linux kubuntu static IP 192.168.2.2
gateway 192.168.2.200
name servers 192.168.2.200 192.168.1.1 now added 192.168.15.1

1st router (hacked as client)
static IP 192.168.2.200
gateway 192.168.1.1
local DNS 192.168.1.1

1st router (hacked as client) wireless settings connect to 2nd router wireless
static IP 192.168.1.102
gateway 192.168.1.1
DNS 192.168.1.1 now added 192.168.15.1

2nd router (orginal) LAN settings
static IP 192.168.1.1
gateway 192.168.15.1
DNS 192.168.15.1

2nd router (original) WAN settings, of course it use to be PPPOE now DHCP
IP 192.168.15.4
gateway 192.168.1.15
DNS 192.168.15.1

VOIP router DLINK
DHCP on the lan side 192.168.15.1
WAN settings PPPOE

any help ?

---

### Post by giftnudel on 2005-11-13
Hi,

try to replace your resolv.conf with an internet nameserver and see if things improve 

giftnudel

---

### Post by mips on 2005-11-13
Alternatively try and disable IPv6.

---

### Post by raven on 2005-11-13
[QUOTE=giftnudel]Hi,

try to replace your resolv.conf with an internet nameserver and see if things improve 

giftnudel[/QUOTE]

definetly it works great but these name servers change from my ISP
what I'm trying to do is make it through routers, cause before
having the VOIP router I did not have any name servers except my gateways and each router will be the DNS of the one before it, it worked great, when I put this DLINK VOIP router I do the same setting, but like I said  it's very slow, and sometime it works fast than will work very slow.

1 question why when I ping it works very fast ?

any suggestion about configuring it through routers ?

---

### Post by raven on 2005-11-13
[QUOTE=mips]Alternatively try and disable IPv6.[/QUOTE]

but than before getting VOIP router it was working fine and IPV6 was on as now ?

can you tell me how to do it ? (disable IPV6)

---

### Post by mips on 2005-11-13
raven,

There are known issues with certain D-Link routers, I dont know if it applies to your model though.

Make sure your router has the latest firmware loaded !!!

Look here for IPv6:
[http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)

---

### Post by raven on 2005-11-13
It's fixed and this how is solved

I just added in the 1st router DNS space my ISP DNS server
I don't like it cause ISP DNS will change and I have to update it
but better than doing it on the PC

I just don't understand why would not work as before, where
every gateway will be the DNS forwarding of the previous router

Thanx all for the responses and
thanx mips for the gmail :D

---

### Post by giftnudel on 2005-11-14
Hi,

first of all, you need 1 (in words one) dns server in your network. This should be the router which is connected to the internet since that one will get the dynamic dns servers from the isp. So your resolv.conf should only contain the ip from the router and all others should ask only that one. This should work, if the router has its own dns server. 

Your config might have had problems since the routers where asking themselves. It was fast for one saved ip, but for example the different ad servers must be looked up, too, and that's one reason why it can be slow.

Hope that cleared things up,

giftnudel

---

### Post by mips on 2005-11-14
ISPs usually dont change their DNS server IP addresses on a regular basis, it would be suicidal for them and their clients. My DNS server IP's have not changed since inception over 10yrs ago. They add new ones but the old ones stay.

---

### Post by giftnudel on 2005-11-14
Hi,

well mine does (T-Online in Germany). They change them on a regular basis, but when you establish a pppoe connection, they give you two dns server which work. This will then be added to resolv.conf and I distribute them via dhcp to my clients ...

so far, 

giftnudel

---

### Post by mips on 2005-11-14
That sounds really strange.


[http://www.atelier89.de/users/dirk/t-o/010.html](http://www.atelier89.de/users/dirk/t-o/010.html)
Die Liste

Neuerdings antworten einige der Server nicht mehr auf DNS-Anfragen! Diese Server sind in der Liste mit einem entsprechenden Kommentar versehen bzw. habe ich sie ganz entfernt.

Es gibt au&#223;erdem eine Liste weiterer Server, die sich nach einem bestimmten Muster ermitteln lassen.

Son, 27. M&#228;r 2005 16:47:39 CEST; 13 Bereiche mit insgesamt 9 Adressen
Lokale DNS-Server von T-Online Stadt	1. Server	2. Server
Dortmund	217.237.151.225 (O.K.)	keine
Hannover	217.237.149.161 (O.K.)	keine
Hansestadt Hamburg	217.237.150.225 (O.K.)	keine
K&#246;ln	217.237.150.97 (O.K.)	keine
Leipzig	217.237.149.225 (O.K.)	keine
M&#252;nchen	217.237.151.97 (O.K.)	keine
N&#252;rnberg [Stadt]	212.185.253.9 (O.K.)	keine
Stuttgart	217.237.151.161 (O.K.)	keine
Alb-Donau-Kreis und Ulm	217.237.150.141 (O.K.)	keine
Liste weiterer Server

Bei diesen Adressen handelt es sich ebenfalls um DNS-Server.

Son, 27. M&#228;r 2005 16:53:53 CEST; 3 Bereiche mit insgesamt 6 Adressen
Weitere DNS-Server von T-Online Stadt	1. Server	2. Server
Frankfurt am Main [Stadt]	194.25.0.69 (O.K.)	194.25.0.70 (O.K.)
Hannover	194.25.0.61 (O.K.)	194.25.0.62 (O.K.)
Leipzig	194.25.0.53 (O.K.)	194.25.0.54 (O.K.)
dns00.btx.dtag.de	194.25.2.132	keiner
dns01.btx.dtag.de	194.25.2.130	keiner
dns02.btx.dtag.de	194.25.2.131	keiner
dns03.btx.dtag.de	194.25.2.129	keiner
dns04.btx.dtag.de	194.25.2.133	keiner
dns50.t-ipnet.de	217.5.100.185	keiner
dns51.t-ipnet.de	217.5.100.186	keiner


[http://fx3.org/faq/t-online_dns.php](http://fx3.org/faq/t-online_dns.php)
DNS Server bei T-Online (15.11.2004)
geschrieben von: link J&#246;rg-Olaf Sch&#228;fers
zuletzt ge&#228;ndert: 15.11.2004, 16:20

DNS Server bei T-Online      			    (15.11.2004)
================================================================ 
* + 194.25.2.129   dns03.btx.dtag.de           Port: 53  domain     
* + 194.25.2.130   dns01.btx.dtag.de           Port: 53  domain     
* + 194.25.2.131   dns02.btx.dtag.de           Port: 53  domain     
* + 194.25.2.132   dns00.btx.dtag.de           Port: 53  domain     
* + 194.25.2.133   dns04.btx.dtag.de           Port: 53  domain     
..                                                                  
* + 194.25.2.161   dns30.btx.dtag.de           Port: 53  domain     
* + 194.25.2.162   dns31.btx.dtag.de           Port: 53  domain     
* + 194.25.2.163   dns32.btx.dtag.de           Port: 53  domain     
* + 194.25.2.164   dns33.btx.dtag.de           Port: 53  domain     
* + 194.25.2.165   dns34.btx.dtag.de           Port: 53  domain     
..                                             
* + 194.25.2.170   dns39.btx.dtag.de           Port: 53  domain     
* + 194.25.2.171   dns40.btx.dtag.de           Port: 53  domain     
* + 194.25.2.172   dns41.btx.dtag.de           Port: 53  domain     
* + 194.25.2.173   dns42.btx.dtag.de           Port: 53  domain     
* + 194.25.2.174   dns43.btx.dtag.de           Port: 53  domain     
* + 194.25.2.175   dns44.btx.dtag.de           Port: 53  domain     
..                                                                  
* + 194.25.2.181   dns45.btx.dtag.de           Port: 53  domain     
..                                                                  
* + 194.25.2.184   dns46.btx.dtag.de           Port: 53  domain

---

### Post by raven on 2005-11-14
[QUOTE=giftnudel]Hi,

first of all, you need 1 (in words one) dns server in your network. This should be the router which is connected to the internet since that one will get the dynamic dns servers from the isp. So your resolv.conf should only contain the ip from the router and all others should ask only that one. This should work, if the router has its own dns server. 

Your config might have had problems since the routers where asking themselves. It was fast for one saved ip, but for example the different ad servers must be looked up, too, and that's one reason why it can be slow.

Hope that cleared things up,

giftnudel[/QUOTE]

before I get the VOIP router all worked fine, but I will give your post a shot
I am not sure if they have the DNS server but worked fine before, so I guess they do. (linksys WRT54G)

what I have in my resolv.conf is the 3 router's static IP's (gateways)
192.168.1.15 3rd router connect to DSL modem
192.168.1.1 2nd router which is my access point (wireless)
192.168.2.200 1st router which is the gateway to my PC (client to 2nd wireless connection)

I don't see any problem putting 3 of them especially when what you asked is already in as the first DNS 192.168.15.1 in resolv.conf

allright, I will repeat what I understood from your post.

on my PC's I will have only the last (3rd) gateway IP of the router LAN SIDE that connect to my DSL in resolv.conf which is 192.168.15.1

on the 1st router (which will be the first router coming from the PC) what do I put in the DNS space LAN SIDE(it's a static IP) ?
what I have now is 192.168.1.1 LAN SIDE

on the 1st router (which will be the first router coming from the PC) what do I put in the DNS space WIRELESS SIDE (it's a static IP) ?
what I have now is the IP of the next router 192.168.1.1 and 192.168.1.15

what do you put in the second router DNS space, LAN SIDE ?

WAN of the 2nd router is configured DHCP so is getting the info from the 3rd router the ISP DNS's

if you want give me the the way you would configure your network (with dummy IP's I will manage with setting up my routers later)
my network starting from PC >

PC linux static IP wired
IP=
subnetmask=
gateway=
DNS1=
DNS2=
DNS3=

1st router static IP lan (WRT54G client to access point)
IP=
subnetmask=
gateway=
DNS1=

1st router static IP wireless (WRT54G client to access point)
IP=
subnetmask=
gateway=
DNS1=
DNS2=
DNS3=

2nd router static IP lan (access point WRT54G)
IP=
subnetmask=
gateway=
DNS1=
DNS2=
DNS3=

2nd router is DHCP wan side (access point WRT54G)

3rd router lan is static IP (Dlink VOIP DVG-1120M)
IP=
subnetmask=
gateway=
DNS1=
DNS2=
DNS3=

Sorry about the long post, I'd rather give more info than you have to ask.

---

### Post by raven on 2005-11-14
ignore

---

### Post by raven on 2005-11-14
ignore

---

### Post by giftnudel on 2005-11-16
Hi,

from what I have read, you have the following configuration:
```

Internet --- VOIP Router --- Router #1 .·``·. Router #2 --- PC
where:
--- means wired, .·``·. means wireless

```If so, I suggest the following configuration:
VOIP Router is DNS server. If you want DHCP, let the Voip router do that, too.
```

Netmask is always 255.255.255.0
Name     | IP        | Gateway   | DNS
---------+-----------+-----------+-------------
VOIP     |192.168.0.1| Internet  |From ISP, auto
Router #1|192.168.0.2|192.168.0.1|192.168.0.1
Router #2|192.168.0.3|192.168.0.1|192.168.0.1
PC       |192.168.0.x|192.168.0.1|192.168.0.1

```This should work, and that's how I did it at home (I have only one intermediate, though, if it isn't working, try to seperate it into two networks, use the approach below to do that)
giftnudel

P.S.: This is a three different Networks approach, I don't know if it works, but it looks like fun and it might work, you can merge network .0+.1 to get to two networks
```

Netmask is always 255.255.255.0
Connect. | IP        | Gateway   | DNS       |Interface
---------+-----------+-----------+-----------+-----------
VOIP     |192.168.0.1| Internet  |auto (isp) | Lan
R#1-Voip |192.168.0.2|192.168.0.1|192.168.0.1| Lan
R#1-R#2  |192.168.1.1|192.168.1.2|192.168.0.1| wlan
R#2-R#1  |192.168.1.2|192.168.1.1|192.168.0.1| wlan
R#2-PC   |192.168.2.1|unnecessary|192.168.0.1| Lan
PC       |192.168.2.x|192.168.2.1|192.168.0.1| Lan

```

---

### Post by raven on 2005-11-19
```

Netmask is always 255.255.255.0
Connect. | IP        | Gateway   | DNS       |Interface
---------+-----------+-----------+-----------+-----------
VOIP     |192.168.0.1| Internet  |auto (isp) | Lan
R#1-Voip |192.168.0.2|192.168.0.1|192.168.0.1| Lan
R#1-R#2  |192.168.1.1|192.168.1.2|192.168.0.1| wlan
R#2-R#1  |192.168.1.2|192.168.1.1|192.168.0.1| wlan
R#2-PC   |192.168.2.1|unnecessary|192.168.0.1| Lan
PC       |192.168.2.x|192.168.2.1|192.168.0.1| Lan

```

thanx for responding giftnudel
this is exactly what I have(dif IP's), except in ubuntu (now I have 2 machines)
they're both a lot slower than winXP, they are all 
of them on the same router R#2
my question is does ubuntu treat the network (especially DNS, cache) 
differently than winXP ?
even the windows machine is the slowest and the cheapest NIC but the fastest surfing

---

### Post by giftnudel on 2005-11-20
[QUOTE=raven]
my question is does ubuntu treat the network (especially DNS, cache) 
differently than winXP ?
even the windows machine is the slowest and the cheapest NIC but the fastest surfing[/QUOTE]

Hi,

funny that you are saying this, because I have the same problem in my network. I'm the only Linux PC in here, and I'm the only one that has dns problems. I had to manually add DNS servers to my resolv.conf to get it working. So there must be some problem somewhere, but I don't know where

giftnudel

---

### Post by raven on 2005-11-20
[QUOTE=giftnudel]Hi,

funny that you are saying this, because I have the same problem in my network. I'm the only Linux PC in here, and I'm the only one that has dns problems. I had to manually add DNS servers to my resolv.conf to get it working. So there must be some problem somewhere, but I don't know where

giftnudel[/QUOTE]

the only diference between me and you, is that my linux boxes were the same surfing speed as winXP box till I added VOIP router, while winXP stayed the same speed, linux boxes 2 of them got slower (unbareable speed) but no DNS errors.

any input from anybody ?

---

