---
title: "Ubuntu samba share no longer accessible - The group name could not be found"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by ssjwolf on 2008-07-15
Hi,

I set up some samba shares on my Ubuntu box using this great guide [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605), and they were working superbly until recently. I can no longer access my shares on my Ubuntu box from my Windows boxes and this error pops up "The group name could not be found". I haven't made any changes to the samba shares or network setup since I set it up. Accessing shares on my Windows boxes from the Ubuntu box still works fine. Any ideas?

Thanks for the assistance, much appreciated!

---

### Post by Jay_R on 2008-07-15
I have the same problem, and it started just now too. Samba is a timebomb? :|

Syslog says

> create_builtin_users: Failed to create Users

EDIT -- commenting out force user and force group in smb.conf worked like a charm. I'm stumped.

Example: > [Music]
    path = /media/misc/Music
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0755
    directory mask = 0755
#    force user = <snipped>
#    force group = <snipped>

---

### Post by paulsdavies on 2008-07-30
I also had samba shares working for ages, and then they stopped working a little while ago. Like the post above, commenting out the force user and force group lines in smb.conf solved the problem.

---

### Post by crimson30 on 2008-10-18
Commenting out worked for me.

THANK YOU!

---

### Post by ub-newbie on 2008-11-28
Worked here also.  Went into /etc/samba, then opened smb.conf with "gksu gedit" and made the change.  Restarted samba with "sudo /etc/init.d/samba stop" then "sudo /etc/init.d/samba start".  I saw results immediately.  Thanks for the tip.

---

### Post by Utemetsu on 2009-03-21
Thanks so much for the help. Been Stumped for days!


I can't remember how many times i've combed the samba file to figure it all out. Much apprieciated!

Cheers,
Utemetsu

---

### Post by jimnz111 on 2009-03-29
I did an upgrade to latest ubuntu distro (from 8.04 to 8.10) and Samba was updated to 3.23 which fixed issue. 

It shows as BUG 5696 fix [http://samba.org/samba/history/samba-3.2.2.html]("http://samba.org/samba/history/samba-3.2.2.html"), but look out! Me thinks between 3.23 and 3.32 it will break again because the 3.32 release shows BUG 6155 [http://samba.org/samba/history/samba-3.3.2.html]("http://samba.org/samba/history/samba-3.3.2.html") fixed...

---

