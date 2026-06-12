---
title: "How do I find out my usernam/password"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by gnarkilljboy on 2008-05-11
I created a file share between my laptop which is running Ubuntu, and my pc, which has windows xp. But when I try to access the laptop, it says I need my user name and password. I tried the one for when I log onto ubuntu, but it does not work. any ideas?

---

### Post by .rdg on 2008-05-11
You need to use a user/password duo which are on Windows XP, not on Ubuntu.

---

### Post by Iowan on 2008-05-12
There are ways to link Windows user names to Ubuntu/Samba usernames, but the easiest is to insure that the username/password on the Windows machine are the same as a username/password on Ubuntu AND Samba.  
Use the **adduser** to create a Ubuntu user and **passwd** to set a user password. The **smbpasswd -a** can then be used to create a Samba username/password.

There are other posts around that probably explain this better.

---

