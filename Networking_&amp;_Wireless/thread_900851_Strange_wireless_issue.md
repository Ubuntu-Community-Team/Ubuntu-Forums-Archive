---
title: "Strange wireless issue"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by D6c3X2 on 2008-08-25
Since some days now I'm puzzled with an issue on Ubuntu 8.04.

Some days ago I did an update and ever since then I can't get connected to the internet. My setup:

Ubuntu -> Linksys WAP -> Smoothwall3.0 -> ADSL modem -> internet

When booted up I have no internet connectivity although I am connected wireless. I am at that time able to reach the Wireless AP, but I can't reach the Smoothwall. A TCPDUMP om the smoothwall shown no traffic whatsoever coming in from the client.
 
Only when I "force a doorway" by launching a traceroute to a fake internet IP (e.g. traceroute 82.188.22.22) after some seconds the connection seems to be made and I'm able to get onto the internet. I though it might be the smoothwall setup but I have reinstalled it (with no updates and again with updates): still no luck. I have checked if I have the same issue when connected via cable. To my surprise there was no issue at all.

And then even stranger: when using Micro$oft XP (=laptop from work) I have no issue at all.  
When I boot up that same machine from Ubuntu CD the problem returns. So it's not client-hardware related neither.

I can only conclude for now that it seems to be directly linked to Ubuntu.
I have spent hours on finding any clue and had some sleepless night, but I have no ideas anymore.

Can anyone please tell what I can try now? I'm pretty desperate already.

thanks beforehand!

---

### Post by D6c3X2 on 2008-08-25
By the way: the ADSL link is a persistent one. The time-out during the "force a doorway" cannot be explained as the time needed to get connected through the modem. When using a Wired link no such forcing is needed. TCPDUMP shows immediate traffic when wired. only with wireless there is no activity whatsoever until I launch the traceroute...

Another by the way: the setup has worked for months without any issue. Only after an update done some days ago the problems started. No hardware changes were done, no changes on any link in the chain.

please help... I hate having to use Micro$oft again simply because I cannot get this resolved.

---

### Post by AlexenderReez on 2008-08-25
hrm,this might related latest version of linux-ubuntu-modules...to solve it,downgrade version to 2.6.24.21...

---

### Post by D6c3X2 on 2008-08-27
I've tried that. I did a go with 2.6.24.20 , 2.6.24.19, even 2.6.24.18 no luck.

I have replaced the Wireless AP with a test WAP since I though it could be the reason as well -> still the same issue.

The stragest thing is that I have no issue if using any Window$ version...

---

### Post by D6c3X2 on 2008-08-27
I believe more and more that this might be linked to another issue reported by many people:

[http://ubuntuforums.org/showthread.php?t=765647](http://ubuntuforums.org/showthread.php?t=765647)

---

