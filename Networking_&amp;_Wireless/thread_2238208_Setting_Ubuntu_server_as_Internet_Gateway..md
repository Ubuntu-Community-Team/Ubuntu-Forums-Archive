---
title: "Setting Ubuntu server as Internet Gateway."
date: 2014-08-06
forum: Networking &amp; Wireless
---

### Post by kannuruser on 2014-08-06
Hi,
Friends, im stuck up with problem regarding to network configuration to make my Ubuntu 14.04 server machine as internet gateway in a LAN, and I am a relatively newbie in this regard.
My scenario is as follows.
ISP Address 59.X.X.10
ISP Gateway 59.X.X.1 (as seen from modem router)
Netmask 255.255.255.255 ( " )
Modem Address : 192.168.1.1
I edited the /etc/network/interface file as
```
auto eth0
iface eth0 inet static
address 59.X.X.10
netmask 255.255.255.255
gateway 59.X.X.1
network 59.X.X.0
broadcast 59.X.X.255
dns-nameservers 8.8.8.8 4.4.4.4

auto eth1 
iface eth1 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

```
now when I save and restart the service, i cannot even ping to 192.168.1.1 or get internet connection from this server machine itself. I also tried to change gateway of eth0 to 192.168.1.1 , but no good.
Where am I wrong,? Do I have to make any particular changes to my broadband modem router?

---

### Post by TheFu on 2014-08-06
For the vast majority of people, using a router distro if you want an internet gateway is easier than trying to configure Ubuntu for the same task.
* ipcop
* pfsense
* smoothwall
* sonicwall
* Zentyal 
* ClearOS

You'll need to talk with the ISP about their modem's capabilities. I doubt that with a single IP you can take over the public IP on an internal machine.  I suspect that double-NAT will be the only solution.  Might be easier to get a $20 cheap home router and use that for your gateway.

I had to setup 1-for-1 routes on my business connection to gain access to the extra public IPs provided by my ISP.

---

### Post by SeijiSensei on 2014-08-07
Why do you want to replace the existing router?  Perhaps if you explain what you want to accomplish we can be of more help.  You can always put a Linux box behind the router if you want greater control over your connection.

---

### Post by kannuruser on 2014-08-08
Hi friends,

At present i am having a Iball Baton ADSL2+ Router, through which i can connect all my computers in the LAN to the internet. Now i want to have an ubuntu server behind this router so that i can control the network connection, which would act as a gateway, dhcp server,  proxies and all those things. 

I have an internet connection with a static IP mentioned above, and I plan to have that static Ip assigned to this server, so that I can access some of the software and websites hosted on this server over internet too. !

---

### Post by TheFu on 2014-08-08
> **kannuruser said:**
> I have an internet connection with a static IP mentioned above, and I plan to have that static Ip assigned to this server, so that I can access some of the software and websites hosted on this server over internet too. !

While this makes sense, but it isn't how things are normally accomplished for what you describe.

Most of the time, we have the router just as it is in your setup. The router WAN interface has the public IP and the router forwards only those specific ports for specific services into specific internal static IPs & ports on systems running on the LAN.  That means your Linux system will need an internal static IP - that is easy enough.

What this doesn't do is provide bandwidth tracking, but there are solutions for that too.  Most current-gen routers support SNMP and through the configuration, we can tell them to report that data to any system on our LAN. BAM, bob's your uncle. You've got a separate firewall, haven't needed to purchase an ADLS card for any PCs, and haven't completely thrown out security for your Linux system and LAN. Plus can see bandwidth use charts using many different tools thanks to SNMP.  Oh - be careful when you enable it - SNMP is a cracker method to access networks.

I hope that makes sense?  Check out  [http://www.ratemynetworkdiagram.com/](http://www.ratemynetworkdiagram.com/) to get a feel for how others do this stuff. Diagrams really do help.

Or are we missing something critical?

---

### Post by kannuruser on 2014-08-10
Hi, TheFu, yeah... i think, if need to provide public IP to my linux machine, I  have to make the router act just only as a bridge and then make my server the actual router. 
With the DMZ option in the router, i think, we can actually access the local machine using the public IP from outside. 
But, which one is the better solution? making Linux machine as the router and make the modem as bridge or ... just make the router as it is and make the linux machine just forward the communication through 2 interfaces with private IP.?

---

### Post by TheFu on 2014-08-10
Don't use a DMZ. That is the lazy, non-secure, way, fraught with danger.

Make use of the existing router and have it use SNMP to provide bandwidth information back to a system on your internal network. Sure, you could dedicate an entire machine to be the internet gateway, but why? The gateway machine needs to serve a single purpose, this is a security principle. If it is already serving other needs, then that machine probably is NOT appropriate to use as a gateway/firewall too. There are different opinions about this - but in the corporate world, this is how things are designed. Security is layered for many good reasons and ignoring that is a poor idea.

I'm not here are tell you how to do X - google will handle that and a few other people here will too.  I'm here to tell you why X isn't the best idea and hopefully convince you to do a little more research so you setup the situation like most corporate networks do it. Tried and proven methods to avoiding "reinventing the wheel" whenever possible.

Of course, only you can decide which technique is best for the situation, but whenever someone says they are new, it would be smart to follow well-known tracks and do it that way.  Setting up a gateway requires strong OS knowledge and there are hundreds of details to be addressed.  It is more than setting up ip_forwarding and enabling the routing tables correctly, much more, though that is all it takes to get it _*working*_ - I hope working isn't all you desire - **secure** should be a higher priority than *working*.

---

### Post by nix_weasel on 2014-08-11
I think i know what you are after (kinda) and i can see where you are going wrong,
what im seeing your setup looks kinda like this

 <<[COLOR=#000000]ISP Address 59.X.X.10:[/COLOR]your router isp side> (nat to)<[COLOR=#000000]Modem Address : 192.168.1.1[/COLOR]>>----<<[COLOR=#000000][FONT=Ubuntu Mono]address 59.X.X.10:your eth0(plugged in to router??) (Your server Nat? to) [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]address 192.168.1.2:your eth1(local networkside)[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]>>

 so in the chain your describing you have the same ip address twice and that is why you cant get internet access (eth0 & your router isp assigned ip are the same and that confuses the network as to where to send the information next) the other problem is in a double nat like this you have your local network on the same ip range as your router to server connection (even though its set up wrong anyway :)) and that confuses the second nat, i would do it like this 

59.x.x.10<router>192.168.1.1 === 192.168.1.2:eth0<server>192.168.0.1:eth1  (or even 10.0.0.1/10.0.0.2 router to server link and 192.168.0.1 for your local network

 as for the rest if your talking about say accessing mp3 from the internet maybe look into a Virtual private network setup?

the only way i know of to have your server have the isp address is to install a adsl? modem pci/pcie/usb directly[/FONT][/COLOR]

---

