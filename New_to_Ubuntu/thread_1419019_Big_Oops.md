---
title: "Big Oops"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by TiggerIB on 2010-03-01
Good morning,

I somehow managed to kill my only account's super user ability and have lost the ability to use the sudo command. I tried logging in as root; however, the system laughed at me multiple times. Is there a way to regain the super user / sudo access on this normal account or do I need to reinstall ubuntu?

I have tried using the following commands in terminal mode:
sudo su -
sudo -l
sudo -s

I am currently running ubuntu 9.10

Thanks Tig

---

### Post by sisco311 on 2010-03-01
What error message you get when you try to use sudo?

Anyway, this should help:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by TiggerIB on 2010-03-01
I get the following error"

tigger is not in the sudoers file.  This incident will be reported.

---

### Post by sisco311 on 2010-03-01
Reboot in *Recovery Mode* and add your user to the *admin* group. For detailed instructions, check out the link from my first reply.

---

### Post by TiggerIB on 2010-03-01
WOW  Many thanks!!!!!!

---

