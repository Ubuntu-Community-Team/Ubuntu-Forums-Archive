---
title: "Static IP questions for Ubuntu 6.10 Edgy LAMP server edition"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by iFRE4K on 2008-07-28
Okay here is my problem. My internet is in constant use and it would be very bad for it to have to be down for long because of my experimentation. I recently installed Ubuntu 6.10 (edgy eft) lamp server edition. It has no gui, just command line. I am trying to set up a static IP with it. My internet is cable. It runs through a modem, then to a Lynksys wireless/4slot router. I know the command to change the internet to static on ubuntu is "sudo vi /etc/network/interfaces" It brings me to the screen which when changed should look like this:

auto eth0
iface eth0 inet static
address xxxx.xxxx.xxxx.xxxx
netmask xxxx.xxxx.xxxx.xxxx
network xxxx.xxxx.xxxx.xxxx
broadcast xxxx.xxxx.xxxx.xxxx
gateway xxxx.xxxx.xxxx.xxxx

I think that the netmask should be 255.255.255.255, and that the gateway should be the same as my dns, but how would I go about getting these 5 lines of addresses? Preferably w/out contacting my isp provider? Once I do this shouldn't the router be configured the same way? Future thanks for the help.

---

### Post by bab1 on 2008-07-29
> > **iFRE4K said:**
>  My internet is cable. It runs through a modem, then to a Lynksys wireless/4slot router.

[QUOTE]Do you mean that your server is attached to the Linksys?  Is it running as an AP and switch?

The modem should handle the routing from the ISP to your network.


> auto eth0
iface eth0 inet static
address xxxx.xxxx.xxxx.xxxx
netmask xxxx.xxxx.xxxx.xxxx
network xxxx.xxxx.xxxx.xxxx
broadcast xxxx.xxxx.xxxx.xxxx
gateway xxxx.xxxx.xxxx.xxxx

I think that the netmask should be 255.255.255.255, and that the gateway should be the same as my dns, 

The net mask is dependent on what the network your using requires.  Most use a /24 net and that would look like this:
iface eth0 inet static
address 192.168.1.n  [COLOR="Red"]where n=any num from 2-254[/COLOR]
netmask 255.255.255.0  [COLOR="Green"]masking the network part only[/COLOR]
network 192.168.1.0  [COLOR="Blue"]where 0 denotes the network[/COLOR]
broadcast 192.168.1.255  [COLOR="DarkOrange"]last num in the network goes to all[/COLOR]l
gateway 192.168.1.1  [COLOR="Magenta"]the nearside address of the router[/COLOR]

NOTE -- I'm not so sure all of this goes in /etc/network/interfaces.  Mine does not look like this.

---

### Post by cariboo on 2008-07-29
Depending on your router:

address 192.168.1.200
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

Your internal connections have to be on the same subnet as your router. To access your server from the outside world you will have to either connect your server directly to your cable modem, or use port forwarding in your router and dynamic dns. I use a free ddns service called noip.com

Jim

---

### Post by bab1 on 2008-07-29
> 
To access your server from the outside world you will have to either connect your server directly to your cable modem or...

Jim,

By what you say, a cable modem has the ISP's addr on the iterface [COLOR="Green"]you [/COLOR]connect to.  Is that so?  what is on the side facing the ISP and what is on the side facing the user?  I don't have that type of service so I ask.  I have a service that has an internet addr on one side and my private network on the other interface.

Edit:  I don't have a second router.  I do have a switch and an AP.  My wifes laptop is wireless and attaches to the network (mine) thru the AP and my 3 hosts are attached via the switch.  The switch is attached to the router "inside" interface and the telco provides the Internet services on the "outside" interface.

---

### Post by superprash2003 on 2008-07-29
typically cable connections require dialing.. so i guess you would need to create one by typing sudo pppoeconf ..and regarding the xxxx part ..post no 3 and 4 should be helpful..depends a lot on your current setup

---

### Post by chili555 on 2008-07-29
> **superprash2003 said:**
> typically cable connections require dialing.. so i guess you would need to create one by typing sudo pppoeconf ..and regarding the xxxx part ..post no 3 and 4 should be helpful..depends a lot on your current setupWhen I had cable, it did *not* require dialing, that is, PPPoE. Now I have DSL, and it's protocol *is* PPPoE, but the authentication is handled in my Linksys router. As far as I know, I would only have to be concerned about PPPoE if I hook my computer directly to the DSL modem.

I believe this will be a perfectly fine static setup:```
auto eth0
iface eth0 inet static
address 192.168.1.151
netmask 255.255.255.0
gateway 192.168.1.1
```And please do not touch the lo entries.

Be sure the address is outside the range of the DHCP server. My Linksys, by default, assigns up to 50 addresses, starting at 192.168.1.100.

After you have this in place in *interfaces*, please do:```
sudo ifdown eth0 && sudo ifup eth0
ping -c3 www.google.com
```If you get ping returns, you are all set.

---

