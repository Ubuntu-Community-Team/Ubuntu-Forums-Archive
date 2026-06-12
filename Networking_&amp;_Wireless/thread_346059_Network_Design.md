---
title: "Network Design"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by Linuturk on 2007-01-25
I need help designing and implementing my network.

First, let me layout the hardware.

1. Ubuntu 6.06 Server - Desktop
2. Ubuntu 6.10 Workstation - Laptop
3. Kubuntu 6.10 Workstation - Laptop
4. Windows XP Pro Workstation - Laptop (hardly used, but needs access to all network services)
5. HP Laserjet 1100 Printer
6. D-Link Network Storage Device
7. Linksys WRT54G Wireless Router

My internet is provided by my apartment complex in the form of a wireless cloud over the entire building. Whoever set this stuff up is a pro. I do not have ethernet cable access to my internet source. 

Fortunately, I have a wireless USB dongle that gives my server (1) access to the internet. 

Here is what I have in mind.

Internet > Server via Wireless > Linksys via Ethernet (into the Internet port on the Linksys) > Other devices via my wireless network (not the apartment complex's)

My first question is, can I do this and/or is this a solid network plan?

My second question is, obviously, how do I do this?

From my research so far, my server is going to have to provide the following services.

1. Samba
2. NFS
3. Print Server
4. Squid Proxy Server with Antivirus scanning
5. DNS
6. DHCP
7. Firewall/gateway 

I'd like to know your thoughts on this setup, and any tips you can give me that will assist me in a smooth setup.

---

### Post by Nik_Doof on 2007-01-25
I think you'll be able to configure your linksys router as a wireless bridge by setting into client mode. Not sure if this can be done in stock firmware, but will be possible in many of the open firmwares out there. 

This will only be useful if you want a pure wired network.

---

### Post by netztier on 2007-01-25
> **Linuturk said:**
> 

Internet > Server via Wireless > Linksys via Ethernet (into the Internet port on the Linksys) > Other devices via my wireless network (not the apartment complex's)


My first question is, can I do this and/or is this a solid network plan?


Hm. I wouldn't do it quite that way. From a pure networkers' point-of-view, I suggest separating Routing/Firewalling from File and Print Services. Proxy Services could be done on either.

First thing to find out: what security mechanisms does the "campus WLAN" implement? WPA-PSK? WPA2? WEP? EAP-TLS etc? This information has to be available from the WLAN admins.

Then setup a routing/firewalling device that connects to the campus WLAN. This could be:
[LIST]
[*] a Linux box witha WLAN card or USB stick as "outside interface" and an ethernet NIC ("inside"). It performs routing functions, and runs a firewall. You can also run a forwarding-DNS and a DHCP on it, serving requests from the "inside" interface only. 
These functions are often summarized as "internet connection sharing", and you can configure this system as such. There should be plenty of HOWTOs around in this area.
[*] a WLAN client device (such as a *non-router* WLAN access point in "Wireless client" oder "wireless bridge" mode) that is compatible with your campus WLAN, combined with a normal wireless broadband router (typical: Linksys WRT54G), connected to the WLAN client device on it's "internet/WAN/outside" port.
[/LIST]

As "inside network" you use:
[LIST]
[*]a simple switch you connect your internal Server, NAS devices, print servers etc. to. If needed, add a separate WLAN access point if you need wireless for your own inside network. Connect your separate File/Print Servers and Clients to this internal (W)LAN.
[*] workong with the WLAN Client/broadband WLAN router combination, you can use the router's integrated 4-port switch and integrated WLAN access point for your "inside" network, and connect the internal Systems to this (W)LAN. 
Make sure that your private WLAN uses a frequency with a gap of at lest 4 channelsto the campus WLAN (or any other WLAN in the air), or *both* will suffer performance degradation because of interference.
[/LIST]

This setup is basically similar to your idea. In my opinion your plan has one major drawback: the "server" is going to be outside the router: performance will suffer, because a Router will hardly ever be as fast as a switched ethernet connection. Plus, with the router's NAT/PAT and firewalling functions, you'll have "one-way" communication between your internal LAN and the Server (unless you configure it otherwise, upon which it loses it's intended function).

A setup like yours might actually be desirable if you intend to have a host in a DMZ, but my experience is that hinders more than it helps. If you really want a DMZ, then use a Linux box as firewall/router with a separate third interface and small LAN segment where you'll connect your server - but we're getting more and more advanced here .. :-)

best regards

Marc

---

### Post by Linuturk on 2007-01-25
> I think you'll be able to configure your linksys router as a wireless bridge by setting into client mode. Not sure if this can be done in stock firmware, but will be possible in many of the open firmwares out there.

Unfortunately, I have the v6 of the WRT54G. Linksys really cut the hardware specs on every router v5 and up.

> Hm. I wouldn't do it quite that way. From a pure networkers' point-of-view, I suggest separating Routing/Firewalling from File and Print Services. Proxy Services could be done on either.

I am limited on the fact that I only have one desktop computer.

> First thing to find out: what security mechanisms does the "campus WLAN" implement? WPA-PSK? WPA2? WEP? EAP-TLS etc? This information has to be available from the WLAN admins.

They run an open network as in no encryption types. They do, however, filter everything on MAC addresses, and everyone is apparently on a different subnet because I can't ping any other machines on their network. Just me and the gateway.

Let me upload a drawing of my idea.

---

### Post by netztier on 2007-01-25
> **Linuturk said:**
> 
I am limited on the fact that I only have one desktop computer.


That'll make it the server then. 

> **Linuturk said:**
> 
They run an open network as in no encryption types. They do, however, filter everything on MAC addresses, and everyone is apparently on a different subnet because I can't ping any other machines on their network. Just me and the gateway.


Hm, not necessarily a single subnet. My memory might be failing me, but I think that on professional WLAN equipment, there is a configurable option that prevents WLAN clients from talking to each other, very much like the "private VLAN edge" feature on Cisco Switches. Systems connected to so-called "protected" ports can't talk to each other, but they can talk to the non-protected ports (where you'd connect the router).

> **Linuturk said:**
> 
Let me upload a drawing of my idea.

Ah - this is looking good, and is pretty much the same as I meant to suggest. The drawing helped to clarify your idea, thanks a lot!

Picking up your thoughts from text and drawing, here's what I think you can/should do:
[LIST]
[*] plug the USB dongle directly into the server and use it to access the community WLAN (outside interface)
[*] on the server, run "everything" ;-): File services, Print Services, DHCP, forwarding-DNS, Web Proxy. Be careful to configure all deamons to listen to the internal interface *only*. (unless of course you want them specifically open to the community...)
[*] run routing/NAT/PAT and firewalling services on the server
[COLOR="Red"][*] On your WRT54G, ** deactivate** DHCP service, firewalling and routing, and remember the thing with the WLAN channel gap from my previous posting. *Basically, you reduce this router to a 4-port switch with an integrated WLAN access point.*
[*] connect the server to the **internal** ports of the WRT54G. 
[*] if there's other PCs or Laptops, also connect them to the internal ports of the WRT54G. [/COLOR]**Yes**,  your private WLAN is the "5th internal port" on that device. ;)
[*] use some good encryption/access control mechanism on your private WLAN. Maybe even something fancy that uses RADIUS service on your server to authenticate the clients...
[*] be happy :-)
[/LIST]

