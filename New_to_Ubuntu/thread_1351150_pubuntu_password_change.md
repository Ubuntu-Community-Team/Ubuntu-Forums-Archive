---
title: "pubuntu password change"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by skyjacker on 2009-12-10
I have put pubuntu on a usb key, and it works very good (this program puts the os in a virtual window in xp). Problem: during the install, I was not given the chance to assign a root password, and now cannot use synaptic, or receive new updates. How can I assign a password to allow me to do these things?  Thanks in advance!

---

### Post by RedSingularity on 2009-12-11
Try this

sudo passwd root

---

### Post by abeisgreat on 2009-12-11
You don't need a root password to do these things, you need your password. You are part of the "admin" groups, which means you can pretend to be root by giving it your password. Try just entering the password you set for your account.

---

### Post by skyjacker on 2009-12-12
> **abeisgreat said:**
> You don't need a root password to do these things, you need your password. You are part of the "admin" groups, which means you can pretend to be root by giving it your password. Try just entering the password you set for your account.Like I said, I was not given the opportunity to assign a password during the initial process. What can I do now?

---

### Post by skyjacker on 2009-12-13
Never mind, I finally found the answer on the internet.

---

### Post by RedSingularity on 2009-12-13
What did you do?

---

### Post by reapur on 2010-01-02
> **RedSingularity said:**
> What did you do?

The pubuntu user password is: 123456
sudo change the root password and then change pubuntu's passowrd.

---

