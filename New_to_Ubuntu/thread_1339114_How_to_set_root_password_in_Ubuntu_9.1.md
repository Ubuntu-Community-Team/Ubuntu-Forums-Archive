---
title: "How to set root password in Ubuntu 9.1"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by coka on 2009-11-27
HI all
How to set a root password in Ubuntu 9.1
i tried admis--> user group 
but it is not working

---

### Post by NickJones on 2009-11-27
System, Administration, Users and Groups, Click the keys, Type password, Click on Root, Click Properties,
Nick

---

### Post by coka on 2009-11-27
i have done d same in 8.04 bt now working in my 9.1:(

---

### Post by NickJones on 2009-11-27
So its not working or it is?

---

### Post by Cheesemill on 2009-11-27
I'm afraid we can't tell you that:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by Iowan on 2009-11-27
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by anaconda on 2009-11-27
> **Cheesemill said:**
> I'm afraid we can't tell you that:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

Yes we can!

As the link you pointed out tells helping to enable GRAPHICAL root login is not supported (not allowed)

But enabling root accout, ie. giving root a password is "allowed".. And this can be necessary, eg. if you want to disable passwordless booting to "rescue mode"

One way that has worked in every distro I know of is the terminal. Just type:
```
sudo passwd root
```
and it will ask first your sudo password, and then the new password for root....

---

### Post by coka on 2009-11-27
Done 
Thanks all

---

### Post by aysiu on 2009-11-28
> **Cheesemill said:**
> I'm afraid we can't tell you that:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
This.

---

