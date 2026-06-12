---
title: "Quick Shorewall policy question"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by Alamar on 2007-06-30
I've had Shorewall set up for a few weeks now - or so I thought.  Just today I setup a VNC server (which looks for connections on port 5901) which I intended to connect to through an SSH tunnel.  To my horror, I discovered that I could connect directly to port 5901 from within my local network - something Shorewall should have been preventing!

I eventually tracked down the problem to a missing line in my /etc/shorewall/policy file - the lines now in my policy file are:```
#SOURCE         DEST            POLICY          LOG             LIMIT:BURST
#                                               LEVEL
fw              net             ACCEPT
net             fw              DROP            info
net             all             DROP            info
all             all             REJECT          info
#LAST LINE -- DO NOT REMOVE
```

The line I hadn't previously included was the second one (net fw DROP info), although it was present in the one-interface example, because I thought it was covered by the next line (net all DROP info).  Since port 5901 is now correctly blocked on my LAN, I was evidently wrong before - but my question is... why?

---

### Post by Alamar on 2007-07-06
*bump* Anyone?

---

