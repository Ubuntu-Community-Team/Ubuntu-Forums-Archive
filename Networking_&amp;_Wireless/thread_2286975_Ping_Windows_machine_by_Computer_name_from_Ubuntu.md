---
title: "Ping Windows machine by Computer name from Ubuntu"
date: 2015-07-16
forum: Networking &amp; Wireless
---

### Post by Nathan_Veysey on 2015-07-16
Hello, 

I’m attempting to configure a Varnish server to run from an Ubuntu server to an IIS web server, hopefully this can be done by Computer name, but I cannot ping the windows machine by computer name. The Machine is visible under Computer>Network and can ping from the IP address.

The Ubuntu server is pingable from the Windows Machine and are under the same Workgroup.

This is a development environment, where the IP addresses are at times subject to change (more than I would like) but binding the IP addresses appears to cause more problems than I would like, so attempting to sort this out by the names to avoid IP change problems.

Is there something I need to do to get this to work, or something I’m missing? 

Thanks

---

### Post by TheFu on 2015-07-16
There are standard IP protocols - DNS is the main one.  

MSFT made up their own before they used IP with netbios. Machines broadcast to the LAN that they are there. That doesn't scale well for large LANs and cannot be routed, so they invented another non-standard protocol call "WINS" - which can be routed.  When you "browse"  the network using a file browser, that is using CIFS as the protocol. It is a standard just mainly used for Windows. Samba provides this for CIFS through the nmbd process. Not used by other protocols like ssh, sftp, http, .... just CIFS.

So - what can you do to make this work? There are a few options.
* setup a DNS server and enter all the hostname/IP mappings. CON: IPs cannot change.
* In your router, setup DHCP reservations and DNS based on MAC address, IP, hostnames - easy for some routers, impossible for others [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)
* Modify your /etc/hosts file on **every** system with the IP to hostname mapping. This can be tedious on Windows (admin access is required).  It can be automated using ansible/puppet/scripts on Linux. There can be other great side effects: [http://blog.jdpfu.com/pages/hosts-for-security](http://blog.jdpfu.com/pages/hosts-for-security)
* Use Bonjour protocol - also called ZeroConf and implemented by Avahi. Basically, if you name the hosts to "server.local", the avahi protocol will announce/broadcast the hostname on the network. [https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)  - I've had issues with it exploding CPU use above 90% for hours a few times on a few systems, so I generally purge it (just like nano).

For my small network (only 20 machines), I use static IPs for all servers/workstations, /etc/hosts managed through ansible and DHCP reservations for all portable devices (laptops, smartphones, media devices that suck to enter IPs manually).  I will probably switch to a DNS server if we grow any larger.

So - which do you want to try?

---

### Post by Nathan_Veysey on 2015-07-16
> **TheFu said:**
> There are standard IP protocols - DNS is the main one.  

MSFT made up their own before they used IP with netbios. Machines broadcast to the LAN that they are there. That doesn't scale well for large LANs and cannot be routed, so they invented another non-standard protocol call "WINS" - which can be routed.  When you "browse"  the network using a file browser, that is using CIFS as the protocol. It is a standard just mainly used for Windows. Samba provides this for CIFS through the nmbd process. Not used by other protocols like ssh, sftp, http, .... just CIFS.

So - what can you do to make this work? There are a few options.
* setup a DNS server and enter all the hostname/IP mappings. CON: IPs cannot change.
* In your router, setup DHCP reservations and DNS based on MAC address, IP, hostnames - easy for some routers, impossible for others [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)
* Modify your /etc/hosts file on **every** system with the IP to hostname mapping. This can be tedious on Windows (admin access is required).  It can be automated using ansible/puppet/scripts on Linux. There can be other great side effects: [http://blog.jdpfu.com/pages/hosts-for-security](http://blog.jdpfu.com/pages/hosts-for-security)
* Use Bonjour protocol - also called ZeroConf and implemented by Avahi. Basically, if you name the hosts to "server.local", the avahi protocol will announce/broadcast the hostname on the network. [https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)  - I've had issues with it exploding CPU use above 90% for hours a few times on a few systems, so I generally purge it (just like nano).

For my small network (only 20 machines), I use static IPs for all servers/workstations, /etc/hosts managed through ansible and DHCP reservations for all portable devices (laptops, smartphones, media devices that suck to enter IPs manually).  I will probably switch to a DNS server if we grow any larger.

So - which do you want to try?

Thanks, some good information in there. Its been a long time since Ive actively worked on Linux so feeling a bit green.

Ive got a Draytek Vigor 2710 router - which allows IP to mac address binding however for some reason this appears to cause our mobile phones to not be able to connect once they leave and come back in and occasionally there are network issues that do not occur when the Mac binding is disabled (Mostly machines not being found - no idea why).
  
I may be able to get away with simply mapping the Hosts file, /etc/hosts on Ubuntu, Ill see how that goes as a test this evening - Windows can see Ubuntu via the Computer name without the hosts entry so may not be a big issue if this works.
But the *Bonjour protocol looks like a good option? though 90% CPU doesn't sound great, do you purge it on a schedule?

Its a development environment so not mission critical, there are only 3  development machines (These are windows web servers) which for the most part most wouldn't need to  address the varnish cache a lot of the time. We have the odd power cut  around here in peak Holiday seasons Wanaka, New Zealand, Will setting up Bonjour save much hassle (Long term there may be more machines in the network - but I may be being hopeful)

What would you recommend?

---

### Post by Morbius1 on 2015-07-17
Just a comment on one specific item of your post:
> Will setting up Bonjour save much hassle (Long term there may be more machines in the network - but I may be being hopeful)
mDNS ( Bonjour, Avahi, Zeroconfig, etc ... ) name resolution is way faster than the netbios mechanism in Windows. At least in a home lan environment.

There's a problem however. Windows doesn't do mDNS by default. You would have to install an Apple addon to your Windows system and for a  Web server I would think that would not be a good idea. OSX has it  enabled at all times but Apple has 10+ years experience with the thing.

This all changes with Windows 10 however. Win10 does mDNS out of the box - not as automatically as Linux and certainly not like OSX would do it but machines can be explicitly accessed with a hostname.local.

---

### Post by TheFu on 2015-07-17
"purge" means "wipe from the system" - so I do it once.

90% CPU happened to me. I suppose it doesn't happen to everyone. However, it happened to me on multiple machines, multiple times, before I decided it was just easier to purge, since I was already managing my network.

Only you can pick which level of hassle you'd prefer. I provided options, each has some downside. Never heard the term "Mac binding" - "Interface bonding" means something completely different which is what my brain filled in at first. Pick your poison.

If you have an all-in-one modem/router from the ISP - you can go get a $20 personal router and do double-NAT. That new router should be well-know to support DD-WRT, then you'll know that it can do the DHCP reservations +DNS properly.  I don't trust my ISP's router, so I have a few other routers connected and split off different network for the house. It is an option, but then you'll want to setup port forwards for ssh more carefully.  A house without an ssh server running and available to the world - I cannot imagine that.

---

