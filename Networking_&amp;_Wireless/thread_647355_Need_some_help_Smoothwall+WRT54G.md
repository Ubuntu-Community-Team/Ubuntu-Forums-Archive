---
title: "Need some help: Smoothwall+WRT54G"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by bwhite82 on 2007-12-22
Firstly, thank you for reading. I realize that there are smoothwall forums but I haven't received an "account activation" email yet, so I thought I'd ask here. I am hoping this gets read by a current smoothwall user as the following will probably confuse those who aren't.

Anyways, here's the rub. My home network is setup as follows:

Sat. modem --> Smoothwall box --> WRT54G router

I would simply like to be able to use the wrt as a WAP. Everything will be handled by the smoothwall box (dhcp, dns, etc), I simply need to use the wrt as a means to connect wirelessly to the internet. I believe that my smoothwall box is set up correctly as I am currently connected to the internet through it. Right now, I have a cable going from NIC1(GREEN) to a LAN port on the wrt, NIC2 (RED) is connected to the sat. modem. I have a cable running from another LAN port on the wrt to this computer.

So currently the router is acting as a simple hub although I cannot connect to its web interface OR connect wirelessly. I have changed zero default settings on the router (as of yet).

Heres some pertinent info:

Sat. Modem:
Dynamic IP from ISP
Privated IP (to access web interface) is 192.168.0.1 <--not able to be changed


Smoothwall box:

Default Security level: Open
Network config. type: Red+Green
Green IP: 192.168.1.1
Green network mask: 255.255.255.249
Red: set to DHCP (hostname: smoothwall, ip+netmask left blank)
Primary DNS: 66.82.4.8 <---ISP's DNS server
Default Gateway: 192.168.0.1
DHCP enabled: range: 192.168.1.100-200
DHCP Primary DNS: 66.82.4.8


WRT54G:

-Default settings-
IP: 192.168.1.1
Netmask: 255.255.255.0
DHCP enabled

I do realize that there is an IP conflict with the wrt and the smoothwall box, I simply do not want to change anything until I get some advice. I spent hours last night trying various scenarios with the wrt settings to no avail. I've tried disabling DHCP on the wrt, whilst setting its IP to a non-conflicting one on both the same subnet and different subnet as the smoothie box. I believe my issue to be IP/subnet related. Thanks!

---

### Post by bwhite82 on 2007-12-22
Alright, figured it out meself. For any others who run into the same problem:

I changed the GREEN (on the smoothwall box) subnet mask to: 255.255.255.0
I disabled DHCP on the wrt
I set wrt's ip to 192.168.1.201
I set wrt's subnet mask to 255.255.255.0

I can access all the web interfaces now and surf the web.

To access smoothwall config, goto browser and type GREENIP:81 in my case: 192.168.1.1:81

---

### Post by Thund3rstruck on 2008-01-05
I actually did the opposite with my WRT54G/Smoothie. 

I ran an Ethernet cable from one of my switches into the WAN/Internet port on my WRT54G. 
Then I set a static ISP IP Address to an address on my smoothwall green zone subnet and pointed the gateway and DNS to the smoothwall. 

I left DHCP on (WRT54G) on a different subnet and set the "internal" IP on that subnet. 

So now when my wireless client connect they get an IP 192.168.1.x where the rest of my wired green zone gets 192.168.2.x. By doing this, wireless clients can access all resources in the green zone and on the internet without having to establish static routes between the 2 routers. All wifi clients are on the 192.168.1.x subnet so I can easily differentiate wifi clients from wired clients. 

NOTE: this is really dangerous, and stupid to a certain degree because I essentially have a bank vault front door and a screened in back door so we only plug in the wireless router when absolutely necessary (like when I need to stream music to my workshop out back or surfing the net while watching TV) ;)

---

