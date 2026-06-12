---
title: "Network printing with dynamic ip"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by borobudur on 2008-02-12
Hi there,
I'm using network printing. This printer is on my main machine which has a dynamic ip.
It's a bit ugly on my clients because there it stores the ip (/etc/printcap) of the remote default printer. Like this I need to set each time the default printer before printing.
I didn't see anything in the /etc/cups/printers.conf file to set the url.

Is there a solution for that problem?

---

### Post by chili555 on 2008-02-12
Why not use a static IP address on your main machine with the printer attached? In my home network, all the desktops (including the one with the printer) have static IP's and the laptops, that may need a dynamic IP at the coffee shop hotspot, use DHCP. Works well for me.

---

### Post by borobudur on 2008-02-14
I have a wireless router which does the dhcp stuff. There I forward the dynamic ip to the main computer. So it is accessible from the outside. 
As much as I know, it isn't possible to have a static ip on that machine.

---

### Post by borobudur on 2008-02-29
hey, I still have this problem here. Has anyone an idea? Static ip doesn't work for me, to expensive :(

---

### Post by volkswagner on 2008-03-01
I am no expert.  It seems to me you may have a little confusion on your dynamic IP being forwarded to you machine.  Is it you lan ip ie 192.168.1.xxx getting forwarded to the outside world?   Or is it the ip issued by your internet provider more like 71.74.xx or whatever?

On my lan my router issues DHCP to all machines.  Even if I remove, replace, or change lan ports my linksys router 99.9% of the time issues the same ip address to each machine.  I have a network printer which I set the lan address as the location in cups.  It has yet to fail to connect.  I have yet to get around to setup static ip's on my lan.  This quest has landed me here.  I think the previous poster has an excellent idea.  I will be setting my desktop machines to static, and leave my lappy to dhcp.  As soon as I find out how.

---

### Post by borobudur on 2008-03-02
Yes, usually all machines get the ip from the router (192.168.x.x) but because of my dynamic address at dyndns.org I set ip-forwarding to my main machine so just this address looks for all like 84.75.x.x. 

I don' t know of a way that my main machine could have two ip addresses:
the dynamic from the provider (he changes the addresse all the time) and a static  like 192.168.1.2 for the inside world.

Does that exist?

---

### Post by Eiríkr on 2008-03-02
Okay.  You've got two different dynamic IPs at issue here.  Only one of them is likely relevant to your network printing question.  

1) The dynamic IP assigned for web-wide use by your ISP.  This is what DynDNS helps you keep track of, so you can type in "http://www.your_server.org/" and see your website even from a friend's house or the library public terminals.  

2) The dynamic IP assigned within your home network by (most likely) your router.  This is what you'd probably want to switch to a static IP.  

My setup sounds vaguely similar to yours.  I've got my web-wide IP that changes every week or so, depending on what I'm doing, which I've got set up through DynDNS so I can do fun stuff like serve up web pages to family or ssh into my machine from elsewhere in the web.  My DSL modem is the only thing on my end that has anything to do with this web-wide IP address, and it handles it all automatically.  

Connected to the DSL modem is my D-Link router (would have gotten a LinkSys if I'd known better, but there you go).  This has a built-in DHCP server turned on by default, as do most consumer-grade routers, that assigns IP addresses to my home machines.  If I want and know what I'm doing, I can log into my router's admin pages and change this to use static IPs instead, based on the MAC addresses of the network cards in each of my home machines.  So my router's address defaults to 192.168.0.1, while my main workstation is assigned to 192.168.0.10, my iBook is 192.168.0.12, my wife's iBook is 192.168.0.15, and my network printer is 192.168.0.100.  

(Incidentally, most every network-capable machine these days automatically has multiple IP addresses by default - the one associated with the network card, and the loopback address of 127.0.0.1.  Multiple other IP addresses are also possible.  Open a terminal and type [font=courier]ifconfig[/font] to see your network **i**nter**f**ace **config**uration, showing your loopback and ethernet interfaces, and any others you might have.)

HTH,

Eiríkr

---

### Post by borobudur on 2008-03-02
I totally agree with you. I have almost the same situation except the ip of the main computer. I solved the access form the outside world with ip forwarding. 

I can't find anything to configure my [FONT=verdana][SIZE=2]Netopia router that I could set static ip's to the inside world, especially the translation from outside with 84.1.x.x to the inside main machine with something like 192.168.1.2

How is that called in your router configuration panel?

[/SIZE][/FONT]

---

### Post by Eiríkr on 2008-03-02
I'm looking at it right now as I try to configure the router's firewall and logging options (woefully over-simplified; I may need to go buy a different router that is OpenWRT-compatible and install a *real* firewall).  On the D-Lin WBR-2310, I click Setup -> Network Settings, and on this screen I can see the DHCP server settings.  The two ways to configure fixed IPs here is to use what D-Link calls a DHCP Reservations List, where I can assign specific addresses to each machine based on the individual machines' MAC (network card) addresses.  The router's own help hints say:
> 
**DHCP Server:**
If you already have a DHCP server on your network or are using static IP addresses on all the devices on your network, uncheck **Enable DHCP Server** to disable this feature.
[B]
DHCP Reservation:[/B]
In order to ensure that devices on your network are always assigned the same IP address, add a **DHCP Reservation** for each device.

I'm not at all familiar with Netopia, but hopefully this will give you some hints.

HTH,

Eiríkr

---

### Post by borobudur on 2008-03-03
Unfortunately it seems it's not possible with my router. The only thing I can do is setting the range of the dhcp/ip numbers. The only place I can set the mac addresses is in the wireless section, the access control by mac address.

So, I guess the only choice I have is the ip forwarding where I have the problem that my provider changes the ip every 4 hours.

But thanks for your help!

---

### Post by Eiríkr on 2008-03-03
IP forwarding from an ISP is only really useful for network printing if you're trying to print to your home printer while somewhere on the road.  Is this what you're looking to do?  For accessing one machine in your home LAN from another machine in your home LAN, I don't think your ISP could help, but I could be wrong.  

Another thought -- I think if you set your router's DHCP range to, say, 192.168.0.100-254, and then in each machine go into network config and set static IPs under that, say 192.168.0.10-20, and then make sure the /etc/hosts files on all machines include everyone's hostnames and proper IPs, you should be able to make use of fixed IP addresses without having to muck about with MAC address assignment on your router.  

Cheers,

Eiríkr

---

### Post by borobudur on 2008-03-04
Thanks [Eiríkr]("http://ubuntuforums.org/member.php?u=468055") for your patients. With your thought I still have the problem that my main machine has the dynamic ip. 
Otherwise how can the router know to whom it needs to send the outside packages? For this I can find just the ip forwarding in the router config panel.

---

