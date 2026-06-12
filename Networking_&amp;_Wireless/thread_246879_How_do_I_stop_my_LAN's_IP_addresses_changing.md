---
title: "How do I stop my LAN's IP addresses changing?"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by handy on 2006-08-29
I recently set up a NFS home LAN.

Having set each machine up as a Server, this allows me to P2P.

Each **/etc/fstab** has a line for each remote directory like so:

**192.168.0.3:/home /media/handy2home nfs	rw,hard,intr	0	0**

My problem is that sometimes a machine will change it's IP address, which stuffs up that machines conection to the LAN?

How do I **fix** each machines IP address?

Any input much appreciated! :)

---

### Post by Jagot on 2006-08-29
There should be an option within your router settings to allocate each machine on the network a specific IP each time.

---

### Post by handy on 2006-08-29
> **Jagot said:**
> There should be an option within your router settings to allocate each machine on the network a specific IP each time.

Thanks for your reply!

I can't see that option in my Netgear DG632 Modem/Router.

Isn't there a way inside of Linux to specify a machines IP address & for the machine to keep it?

---

### Post by Jagot on 2006-08-29
I have a Netgear WGR614 and the option is certainly there for that - 'fraid I'm not at home right now otherwise I'd post a screenshot.  I could be wrong, but I'm pretty sure that your router deals with issuing IP addresses - your computer has no choice in the matter.

I just download the manual for your router and it is mentioned in there so you can certainly do it - it's called address reservation and it is on page 76.

---

### Post by handy on 2006-08-30
OK, I found it, I don't know it that is applicable?  It finds only one address & lists it in the table, & it is not an address of any of my hardware that is on my LAN.  When I try to change the IP it tells me that it is not a valid device!?

Surely there is a way to specify an IP address for a machine, from inside of linux?

---

### Post by handy on 2006-08-30
How do other people who use the NFS to mount remote directories handle this problem?

***When you have specific IP addresses listed in your /etc/exports /etc/hosts.allow etc/hosts.deny ??***

---

### Post by handy on 2006-08-30
Am I the only one who has this problem due the me setting ALL machines as Servers, under NFS?

Apart from this minor problem ;) NFS works great for me in P2P mode, setup like this! :confused:

I do believe there is a solution... :KS

---

### Post by spd106 on 2006-08-30
What's wrong with setting the ip address as static on each machine? 

As long as they are on the same subnet -or you bridge the networks- they should be able to communicate fine. Just be sure to set the default gateway to the routers address. Put the settings in the /etc/network/interfaces file.

eg

router -> 192.168.0.1 

server 1 -> address 192.168.0.2 netmask 255.255.255.0 gateway 192.168.0.1
server 2 -> address 192.168.0.3 netmask 255.255.255.0 gateway 192.168.0.1
.
.
.
Usually turn off dhcp on the router or set it to give higher addresses eg 192.168.0.4 - 192.168.0.11.

---

### Post by handy on 2006-08-30
Thanks so much for your reply.

If I go to static IP, as opposed to DHCP, will that cause me to move more slowly between servers  on the internet?

Or am I making something out of nothing?

I can do that... :rolleyes:

---

### Post by spd106 on 2006-08-30
It shouldn't have any affect on internet access. DHCP is a mechanism for making sure each client on a network has a unique ip address. 

It is just easier to have a server automate the any changes than an admin have to go round each one to make any changes. So in a large network or if you have no idea about networks (like most users), it makes sense to have a DHCP server do the hard work. The trouble is these home routers are less flexible than a proper commercial/dedicated DHCP server.

It sounds like you're worried about DNS, which should not be a problem as this is handled by the default gateway (router). All that is happening is **you** rather than your router is reponsible for making sure that no clients have the same ip address and that they are able to talk to the router (ie ping 192.168.0.1).

---

### Post by spd106 on 2006-08-30
Oh, another idea jumped into my mind as soon as I clicked Submit. On the routers dhcp config you could change the client lease time to **forever**. Then you will only hit problems when the router is reset. eg power failure.

---

### Post by handy on 2006-08-30
> **spd106 said:**
> Oh, another idea jumped into my mind as soon as I clicked Submit. On the routers dhcp config you could change the client lease time to **forever**. Then you will only hit problems when the router is reset. eg power failure.

Thankyou VERY much for your help, & for educating me, I only ever had experience before with small business, & even smaller home LANs, on windoze. 

That experience taught me that one of the many conditions of insanity is a fundamental component of windoze networking:- If at first you don't succeed, undo what you have done, & then repeat ***exactly*** the same steps until you eventually get the desired results ](*,)  :) After which everything usually works quite reliably for a good deal of time... :confused: 

Yes, sorry I was confusing DNS & DHCP. :rolleyes:

At this early stage I like NFS, it was easy to set up, & by making each machine a server, it looks like it will satisfy my home P2P networking needs very well.  There has just been this particular problem, to which thankfuly, you have offered a solution. :cool: 

I do love this community.

I will put some time into this later on today, & let you know how I go.  I'm bound to have a question or two, if you don't mind? :)

**[Edit:]** I'm on the job now.  I just thoroughly checked out the modem via firefox, & there is **NO** ***Client Lease Time*** options?  This could a good thing - if I was absent, my wife wouldn't have to know how to set that parameter after a blackout, or otherwise required reset of the modem/router.

I'm sure she would think it is a good thing!

I'm not sure of the format that I need to use to input the following into the **/etc/network/interfaces** file?

server 1 -> address 192.168.0.2 netmask 255.255.255.0 gateway 192.168.0.1
server 2 -> address 192.168.0.3 netmask 255.255.255.0 gateway 192.168.0.1

I will do the best I can with that info'.

I'll be back...

---

### Post by handy on 2006-08-31
It looks like the Gnome front end for **/etc/network/interfaces** is the ***Menu:* System / Administration / Networking - eth0 - Properties dialogue**

I've played around some, learned some more, & decided that because the 4 machines on my LAN don't have to talk to each other... That 2 servers & 2 clients is the way to go!

All machines share the same cat5 connected printer & adsl, apart from that 2+2=4 with the machines.

So, thanks again **spd106**, for your help, you took me somewhere I wouldn't have got to on my own, thus expanding my knowledge & experience somewhat...

That's not allways a good thing, but it certainly was this time! :KS

---

