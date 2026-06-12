---
title: "problem with home network"
date: 2015-03-08
forum: Networking &amp; Wireless
---

### Post by jgw on 2015-03-08
I am running with ubuntu 14.10  I have a small home network of 3 windows machines and 4 ubuntu machines.  I can access 2 of the windows machines and 2 of the ubuntu machines.  Some of the machines are wireless and some are not.  Some of each can be accessed.  This machine, for instance, cannot be accessed.  When I try to access this machine, by going to files, browse network I can see this machine.  Its also listed in the workgroup.  In spite of that I cannot access the network, from this machine, to access this machine!  I am, obviously, doing something very strange.  I have examined my samba settings and they seem to be the same for all machines.  This is also true for checking my network connections, etc.   You can find the results of 3 of these machines (ifconfig) at [http://pastebin.com/G8yGSPwU](http://pastebin.com/G8yGSPwU)    The current machine does appear from arp-scan but can still not be accessed (all those that cannot be accessed ask for a password and then rejects it - ALL machines have the same basic password)

Any thoughts would be appreciated - thank you.................

---

### Post by TheFu on 2015-03-09
Did they ever work? Is this a new issue?

Can you bring the tunnel down?

---

### Post by jgw on 2015-03-09
Thank you for the reply.  I don't know what bring the tunnel down means.  I have, basically, two machines that cannot be accessed.  One is a new installation and the other is one that is my main machine, in this location.  All the others work just fine.  I am not knowledgeable enough to figure this one out.  In other words, I have setup two machines out of 7/8, on the network (listed, say, when browsing the network from files) that cannot be accessed.  I click on one of the bad ones and it asks for a password and then keeps on asking.  I have exactly the same password, as far as I can tell, on all of the machines on the network.  I can even live with it but it is a constant irritant and would like to figure it out and make it work and I am pretty stubborn.  The fact that one of the machines I cannot access, when clicked on, is THIS machine (I cannot access the machine I am using) tends to make me believe its setup wrong - I just have no idea why or how <sigh>

---

### Post by TheFu on 2015-03-09
Your pastebin show that there is a tun0 device on at least 1 of the machines. Turn it off. This is definitely something that someone enabled, not a default thing.  Tunnels can mess with routing. Routing can prevent machines from being able to talk even if they are on the same subnet.

Something like **sudo ifdown tun0**  ... of course, I didn't look up the actual tunnel device today - you can do that.

This is probably the last I can help.  Sadly, I've been doing this stuff for so long that I've lost the ability to communicate effective with people really new to Linux and/or networking. We'll both just get frustrated. Sorry for my failure.

---

### Post by jgw on 2015-03-09
Thank you for the reply.  

I tracked down tun0 - it was part of PIA (personal internet access - VPN).  If I exit that the tun0 goes away.  That, however, doesn't change anything.  I can't help but think that my main problem is that I have an unknown password as it just keeps asking for my username and password for WORKGROUP.  When I try to access any of those that are accessible it never asks for a password so I suspect I have cleverly passworded something but have no idea what. 

Its pesky.  I will leave this one open, for a bit, and possibly somebody else has come across this one.

thanks again!!

---

### Post by TheFu on 2015-03-09
On Ubuntu servers, the SMB password DB needs to be initialized with useruids.  That is done by using the **smbpasswd** tool and setting a password. Could that be needed on a desktop install?  Otherwise, how will samba know which users to allow (or not)?

I'll give a solution a shot.  Microsoft decided to use broadcast protocols. Everyone else on the internet doesn't.  That means that for any computer to find any other computer on the internet, there needs to be **something** that links them together.  That is an IP address. Humans don't do well with IPs, so we give computers names and domains.  So, if you try to reach every PC using the IP address (smb://1.1.1.1) for that machine, does it work?  Chances are that on a home network, your PCs have DHCP to get IPs, so those addresses will change, which is a hassle.  Many home routers will help you manage your PC network ... [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) tries to explain a method to have PCs at home always find each other by having the router set the IP and name for each one.  There are other ways to make this work, but that is usually the easiest.  Plus it doesn't break internet standards, which is always a good thing.

Before that can work, every PC needs to be on the same subnet.  Are they?  I would build a table that contains:
```
hostname - IP - MAC Address
```
Be certain to copy/paste everything - don't type it, or mistakes will be made.  Using the **arp** command by itself should get you started with the table.  Most routers want ":" in the MAC, not "-".  Don't worry if this doesn't make any sense now - it will when you fill out the info in the router (hopefully). Of course, not all routers will do it, but if you've loaded dd-wrt, or Tomato or OpenWRT - that will work.

This will be needed to make the router able to manage your network, so it isn't wasted effort.  Be certain that the IPs are all on the same subnet.

Anyway, hope that isn't too cryptic.

---

