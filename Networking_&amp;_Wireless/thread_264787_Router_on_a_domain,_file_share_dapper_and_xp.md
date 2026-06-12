---
title: "Router on a domain, file share dapper and xp"
date: 2006-09-25
forum: Networking &amp; Wireless
---

### Post by Jon &quot;Yogi&quot; on 2006-09-25
I am on a school network (with a domain controller) that doesn't look favorably on the use of linux. I want to have a router to keep my WinXP laptop and my Dapper desktop running under a spoofed mac address (so the router looks like the laptop).  I also want to easily share files between the laptop and desktop, but not have it open to the WAN (unless with a password, and then preferably not have it seen from the network).

What configurations would you suggest for the software, and are there any routers you would choose over another? Thanks!

---

### Post by Iowan on 2006-09-25
My router is a '486 running [FREESCO]("http://forums.freesco.org/support/"), but there are other router/firewall packages out there.

---

### Post by dannyboy79 on 2006-09-25
I can tell you that my Netgear WGR624 or now it's the WGT624 has the ability to take the computers mac address. I guess I should clarify, I can tell you for sure that the WGR624 has an option under the main settings to take it's owm mac address or take a certain computers mac address or I believe you can enter one. I was just saying that Netgear changed the name, if you went to there website under products you won't find the WGR624, only the WGT624. The wireless runs pretty damn good, it would run best I can tell if you got the matching WG511T pc card because that's waht I have so I can't tell you if other pc cards will pick up the Super G signal since it doesn't comply with 802.1g standards, it's a little different which makes it work so good! Good luck

---

### Post by Jon &quot;Yogi&quot; on 2006-09-25
Just so happens that I got a router from a friend today. Does all the MAC spoofing that I need. 

Now to figure out how to share files from Dapper to windows (and the other way around, if easy) without being seen by the WAN side of the router....:confused:

I played around with Samba, but that  popped up on the list of domain servers, which won't work at all in this situation. I also played with NFS, but couldn't see the dapper box from windows.

Something else I have trouble with is opening windows shares with the dapper box. I get prompted for a username and a password, but the authentication doesn't work. ](*,)

Jon

---

### Post by dannyboy79 on 2006-09-27
have you added the windows username and password username.map file and location into your smb.conf file? also, have you added the windows user to your linux user's? then to the smbusers? You could always use ftp or will the dapper ftp server show up on list of domain servers as well??? what about using ssh to transfer files? will a ssh server show up in the domain server list as well?

---

