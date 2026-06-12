---
title: "Login as Root or as Guest?"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by cuongjj on 2010-08-24
I was wondering when playing around on the computer doing normal things, Do you guys advise to login as root or as a guest?  I read somewhere that Its best to login as guest.  **Can someone please explain to me why?**

Thanks in advance! Keep up the good work guys.

---

### Post by Zzl1xndd on 2010-08-25
Normally (the Default) with Ubuntu you would not have a root account. You would have a normal user account that can elevate its privileges when root access is needed.

The reason running as Root is discouraged is that it can be a security issue.

---

### Post by Rubi1200 on 2010-08-25
The root account is disabled by default on Ubuntu. It is also unnecessary (and dangerous) to use it for normal daily usage. You can elevate privileges using sudo.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cuongjj on 2010-08-25
thank you for this information. how do I mark that this thread is solved?

---

### Post by Sef on 2010-08-25
> cuongjj - thank you for this information. how do I mark that this thread is solved?

Under thread tools there is that option.

---

### Post by 3rdalbum on 2010-08-25
You should log in as a normal user, if you are a frequent user of the computer.

Do not let anyone else log in under your user account. They should either have their own user account, or you can switch to the guest account for them. The guest account has greater security and more restrictions.

---

