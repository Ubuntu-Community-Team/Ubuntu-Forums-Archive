---
title: "[SOLVED] Domains vs. Workgroups"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by bilijoe on 2008-03-24
Just what, exactly, is a "domain"?  And how is it different from/similar to a [Windows] "workgroup?  I think much of my confusion with trying to get my network working [correctly] is rooted in a thorough misunderstanding of this issue.  I would just scrap Windows all together, except for this elegant old UMAX Astra 1200s that I can't seem to get to run under anything except WFWG 3.11 (at one time, in the distant past, my favorite operating system).  I need to network the antique computer that is dedicated to running the scanner, so I can access the scans on machines new enough to manipulate the massive files the Astra produces, in its highest resolution mode (I use it for copying and archiving original artwork that is delightfully laden with elegant, subtle detail, hence I need all the resolution I can get--and I can't afford new equipment, at this time).  Anyway, I diverge--if anyone can straighten me out on thedetails of and differences between domains and workgroups, I'd really appreciate it.

---

### Post by seeker1458 on 2008-03-24
A workgroup is just what it sounds like.  A group of computers just working together, mainly just for file/printer sharing.  

A domain is MUCH more complex.  First off you need a machine running some NOS(network operating system) such as windows 2000 server, windows server 2003, any flavor of *nix/*buntu server edition to act as a domain controller.  This is to apply policies on a domain, group, user, etc...level.

first hit on google: [http://www.thatdamnpc.com/57/](http://www.thatdamnpc.com/57/)

just read about the differences from different google searches.  There is no way anyone on here is going to go though ALL the differences.

---

### Post by HermanAB on 2008-03-25
MS Windows 3.1 networking uses Workgroups.  This baggage is still part of modern Windows networking and is the default for a Windows network.

MS Windows NT networking uses Domains.  They took the BSD BIND8 and incorporated it into their servers, then they added some auto-update security holes to BIND8, stirred LDAP and a broken Kerberos5 into the mix and called it Active Directory.

If you have to make Linux work with Active Directory, see this guide: [http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

Cheers,

Herman

---

