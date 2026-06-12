---
title: "UPnP"
date: 2016-04-12
forum: Networking &amp; Wireless
---

### Post by Akarsh_Kharidehal on 2016-04-12
Hi,
 I have been playing with UPnP since a few days and I got to know its purpose and usage.But I want to know how UPnP can be made working in real time and how people can use it in everyday life.
I have come across few small scenarios where we use UPnP but while digging in a bit deeper I am unable to confirm and judge is UPnP is working or not on my client side.
I have enabled UPnP on my router and in the console I have found its working and I have used the UPnP Inspector tool and over there my device is being discovered.
I also checked in Wireshark, I am able to see packets related to SSDP and HTTPU but I am unable to confirm if UPnP feature is working on my client.I need your help in respect to it.
Thanks in advance.

---

### Post by TheFu on 2016-04-12
Welcome to the forums.

Security professionals consider UPnP to be a huge security hole and always, always, always disable it.

Allowing a client-side tool to manage router firewall and port forwarding is asking for trouble.  What is to prevent some website from crafting javascript that scans the LAN from inside, locates the router and opens all ports?  Nothing.

Disable UPnP if you care about security at all.  WPS is bad too.

I'm not the only person with this feeling.
[http://www.howtogeek.com/122487/htg-explains-is-upnp-a-security-risk/?PageSpeed=noscript](http://www.howtogeek.com/122487/htg-explains-is-upnp-a-security-risk/?PageSpeed=noscript)
[http://www.zdnet.com/article/how-to-fix-the-upnp-security-holes/](http://www.zdnet.com/article/how-to-fix-the-upnp-security-holes/) - DHS and CERT both say to turn it off.
[https://nakedsecurity.sophos.com/2013/02/05/upnp-flaws-turn-millions-of-firewalls-into-doorstops/](https://nakedsecurity.sophos.com/2013/02/05/upnp-flaws-turn-millions-of-firewalls-into-doorstops/)
[http://www.ciscopress.com/articles/article.asp?p=461084](http://www.ciscopress.com/articles/article.asp?p=461084) - Cisco says to turn it off!
[http://kb.netgear.com/app/answers/detail/a_id/22686/~/how-to-disable-the-upnp-feature-on-your-netgear-router](http://kb.netgear.com/app/answers/detail/a_id/22686/~/how-to-disable-the-upnp-feature-on-your-netgear-router) - netgear says to turn it off too!

If that isn't enough - visit any DefCon group world wide and as this same question. [https://www.defcon.org/html/defcon-groups/dc-groups-index.html](https://www.defcon.org/html/defcon-groups/dc-groups-index.html)  When they are on penetration testing jobs, they love, love, love UPnP.

Is UPnP bad?  Not in a perfect, safe, world. As with most security choices, there are trade-offs.  Sadly, most people follow instructions written by people who don't care about their security on the internet. The greatest use of UPnP that I know is gaming consoles.  They like it because it reduces end-user complaints that games don't work ... er ... at the cost of poor network security.  





IMHO.

---

