---
title: "Samba performance issues with &quot;security = user&quot;"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by Croccydile on 2008-10-19
Ok this is going to be a *really* weird one for most people, so I don't expect magic to happen here.

Related to the recent problems with the r8169 driver problems and network performance, I was noticing that when I was testing Intrepid Ibex by using a simplified smb.conf file I was also experiencing another layer of problems on top of r8169 driver issues related to samba.

My plague has been trying to read/write lots of smaller files within folders, and the performance has been nightmarish.

The bottom line I'd like to ask if anyone has come across this issue, where having security = user drastically reduces performance of processing many files together?

While security = share is a bad idea, it is currently my only option to get the real performance out of my server... I can only imagine there is something hanging up authentication/acks somewhere.  I've searched endlessly around the internet trying to find solutions to this.

Example: Windows XP is a client reading from Ubuntu running samba, a program attempts to access 1000 files within a folder sequentially and bogs down terribly.  The program will read one file per second (!) and then burst for about 25 files, and then repeat this process.  This could take several minutes, where with security = share this would be seconds, if maybe that.

Any ideas?

---

