---
title: "[SOLVED] VPN Tunneling, does it have to take complete control?"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by phyrewall on 2007-12-12
Ok, I've tried researching this, but I think I can't word the search question correctly to get the answer I need. Hopefully one of you can help me out.

I use Ubuntu 7.10. I use DSL. I use the Cisco VPN client to connect to the Cisco VPN server at work, and then I use TSClient to RDPv5 into my Windows box at the office. All that works dandy. 

My question is: Is there a way to set the VPN connection up so that I can "point" to it with the TSClient instead of whenever the VPN client is connected it takes the whole network connection over? Simply put, my work really doesn't appreciate (or allow) IM programs, torrents, streaming music, and I'd like to be able to continue to use my DSL connection for that stuff LOCALLY while using the RDP  at the same time.  I only want the RDP connection to flow through the VPN.

Is such a thing possible?

Thanks.

---

### Post by jflaker on 2007-12-13
The LAN Security setup on the remote side has policies which are applied to your client based on your user's ID AND/OR group. The policies from the remote side will always supersede your settings regardless of what you do.

You would need to have the settings changed from the remote side. The recommended settings for the remote is to disable LAN access to prevent infection from jumping from another computer on the LAN over into the remote LAN.

I hope this answers the question.

(user of Cisco VPN client)

---

### Post by phyrewall on 2007-12-14
Thanks for the reply, that does answer my question. It makes sense, it's just frustrating.

How likely is running a VPN connection on a VM to keep it seperate to work?

---

### Post by jonallport on 2007-12-14
The answer to your question is YES, VPN wins!

What I think you need to happen is for the firewall admin at you place of work to allow RDP connections in through the firewall.  How he/she/they lock this down is another matter, proably by restricted permitted IP addresses (assuming your DSL line has static IP) and use a non-standard port maybe.

The other way is a branch office VPN.  If your home router is sufficiently smart (or if you have a spare Ubuntu box) you could use setup a BO VPN back to the office and have more extensive routing tables to direct traffic wherever. Depending on the size of your organisation it may mean quite large static routing tables but it's going to get you what you want.

I hope that makes sense!

---

### Post by aranoyas on 2007-12-14
> **phyrewall said:**
> Ok, I've tried researching this, but I think I can't word the search question correctly to get the answer I need. Hopefully one of you can help me out.

I use Ubuntu 7.10. I use DSL. I use the Cisco VPN client to connect to the Cisco VPN server at work, and then I use TSClient to RDPv5 into my Windows box at the office. All that works dandy. 

My question is: Is there a way to set the VPN connection up so that I can "point" to it with the TSClient instead of whenever the VPN client is connected it takes the whole network connection over? Simply put, my work really doesn't appreciate (or allow) IM programs, torrents, streaming music, and I'd like to be able to continue to use my DSL connection for that stuff LOCALLY while using the RDP  at the same time.  I only want the RDP connection to flow through the VPN.

Is such a thing possible?

Thanks.

Look at this thread: [http://ubuntuforums.org/showthread.php?t=430136](http://ubuntuforums.org/showthread.php?t=430136)
I think it can help you to solve the problem

---

### Post by phyrewall on 2007-12-14
VPN works just fine, actually too well is the problem. Thanks for the help.

--EDIT---

I've found that editing the .pcf file and changing:
```
EnableLocalLan=0
```
to
```
EnableLocalLan=1
```
seems to be the trick.

---

