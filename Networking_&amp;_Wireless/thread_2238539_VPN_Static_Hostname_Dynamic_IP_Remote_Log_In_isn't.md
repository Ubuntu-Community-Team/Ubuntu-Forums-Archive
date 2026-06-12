---
title: "VPN Static Hostname Dynamic IP Remote Log In isn't working from WAN"
date: 2014-08-08
forum: Networking &amp; Wireless
---

### Post by groovey58 on 2014-08-08
Hello

I have a recent upgrade from 12.10 to 14.04 Desktop. I have been using x2go and xfce to enable remote access from outside my LAN. I have been using no-ip to direct me to my dynamic ip. I have recently installed PPTP HMA VPN access for improved security. I am using an ASUS RT-N66U Router. I have enabled it to contact No-Ip and update the dynamic IP on a frequent basis. I have port forwarding enabled to direct my unique ports request to the proper ports inside my LAN. Everything is working when I access my machine (which is headless) from inside my LAN. 

My issue is that I can no longer access my machine from outside of my LAN. Which I could do prior to putting the PPTP VPN into service.

Before I added the PPTP piece I would open the x2go program on my Laptop, start the session, enter my password and I would be sharing the xfce desktop. It worked.

With the VPN in the picture I time out, I cannot connect via ssh, or winscp either.

Would the issue be that my router is sending No-Ip my ISP assigned IP? Do I need to have the computer update No-Ip over the newly established VPN?

Any help would be appreciated.

Thank you

Groovey58

---

### Post by TheFu on 2014-08-08
The PPTP protocol is broken and doesn't really provide much security. It has been hacked a few time over the last 15 yrs. NOBODY looking for a secure VPN uses it.  IPSec is the answer.

It is unclear to me why you'd use a VPN for inbound traffic at all?  I suspect the VPN connection is allowing only traffic from the external VPN provider into your PPTP endpoint, so no other traffic, like ssh, can get there. I beleive that is part of the design for every VPN.  Disable the VPN. I bet it works.

It is unclear to me if you are running the PPTP server or paying someone else. If you run it, there should be more options, but then look at ipsec.

x2go uses ssh, so it is as secure as any ssh session - hopefully you are using key-based authentication, NOT passwords.  Also running fail2ban.

---

