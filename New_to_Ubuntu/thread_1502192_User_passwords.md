---
title: "User passwords"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by chandrav23 on 2010-06-05
Hi,
 
I forgot my ubuntu system-user password.How can i get it? Also can we login with root password?
 
 
Thanks

---

### Post by lisati on 2010-06-05
We can probably help you set a new password. The easiest way is to log in to recovery mode and set it from there.

As for the root password, have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by chandrav23 on 2010-06-05
Thanks,
 
how to set new password with out current passoword?
 
Pls give me indetail.
 
 
Regards
ch

---

### Post by warfacegod on 2010-06-05
> **chandrav23 said:**
> Hi,
 
I forgot my ubuntu system-user password.How can i get it? Also can we login with root password?
 
 
Thanks

By default root doesn't have a password and shouldn't. If you want to log in as root, select the recovery kernel heading in GRUB (if GRUB doesn't show, during boot hold shift or escape, I can't remember which). When it loads, select Drop to shell and type startx. Be very careful when root, you can easily break your system.

To change the password for your user, go through the same process but instead of startx type your username passwd. Example: thefishlives passwd

Then enter a new password.

---

### Post by sisco311 on 2010-06-05
> **chandrav23 said:**
> Thanks,
 
how to set new password with out current passoword?
 
Pls give me indetail.
 
 
Regards
ch

[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by chandrav23 on 2010-06-05
Hi guys,

I undersood...............

Its working

Thanks
Ch

---

### Post by sisco311 on 2010-06-05
Cool!

Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

