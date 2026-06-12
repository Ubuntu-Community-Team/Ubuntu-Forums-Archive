---
title: "Can't Open User Account after Power Cut"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by the.dark.lord on 2010-05-01
I was using the computer on my main (and admin) user account, when there was a power cut. This seems to have caused some error- as I cannot log in to that account; however, the other user account I have on the computer works fine.

Help! Thanks.

---

### Post by quadproc on 2010-05-01
> **the.dark.lord said:**
> I was using the computer on my main (and admin) user account, when there was a power cut. This seems to have caused some error- as I cannot log in to that account; however, the other user account I have on the computer works fine.

Help! Thanks.
It is quite possible that the power loss caused some damage to one or more files in your system, and that those files are needed for the login.

Here are a couple of ideas that might help:

1. If you have a Live CD, boot from that.  When you get a working system then use it to reset your main account's password.  Then see if you can log in.

2. Since you are apparently able to boot the system normally, you could use recovery mode (this is normally the selection just under your usual boot choice) and use the command line interface to reset the password on your main account.  Alternatively, you could create a new administrative account and use that one to repair the original one.

quadproc

---

### Post by the.dark.lord on 2010-05-01
Thanks!

How do you change another user to admin using the command line?

---

### Post by quadproc on 2010-05-01
> **the.dark.lord said:**
> Thanks!

How do you change another user to admin using the command line?
I am not aware of being able to change a user, but you should be able to create a new user and use that one instead.

quadproc

---

