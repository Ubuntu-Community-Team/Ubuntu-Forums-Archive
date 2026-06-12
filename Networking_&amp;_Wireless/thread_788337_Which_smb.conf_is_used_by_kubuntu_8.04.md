---
title: "Which smb.conf is used by kubuntu 8.04?"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by venik212 on 2008-05-09
I upgraded Kubuntu from 7.10 to 8.04, and started having a lot of problem with Samba.  I finally discovered that it has TWO smb.conf files: one in /etc/samba/ and one in /usr/share/samba/
Which one is being used by default?  Which one should I be editing?

In addition, the system seems to forget SHARE information.  When I right click on a folder on the desktop, select SHARE, and make changes, I expected those changes to remain in place.  But KDE must be reading some smb.conf file that had not been updated by my changes.  Is this a bug or a feature too subtle for me to appreciate?

Thanks,

---

### Post by superprash2003 on 2008-05-10
its normally the /etc/samba which is used.. once you make changes to samba shares.. its always better to restart samba by typing
 sudo /etc/init.d/samba restart

---

### Post by venik212 on 2008-05-12
That is just what I have been doing, but for some reason (8.04?  Another Samba GUI program?) there was another smb.conf file in the /usr/share/samba/ folder.  This is an EXCELLENT way to confuse the peasants...

---

