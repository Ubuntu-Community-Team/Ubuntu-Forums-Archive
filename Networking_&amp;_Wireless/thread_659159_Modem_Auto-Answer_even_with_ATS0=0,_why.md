---
title: "Modem Auto-Answer even with ATS0=0, why?"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by SiO-Buntu on 2008-01-05
Hi All,

I have recently installed a modem on my Ubuntu box (see below for details).
For some reason, the modem always Auto-Answer to phone rings.

When I use a terminal (eg: Putty) and set the "S" register to zero doing: ATS0=0 it seems to do the job.  As long as the terminal is connected and the ATS0=0 command has been set, the modem does not answer.  

But once putty is closed, then the modem will start to answer on is own again.
I tried to set register and profiles on modem  (AT&W0) without success.

I suspect maybe a background service is running that somehow answers the ring...
Or some default config is pushed back in modem...  dunno. 

Does anyone have an idea what could be the problem?
I simply don't want this modem to answer.  Never.

Thx alot for your help.



-=Additionnal Info=-

Ubuntu Distro: 7.10
Modem used: Rockwell - HSF 56k Data/Fax/Voice/Spkp (w/Handset) Modem
Location: North America

---

### Post by HermanAB on 2008-01-05
I think auto-answer is controlled by the modem S registers.  It's been a while since I have used a modem though!

Cheers,

Herman

---

