---
title: "newbie samba setup for XP to acces shared folder"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by lpketter on 2007-10-19
I am somewhat new to Ubuntu (have 7.10 installed, Ath64 version).  From System> Administration> shared folders    I enabled a new directory /usr/public   to be shared, with read only unchecked (if I understand correctly this allows executing and reading, I'm not sure about writing other than for the owner).

From my wife's (the XP computer [XP, service Pack2]) I can 'see' my computer, but it is asking for a user id and password to connect....  Do I need to set up an account for her as a user on my Ubuntu machine, then setup her machine to keep the user name and password remembered to allow her to get to /usr/public and at least execute and read?

If someone could point me to a HOWTO or discussion that would help, I'd really appreciate it.  I did not find one searching on the forum, or the Ubuntu docs or community.  I am not new to linux, but am to Ubuntu (have played a little with 7.04, but not too much) , SAMBA, and windows networking in any real administrative way....

Thanks...

---

### Post by confusedstingray on 2007-10-19
i had the same problem but from what i read 
you just change in the 
/etc/samba/smb.conf

change the line 
           security = user 
to 
 security = SHARE

also if this link may help 
[http://www.go2linux.org/node/98](http://www.go2linux.org/node/98)

---

