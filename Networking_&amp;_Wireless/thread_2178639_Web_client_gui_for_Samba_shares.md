---
title: "Web client gui for Samba shares"
date: 2013-10-04
forum: Networking &amp; Wireless
---

### Post by futureslay on 2013-10-04
Hi, hopefully I put this in the right place, if it's not, then please by all means, move it.

Am after a solution to get around my college's blocks on ports. Initially, I was under the impression that it was the main ports that were blocked, but I've not been able to connect to my VPN or anything, either.
I'm after something that will allow me to have a service very similar to Novell's NetStorage program, in as much that I am able to upload, download and use my files through port 80 in a web browser. 
After a bit of googling, I have come across [SMB2WWW]("http://www.scintilla.utwente.nl/users/frank/smb2www/") and [this]("http://www.debianhelp.co.uk/smbclientweb.htm"), but I'm not too sure what I'm looking for specifically. Hopefully somebody has either had some experience with something like this or can point me in the right direction.

Regards,
Dom

---

### Post by TheFu on 2013-10-04
Is your IP public or private? [Check the RFC]("https://tools.ietf.org/html/rfc1918") if you don&#8217;t know what that means.  10.x.x.x, 172.x.x.x and 192.168.x.x are private (with exceptions in the 172 range).

If it is private, then only the edge router admin can setup port forwarding and nothing you do will work unless there is an external 3rd party involved to keep the connections open and be proxied through the ports the school actually allows out.

If the college is smart, they've locked down all internal traffic on private IPs and use a transparent proxy for external access allowing only well-known ports like 80, 443, 465, 993 out. They should also cut off external DNS completely to internal non-proxy IPs. In this way, only the proxies **can** be used to get names resolved on the internet.

Colleges have a tough time.  They are responsible for all traffic on their networks and usually the MPAA and RIAA have met with them, threatened to sue if they don't take effective measures to end copyright infringing activities, not that you or I would ever do anything like that.

So, if you are lost, post the output of 
* ifconfig
* route
here.

---