One question about the NAS box: does it offer SMB and/or NFS natively and do you intend to use these directly from your client systems, too? In that case, it should go straight to the "inside" network (do yourself a favour and use a wired connection for both the server's inside and the NAS box).

If however it is "iSCSI-style", where a special driver makes the drives look like locally attached harddisks, I'd consider connecting it directly to the server, to a third NIC via crossover cable (as your drawing suggests).  In that case, the hassle of installing the special driver only occurs once (on the server), and the clients use Samba or NFS to access the shares the server offers them.


best regards

Marc


[SIZE="1"]PS: with a setup like that, a next idea could be installing OpenVPN on the server and on the mobile clients, so you can access your home network and services from anywhere on the internet (provided the IP address you get on the community WLAN is routable from the internet, of course.). I am currently planning on setting up something like that home, but first things first: winter holiday in the sun :-)[/SIZE]

---

### Post by Linuturk on 2007-01-25
Thanks for all the feedback.

> One question about the NAS box: does it offer SMB and/or NFS natively and do you intend to use these directly from your client systems, too? In that case, it should go straight to the "inside" network (do yourself a favour and use a wired connection for both the server's inside and the NAS box).

That is actually a tough question. The D-Link actually runs linux as it's operating system, with Samba! The only problem is, I don't think I have access to the lower level functions (aka terminal) for configuring it. I have to use the web interface, and that is built around Samba apparently. 

D-Links page on the NAS: [http://www.dlink.com/products/?sec=1&pid=377](http://www.dlink.com/products/?sec=1&pid=377)

Picture is attached.

The only problem with my current service is, I don't have control of the outside firewall and I don't have an external IP I can connect to for remote ssh or VNC. Other than that, it looks like this is the way to go!.

---

### Post by netztier on 2007-01-25
> **Linuturk said:**
> The D-Link actually runs linux as it's operating system, with Samba! The only problem is, I don't think I have access to the lower level functions (aka terminal) for configuring it. 

Doesn't matter. In that case, it's best to connect that box directly to the LAN. 

Come to think of it... 

Will you be using all your laptops with WLAN? Then there's no need for a separate "internal" LAN. Just connect the D-Link NAS/WLAN-Box directly into the server's "inside" NIC, and configure it as WLAN access point for your private WLAN. That's all there is to it. No internal (wired) LAN, no reconfiguration of the WRT54G etc.

However: The NAS box only offers Samba, NFS doesn't seem to be available. I can't tell by heart if you could mount a share via Samba on the server and re-export it via NFS for your clients.  Will you be able to do with Samba only, when accessing files from that box? If yes, there's no reason not to buy it!

There's just one thing. This is going to be a 54Mbps (nominal) WLAN. You'll see throughputs in the ~25Mbps range, that's a mere **2-3 MBytes/s**. Should you intend to move larger amount of data (say, your MP3 and video collection of a few dozen GBytes) over such a slow network, you won't have any fun. 
Just do the math: *2-3 MBytes/sec * 3600sec = **7-10 GBytes/h*** are not what you'd call a "quick backup before you go". Hence my strong suggestion to connect that box to the wired part of the LAN.


> **Linuturk said:**
> 
The only problem with my current service is, I don't have control of the outside firewall and I don't have an external IP I can connect to for remote ssh or VNC. Other than that, it looks like this is the way to go!.

Hum, without a public IP address, it is definitely going to be dfficult, agreed.

best regards

Marc

---

