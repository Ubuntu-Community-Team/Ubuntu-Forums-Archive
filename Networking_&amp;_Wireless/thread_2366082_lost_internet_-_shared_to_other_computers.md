---
title: "lost internet - shared to other computers"
date: 2017-07-13
forum: Networking &amp; Wireless
---

### Post by jgw on 2017-07-13
I am running with a wired connection.  I was trying to figure out how to setup a local computer network and came across something that told me that I wanted to change ipv4 part of the connection to "shared to another computer".  I did that and continued to futz around and finally just shut everything down and stopped for the day.  Today I turned my computers on and I had no internet, on two machines.  I checked the computers in the house and they had the internet just fine (I am connected to the same router).  I then checked all my wires to make sure they were right.  Then I tried another hub to see if that was the problem.  After swapping out a bunch of wires, etc. I tried again and still absolutely no connection.  The strange thing is that I could see the net when I would first start but it very quickly shut down the connection.  Then I remembered what I had done with the ipv4 connection and changed it back to automatic and re-booted.  Suddenly I had an internet connection!  I found this a bit strange so I thought I would post this adventure and see if anybody could tell me what the heck happened.

Thank you.................

---

### Post by TheFu on 2017-07-14
Screwing around with routing tables without a good understanding leads to the results you have seen.  Them there check boxes DO MATTER.

---

### Post by jgw on 2017-07-14
Yep - thanks for the reply.  Just thought I would put this out in case anybody gets tempted.   I am just trying to setup a little network and have failed splendidly.  If anybody can point me to someplace with good directions to do this, that won't get me into trouble, I would appreciate it.

---

### Post by BenginM on 2017-07-14
Salutations!

are you lookin' for this:

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by TheFu on 2017-07-14
Understanding IPv4 networking is a start.  grc.com/sn - beginning with episode 25 - "how the internet works". Think is is 3-4 episodes.  Audio and transcripts available.

If you list the equipment you have (general is fine to start) and what you want/intend, perhaps we can help?  I run multiple small networks for the office and can talk larger networking, but I'm not BGP conversant, if that is the level you need.

Oh ... and generally, if you aren't doing something "normal", avoid the GUI.

---

### Post by jgw on 2017-07-14
sary.sa:
thank you for the reply.  The problem with your link is that it tells me "then on tab IPv4 Settings select Method Shared to other computers".  When I did that both the computers suddenly no longer had access to the internet.  After swapping and testing every line I changed that setting back to automatic and that got my internet back.  I would not recommend that particular link as it will, based on my current exerience, shut down your access to the net.

---

### Post by jgw on 2017-07-14
My equipment is pretty straight forward.  I have one ms windows machine (my wife's), 3 ubuntu pc's and 2 ubuntu laptops (all 16.04)  I would like to get them all talking to one another and have failed.

---

### Post by BenginM on 2017-07-14
Excuse me, i actually want to share this link:

[https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing](https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing)

what you asking for is fairly simple you can even do that from network manager , and there is an example:

[https://askubuntu.com/questions/169473/sharing-connection-to-other-pcs-via-wired-ethernet](https://askubuntu.com/questions/169473/sharing-connection-to-other-pcs-via-wired-ethernet)

---

### Post by TheFu on 2017-07-14
> **jgw said:**
> My equipment is pretty straight forward.  I have one ms windows machine (my wife's), 3 ubuntu pc's and 2 ubuntu laptops (all 16.04)  I would like to get them all talking to one another and have failed.

Uh ... router?  dumb switches?  ethernet cables? wifi?  

Setting up a home network is trivial with a minimal effort if you don't care too much about security.  The issue is with almost all home-routers sold, the vendor doesn't provide patches often or long enough to keep them secure.

An old, dedicated, x86 machine can easily be a router if it has 2 network cards.  Mixing routing with any server or desktop is a poor decision, IMHO.  However, lots of people do it.  Ars technica has a few articles on setting up your own router using Ubuntu Server as the base.

The only way to have any security for a home network is to have a router OS that is constantly being patched and maintained for the hardware it runs on.  That basically limits people like you and I to some sort of x86 machine with a linux server or BSD OS that is constantly patched.  If the OS you look at doesn't have multiple patches available every month, it probably isn't maintained enough.  IMHO.

---

### Post by jgw on 2017-07-15
Sorry.....

I have a single router (acronis c1000a) and all computers, wireless and wired, are connected to that router (century link internet and router)  Wired computers are are connected w/rj45 cables.  Some computers will show the windows network and others will show that plus all connected machines (even though the one that does this will not connect with any of them).  My suspicion is that each computer is probably setup differently.  What I need is a single plan, step by step, for each computer.  I have no idea what I am doing wrong.  I used to have this all setup and then it all went way (have no idea what happened or what I screwed up).

---

### Post by TheFu on 2017-07-15
What are the network settings for each system?  Are they all DHCP or static?  Any "server" should be static and the IP needs to be outside the DHCP range.

* IP
* Netmask
* Default gateway 
For each.  The default GW should be the router. The netmask should be the same for all of them and the IPs must be different, but inside the subnet.  If the IPs change all the time, I would fix that so they don't. Only guest devices should bounce around, IMHO. That is NOT a requirement, but really does make managing a network easier.  Use "DHCP reservations" for any portable devices - this is normally something the router controls.  For desktops, setup static IPs.  There are thousands of how-tos for all this stuff for each OS and router. A good web search will find them.

---

