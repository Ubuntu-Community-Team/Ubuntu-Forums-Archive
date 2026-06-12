---
title: "having troubles with wifi install..."
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by Voshra on 2008-10-14
ok so i recently installed the latest hardy heron
and my wireless isnt working. I looked up possible solutions for my problems and i narrowed it down to a package i downloaded and have to install

 "madwifi-0.9.4.tar"

now here is my problem
i've tried to look around for how to install this driver
but i cant seem to find any....can anyone plz help me??

---

### Post by PMahoney on 2008-10-14
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

I'd also recommend you find out what specific card you have and what kind of support there is either here or on madwifi.org.  Some are 'supported' but have specific problems that need to be worked around.

Peter

---

### Post by PMahoney on 2008-10-15
As an additional note, if you are running Ubuntu 64-bit consider using ndiswrapper to bring in Windows XP drivers.  With my Atheros AR5006EG, ndiswrapper worked where as the madwifi didn't in 64-bit.
P

---

