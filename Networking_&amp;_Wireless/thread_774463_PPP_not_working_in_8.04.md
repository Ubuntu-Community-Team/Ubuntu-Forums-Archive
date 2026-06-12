---
title: "PPP not working in 8.04"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by bcardarella on 2008-04-29
I have a Franklin Wireless CDU-680. I have the modem properly setup:
[http://ubuntuforums.org/showthread.php?t=691687&highlight=cdu680](http://ubuntuforums.org/showthread.php?t=691687&highlight=cdu680)

But these instructions are for 7.10. There seems to be an issue in 8.04 where PPP is either being filtered or is blocked somehow. I saw another post with a similar issue:
[http://ubuntuforums.org/showthread.php?t=772248&highlight=ppp0](http://ubuntuforums.org/showthread.php?t=772248&highlight=ppp0)

But that didn't resolve my issue.

So I have the modem setup, and can see with ifconfig that it is obtaining an IP address and being assigned two DNS servers. The only thing that looks odd is that it has a subset mask of 255.255.255.255

Anyway, is there something else I should be checking to make sure that PPP traffic isn't being filtered? Did 8.04 install some new firewall settings?

Any help is greatly appreciated.

---

### Post by bcardarella on 2008-04-30
Just a follow-up. I was able to get the card working. I decided to try on a Window machine to test if the hardware was faulty. I suppose for Quest (the provider... not certain if this is the case with other providers) the card needs to be activated. So I ran the Windows installation software, plugged in the activation code and activated the card. Once this was done and I confirmed that the card was working in Windows I tried again in Ubuntu. The card works perfectly now, no issues at all. Hopefully this helps somebody.

BTW, not the first time I've run into hardware that needs to be activated in Windows first... kind of annoying.

---

### Post by xe1ufo on 2008-07-18
I also have the Franklin Wireless CDU-680. Please tell me how you made it function in Ubuntu. Thanks in advance!

---

