---
title: "Can XP See Ubuntu Mounted Network HDD"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by teotwawki on 2007-07-20
I've not been able to get past the login screen (rlogin?) that appears on my XP box when I try to access the external HDD connected to my Feisty hosted Dell E521. The HDD is properly Shared, the Dell sees all the other Shared folders on the network (multiple XP boxes). The loginID I try is the Feisty defined ID and the appropriate passwd. Is this an XP Remote Login problem?

---

### Post by reckless2k2 on 2007-07-20
samba....and smbpasswd

[http://easylinux.info/wiki/Ubuntu:Feisty#Samba_Server](http://easylinux.info/wiki/Ubuntu:Feisty#Samba_Server)

---

### Post by djchandler on 2007-07-20
> **teotwawki said:**
> I've not been able to get past the login screen (rlogin?) that appears on my XP box when I try to access the external HDD connected to my Feisty hosted Dell E521. The HDD is properly Shared, the Dell sees all the other Shared folders on the network (multiple XP boxes). The loginID I try is the Feisty defined ID and the appropriate passwd. Is this an XP Remote Login problem?

Is the external drive usb connected?

A couple of weeks ago, somebody else had a similar problem, and I duplicated it on my network with a similar result. But ours was reversed with the shared external drive connected to the XP box. The share on the external USB drive even blocked access to shares on our internal XP drives. We never did get it to work, even with wide open shares on all the XP folders, no password or user name necessary. We both gave up, assuming a bug in MS networking software, not samba. Maybe we were wrong. It could be that shared removable media is the key to this from both ends. I'll try to remember. I guess this is why you should archive the threads you have been involved with in your CP folder. :confused:

I'll be lurking with great interest in your outcome, while I try to see if I archived something here locally.

DJ

---

### Post by teotwawki on 2007-07-21
samba server solved my problem. Once I had it configured as per the guidance received here, all was aces...

---

