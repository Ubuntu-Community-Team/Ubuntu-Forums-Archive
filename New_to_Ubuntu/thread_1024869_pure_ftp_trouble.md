---
title: "pure ftp trouble"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by edcouch on 2008-12-29
Hello folks!
I am trying to set up pure admin-pure ftp, and I add a user, with a user name and password, but when that user tries to connect, the log says: user ed OK, then password, XXXXX
530 login authentication failed

Obviously I have missed something in the settings and I would sure appreciate some help with this.  
Thank you in advance.

---

### Post by cmnorton on 2008-12-29
How are you adding this user, through Linux or pure ftp? 

If you are adding through pure ftp, is there a mapping going on, so that your pure ftp users are logging in as a dedicated Linux user?

I would look in your logs, (/var/log/*) to see if there are any clues. syslog and messages are a good place to start.

---

### Post by edcouch on 2008-12-29
thank you for your reply, I am adding users through Pure Ftp and I really don't know what to look for in any of those files.

---

### Post by cmnorton on 2008-12-30
Without knowing more about how pure ftp works, this sounds like you either need to add Linux ftp users, or pure ftp has a way to map lots of users onto one linux account.

---

### Post by edcouch on 2008-12-30
Thanks again for your reply, and you are probably correct in that I need to add linux ftp users, but could you tell me how to do this?
Thanks

---

### Post by ZhiZaki on 2008-12-30
> **edcouch said:**
> Thanks again for your reply, and you are probably correct in that I need to add linux ftp users, but could you tell me how to do this?
Thanks

I think these links should help you better understand the ftp server you have picked. 

[http://www.pureftpd.org/project/pure-ftpd/doc](http://www.pureftpd.org/project/pure-ftpd/doc)

[http://download.pureftpd.org/pub/pure-ftpd/doc/README.Virtual-Users](http://download.pureftpd.org/pub/pure-ftpd/doc/README.Virtual-Users)

---

### Post by cmnorton on 2008-12-30
> **edcouch said:**
> Thanks again for your reply, and you are probably correct in that I need to add linux ftp users, but could you tell me how to do this?
Thanks

I would first read the links posted by [ZhiZaki]("http://ubuntuforums.org/member.php?u=733224"), but if you have to add users:

First, look at man useradd

With Ubuntu (Debian) systems, you have to specify that the home directory be created

sudo useradd --create-home --shell bash <some_user_name>

You should also be able to do this from the admin terminal, if you prefer not to use a command line.

---

