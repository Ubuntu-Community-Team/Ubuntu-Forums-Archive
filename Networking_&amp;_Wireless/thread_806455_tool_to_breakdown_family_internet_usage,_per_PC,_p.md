---
title: "tool to breakdown family internet usage, per PC, per Day???"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by callagga on 2008-05-25
Hi,

I really need a tool to understand my home's (i.e. various PCs/Xbox etc) usage of my internet allocation.  I run a linux based firewall.  Are there any good linux based software packages you could recommend for this?  (i.e. all my traffic goes through my [www.clarkconnect.com](www.clarkconnect.com) box at the moment).  What I'm after is:  

[1] Tool that summarizes my family's internet bandwidth usage (on ppp0) per internal IP address/PC, per day, per upload/download?   

[2] As a bonus it would be great if the report [1] above could also be configured to break down the traffic based on hours of the day, i.e. to compare against the ISP Peak & OffPeak bandwidth limits.  

Regards

---

### Post by SpaceTeddy on 2008-05-25
i think the bandwidth monitoring tool of webmin can do what you want. It is very simple, but should do the work. I've gotten it to work once, but that was a long time ago, and i remember correctly, it does not work properly with syslog anymore, but needs a reconfiguration of syslog-ng instead...

i am all but sure about this :(

hope it (somewhat) helps :)

---

### Post by Patb on 2008-05-25
Callagga, you might also have a glance at vnstat.  It is in the repositories.  I do not know about the "breakdown" or how it might be applied to a home network; I've only ever used it on a stand alone pc.  It does hourly, daily or monthly traffic summaries.  And I've never used webmin so I can't give any comparison.  Good luck.  

Cheers, Pat.

---

### Post by telecomando on 2008-06-26
nTop, the clark connect box might already have this or something built on this in it.  You can check the forums and see if anyone has built a package for it.
Or switch to a firewall that does.
Endian Community has it built in.
Ipcop + smoothwall have packages for it.

But nTop will do everything your asking and more.  Breakdown of traffic, bandwidth, ports, downloads etc.  Add that with a good proxy server and you can watch anything that goes on.  Drop a packet sniffer like ethereal on that and you can even read people's IM's, emails, gather passwords anything sent in clear text.

---

### Post by dayvy on 2008-06-26
You might also want to look at squid. It's in the repositories.

d.

---

