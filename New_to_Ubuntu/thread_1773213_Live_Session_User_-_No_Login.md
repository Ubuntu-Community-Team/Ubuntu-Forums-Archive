---
title: "Live Session User - No Login?"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by Anseis on 2011-06-01
I have installed Natty Narwhal 11.04 on a USB Drive.  Most is working well and I have added users for non administrative tasks.

However, whenever I boot, the system automatically starts as the default "Live Session User" no login or password required.  Because the Live Session User has "sudo" privileges, I would like to force a user to enter the password.

I have been able to set a persistent password using System Settings >> Users and Groups.

I think I could just change the privileges of ubuntu@ubuntu (live session user) but am unsure if this is wise.

I have searched a while in the forums but not found this question addressed anywhere so if someone could point me in the right direction, I would appreciate it.

Thanks!

---

### Post by jtarin on 2011-06-01
[Is this what your after?]("https://help.ubuntu.com/community/LiveCD/Persistence")

---

### Post by Anseis on 2011-06-02
I found my own answer. :redface: If I had been a little more patient I would have found a tool for setting the login function: System Settings >> Login Screen.

Because I am running from a LiveCD ISO installed on a USB, the default set up is intended more for performing new installations than as a standalone OS, hence the default automatic login is as ubuntu@ubuntu (Live Session User).

---

