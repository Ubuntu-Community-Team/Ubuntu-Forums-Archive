---
title: "College Network Security Pain In Butt!"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by BT1 on 2009-11-23
Well, about a year (or so) ago I could not log into the college's wireless network because they required the WPA protocol which wasn't default with most linux distros at the time. Eventually Linux came out with WPA default support and I reported to the network administrator (with glee and joy) that his system was now supporting Linux users.

Well, this new semester is here and they still use WPA encryption, but they threw in a wildcard and I think they're just being a bunch of stinkers. They now require that you download a file (a .sh file) that normally runs in windows after you register. This file (I think) runs a scan on your system to see if your system supports their security protocols. Problem is, Linux doesn't run this file right. It keeps saying it fails when I run it as a script, and nothing seems to work.

Normally the file checks the system, sends an "all clear" signal back and self deletes (as they lead us to believe). This one little file is keeping me out of the school's wireless system I pay tuition for BECAUSE I run linux.

Please help me correct this tradgedy!

(P.S. Who else thinks this is an underhanded attempt at locking out linux users? Lol)

---

### Post by undecim on 2009-11-23
You cloud take a look at the script, determine what it does, and send your own "all clear" back.

Or I could take a look at it... There may be legal issues with posting it though. (or also with circumventing the script.)

---

### Post by marshmallow1304 on 2009-11-23
My college has a similar system that they cleverly named the Network Access Client (NAC).  In this case, it's a Windows program that scans for security vulnerabilities and makes sure there is an active anti-virus and firewall.  

To get around this, I had to contact IT and give them the MAC addresses of my network interfaces, which I assume they added to a whitelist.

---

### Post by matthewbpt on 2009-11-23
Maybe you could try running in on wine... might be a complete fail but it's worth a shot

---

### Post by BT1 on 2009-11-23
> **marshmallow1304 said:**
> My college has a similar system that they cleverly named the Network Access Client (NAC).  In this case, it's a Windows program that scans for security vulnerabilities and makes sure there is an active anti-virus and firewall.  

To get around this, I had to contact IT and give them the MAC addresses of my network interfaces, which I assume they added to a whitelist.

Good idea, I'll swing by there and give him a talking to. 

> Maybe you could try running in on wine... might be a complete fail but it's worth a shot

Yeah, it seems to look for stuff through windows eyes, and not through linux eyes if you get my drift.

> You cloud take a look at the script, determine what it does, and send your own "all clear" back.

Or I could take a look at it... There may be legal issues with posting it though. (or also with circumventing the script.)

If all else fails, I'll ask em before I post it. I've been there before so they know I'm not just trying to bypass their security, I'm trying to utilize what I am paying for.

---

### Post by BT1 on 2009-11-23
Alright good. I spoke with them and asked them about the MAC address issue and they just had me write down my MACs and they would put me on the list. It should be fixed by tomorrow night. Woot!

Thanks for the ideas.

---

