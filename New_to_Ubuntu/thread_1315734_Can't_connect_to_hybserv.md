---
title: "Can't connect to hybserv"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Remagen on 2009-11-05
This is rather annoying.  I set up a hyberserv on my server; went through the config files etc.

Then, I set up xchat to connect, and get this output:
Connected... now logging in...

Hyberserv (...version info...)
Username:
Password:
Invalid password!
Disconnected.

Ok.  So I go back to my hybserv.conf file; to the appropriate users line:
O:matthew@dormix:MPA6J5VLmfhJE:aminet:segj
MPA... is the password sent through mkpasswd

Comparing this to my xchat connection settings:
Nickname:aminet
Username:matthew@dormix
Realname:*empty*
NickservPass:*empty*
ServerPass:(what would be MPA... if sent thru mkpasswd)

What am I doing wrong? I also have the I line set to basically allow a max of 5 users from anyone.

---

