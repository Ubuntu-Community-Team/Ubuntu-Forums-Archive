---
title: "What can be done with a Linux router? Help me &quot;Trick it out&quot;"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by tuproxy on 2007-12-15
I want to create a Linux router out of a P3 1Ghz 256mb ram (could be 512mb if needed).

I want to know all the cool things that can be done with this machine.  What features can I add to the router.

I want to have 2-3 NIC's and Wireless
NIC 1  Input
NIC 2  DMZ
NIC 3  LAN
Wireless  - obvious!
Does this make sense?

I want to make this an in-depth project.  I'm going to make  create a blog with the step by step instructions on how to do this.

I want any an all suggestions that you think would be great to add to a router.

NAT
QoS
VoIP
VPN
FTP
Web Server?

I'm not sure what else could be added but I'm sure you people could figure out what else could be added.

Please lend me your ideas.  Much thanks!!:)

---

### Post by tgalati4 on 2007-12-16
Depending on  your electric rates, it would be cheaper to buy wireless, 4-port router with built-in firewall.  If its a common Linksys model then you can put an open source firmware to tweak it some. 

A PIII probably burns 90 watts continuously.  24/7 operation will burn 788 kwh per year.  At 11 cents per kilowatt that's $87 per year.  At 14 cents per kilowatt that's $110.  You can buy a decent router for $40 and it will burn 10-15 watts.

---

### Post by tuproxy on 2007-12-16
That is a considerable difference!  Thanks for the input.  I think I'll stick with a consumer router.

Well, I'd still like to build one anyway, just for the experience.  Any suggestions as to what to add on top of the items I listed above?

---

### Post by mjpolifka on 2007-12-16
Go to [aboutdebian.com](http://aboutdebian.com) for an in depth tutorial on not only networking as a whole, but using iptables to set up a nat proxy.  I did it with an old computer so I could have a gigabit router, since I was already using the machine as a web and ftp server.  This way I'm actually saving money, since the server would be up constantly anyway, eliminating the extra power of a router.  The one thing I wanted to do but never got around to is wireless.

For the web server, we use apache (duh).  For ftp I think we're using wu-ftpd, and using secure ftp (sends everything through an ssh tunnel), though on another machine i'm using proftpd without the secure feature, so I could send ftp commands in a bash script (does anyone know how to use sftp in a bash script?).  I also have both ssh and webmin for administration, and using dyndns.com to map the internet IP to a free hostname for when I want to access it from outside the network.  I use samba to map the media drives (music and video) so that windows media player can use them as the library, which frees up a lot of hard drive space (my roommate was running vista on only 40GB with WoW and Ghost Recon installed).

VoIP shouldn't be that hard, I believe it's a simple daemon like ftp or apache.  I know that ventrillo has a linux server daemon, but no linux client.  I don't know what QoS is (I'm mostly a noob, I just started last summer), and I'm not sure what a VPN really does, all I know is it means virtual private network.

Good luck, let me know if you want any help.

---

### Post by Archmage on 2007-12-16
What you can do with a router that is 24/7 on:

DNS-Server
Mailserver
Apt-Proxy
MythTV

Deepending on your laws you can use it to download your favourite internet-radio.

---

### Post by tuproxy on 2007-12-16
Thank you, that's exactly what I am looking for!!  I just want some cool projects to setup.

---

### Post by tuproxy on 2007-12-16
Would running a router on a virtual machine be an option?  I am going to have a virtual server running all the time, so I could dedicate a small portion of the system to a router.

Any suggestions?

---

### Post by mjpolifka on 2007-12-17
> **tuproxy said:**
> Would running a router on a virtual machine be an option?  I am going to have a virtual server running all the time, so I could dedicate a small portion of the system to a router.

Any suggestions?
you just need to run the iptables script, so that should work.  I don't really know what a vm is or does, so I don't know exactly what you can do with it.

---

### Post by kustomjs on 2007-12-19
One Word Smoothwall for linux router

---

### Post by yogakills on 2007-12-21
Have used smooth wall in the past. Very slick and easy. Minimal mucking about for maximum features. 
Definitely worth a look. 

There are also a few distros dedicated to specific network tasks. eg for NAS have a look at

[freenas]("http://www.freenas.org/")
[naslite]("http://www.serverelements.com/naslite.php")
[openFiler]("http://www.openfiler.com/")

save the hassle of setting up a samba server on an other distro and disabling all the stuff you dont want running.

I have a desktop that double as a smb server. tho not ideal because it make to much noise with the crummy old PSU. eventually i will migrate to one of the solutions above and shove it up in the loft. Out of the way and out of sight.

Have a merry Christmas y'all.

---

### Post by trobbins on 2007-12-21
Smoothwall is OK but I don't think it supports OpenVPN out of the box.  I use Endian as my  router/firewall distro.  It fully implements OpenVPN and uses the TAP interface (basically ethernet bridging).  I use this so that ARP, broadcast, and multicast packets get routed correctly.  This is required for many video games.  For very minimal routing, I use BrazilFW, a 1.44 meg distro.

BTW, you don't need anything faster than a 133mhz PC unless you are going to start using it for encoding video and such.

---

