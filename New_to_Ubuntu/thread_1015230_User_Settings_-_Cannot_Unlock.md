---
title: "User Settings - Cannot Unlock"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by oopsHelp on 2008-12-18
Hi,

I just installed Ubuntu and because I am a security conscious idiot I got worried that the first user that is created has administrative priveleges, so I went to System > Admin > Users and Groups and unlocked with my first user password to change my own user priveleges and unticking "administer".

I only found out because my screen size is huge and wanted to change it but couldn't because I couldn't sudo.

This is what I tried to do to change my resolution: 
[http://www.linuxquestions.org/questions/linux-newbie-8/screen-resolution-problem-in-ubuntu-362160/](http://www.linuxquestions.org/questions/linux-newbie-8/screen-resolution-problem-in-ubuntu-362160/)

Please help. I think I have to create a root password and change some config files but how do I create a root password when I have no admin priveleges and the root account is locked by default, not allowing login?

Thanks for any help

---

### Post by Michael.Godawski on 2008-12-18
> **oopsHelp said:**
> Hi,

I just installed Ubuntu and because I am a security conscious idiot I got worried that the first user that is created has administrative priveleges, so I went to System > Admin > Users and Groups and unlocked with my first user password to change my own user priveleges and unticking "administer".

I only found out because my screen size is huge and wanted to change it but couldn't because I couldn't sudo.

This is what I tried to do to change my resolution: 
[http://www.linuxquestions.org/questions/linux-newbie-8/screen-resolution-problem-in-ubuntu-362160/](http://www.linuxquestions.org/questions/linux-newbie-8/screen-resolution-problem-in-ubuntu-362160/)

Please help. I think I have to create a root password and change some config files but how do I create a root password when I have no admin priveleges and the root account is locked by default, not allowing login?

Thanks for any help

Hi, have a look here:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by jimmy the saint on 2008-12-18
[http://ubuntuforums.org/showthread.php?t=9805](http://ubuntuforums.org/showthread.php?t=9805)
That should do just fine for you.

---

### Post by oopsHelp on 2008-12-18
> **Michael.Godawski said:**
> Hi, have a look here:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Ah that was easy peasy. I just created a new user and put it in the admin group.

Thank you

I installed the NVIDIA drivers and got back a proper screen resolution. Messing around with xorg.conf did not work.

---

