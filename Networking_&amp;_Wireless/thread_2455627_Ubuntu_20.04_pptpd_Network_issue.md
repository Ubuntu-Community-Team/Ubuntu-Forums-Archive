---
title: "Ubuntu 20.04 pptpd Network issue"
date: 2020-12-24
forum: Networking &amp; Wireless
---

### Post by anthonya55 on 2020-12-24
I am currently using Ubuntu 20.04 for a pptpd VPN solution. It was working great for a while. As of lately I'm having the issue ERR_NAME_NOT_RESOLVED which I believe is a dns issue with the Ubuntu server. Any information will be awesome. Thanks.

---

### Post by TheFu on 2020-12-24
Calling pptp a VPN is being overly nice.
[https://www.schneier.com/academic/pptp/faq/](https://www.schneier.com/academic/pptp/faq/)
[https://samsclass.info/124/proj14/p10-pptp.htm](https://samsclass.info/124/proj14/p10-pptp.htm) Hacking PPTP is widely taught in security engineering classes - both the CHAP and LEAP variants.

At this point, PPTP is used when you desire to leak information, but not appear to leak information.  If you want an unencrypted tunnel between 2 locations, there are other protocols for that which don't provide a fake sense of any security.

---

### Post by anthonya55 on 2020-12-24
i am not using it for anything important really. I am running a game server from home. I have the pptp server running on the ubuntu vps just to mask my home ip with the ddos protection that comes with the vps. I used this guide : [https://help.ubuntu.com/community/PPTPServer](https://help.ubuntu.com/community/PPTPServer) I think the issues is a dns failure but i really am not sure. Any help would be amazing.

---

### Post by TheFu on 2020-12-24
DNS, NAT and routing are the most common problems for any VPN.  Perhaps you can post those settings with and without the cough, VPN, cough, active?

I haven't used pptp since around 1999, so I doubt I'll be much help if the issue is part of that.  

That guide has a fundamental flaw.  It assumes that 192.168.0.0/24 isn't already being used.  Guides should never use 192.168.0.0/24 or 192.168.1.0/24 or 10.0.0.0/24 subnets for examples.  Due to the way that routing works, any client of your VPN that has a 192.168.0.0/24 subnet will fail to work. It is pretty important to use seldom used, private subnets, for all VPNs.  Instead of 192.168.0.0/24, consider using 10.7.7.0/24 just to be random and unlikely to be seen by you or any client location.

**route -n** will show a routing table. If you don't have that command, the inferior command:
**ip route |column -t** can be used so the output isn't too ugly.

As for DNS, since 10.04 DNS has been a problem for every Ubuntu Release I've had.  About a year ago, I finally decided to fix it forever, but most people new to Linux wouldn't do what I've done. I prevent all the extra DNS stuff that Canonical decided was a good idea from being used. IME, it just breaks things whether it is systemd-resolved or resolvconf screwing up the works.  They aren't necessary and can be disabled so we can use the manual DNS controls that worked the last 30 yrs.

But posting an error without saying where it is coming from makes us guess.  Please don't make us guess.  
Which machine is showing that error? 
What command is causing it?  
Have you tried using other commands like dig, nslookup, host?  
Did those work or not?

And please post the exact command with output. Use 'code tags' so a copy/paste keeps the exact formatting. 
[https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) explains.

---

### Post by anthonya55 on 2020-12-24
My apologies.
Windows Server 16 - Main OS im using to host game servers (ARK/Rust/Minecraft etc). This machine is located in my house and I dont want my main IP being leaked. Thus why im using the pptp just to prevent that from happening.

Ubuntu 20.04 - Terminal only. I am using this for the pptp server (obviously) to give my Windows Server a different IP so players can connect with that IP instead of my main network IP.

Issue occurs on the Windows Server 16. I try to load a webpage, ERR_NAME_NOT_RESOLVED pops up. Any connections attempted gets rejected. Once I disconnect from the "VPN" and reconnect it works as normal. I think its a issue with the DNS but I really am not sure.
No real command im using. (Also not very experienced with ubuntu)


-No desire to use OpenVPN/WireGuard/IPSec as its a game server use, those encrypt packets and cause a latency issues while gaming-

---

