---
title: "LAN Problem: Google works, links don't until I click 20x refresh"
date: 2014-12-06
forum: Networking &amp; Wireless
---

### Post by refle on 2014-12-06
Hi guys,
My system: UBUNTU 12.04

I have a strange problem. My wifi always works perfectly. My Lan together with google, too. But sometimes (not always, but most of the time), when I click on links from the google search, immediately I get en error "This webpage is not available with the error codes:
"DNS_PROBE_FINISHED_NXDOMAIN"
or
"ERR_NAME_NOT_RESOLVED"
If I click for about 20x refresh, the page will load. 
Sometimes, some of my bookmarks bring the same error. But google-search always(!) works. 
This happens for firefox as well as for chrome. Thunderbird also can't always connect. 

On my windows (double-boot), my lan works like a charm.

Can you help me?

---

### Post by refle on 2014-12-06
Ich hab das Problem (scheinbar) gelöst, indem ich meinen DNS Server manuell auf den von OpenDNS umgestellt habe

---

### Post by ajgreeny on 2014-12-06
Well done!
Please mark as **Solved** from Thread Tools menu at the top of the thread.

---

### Post by refle on 2014-12-06
Ok, i was mistaken. The problem occured again >.<

---

### Post by refle on 2014-12-06
can anyone help please - this is so anoying. And I don't even know what I changed, this problem just ocurred

---

### Post by refle on 2014-12-07
nobody an idea??

---

### Post by pfeiffep on 2014-12-07
Perhaps manually adjusting the dns server that Linux uses to match that of Windows. 
Step one will be to discover the DNS address used by Windows, then follw instruction found [here.]("http://www.416studios.co.uk/journal/2012/how-to-change-your-dns-on-ubuntu-12-04precise-pangolin")
***Ich wünsche Ihnen viel Glück und viel Spass***

---

### Post by refle on 2014-12-13
I finally made it with OpenDNS. The problem was that I was connected at the same time with lan and wifi -> although I had changed the DNS of my Lan, no my wifi made problems. Turned off it works now!
thanks!

---

