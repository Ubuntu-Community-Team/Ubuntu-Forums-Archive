---
title: "system freezes when turning off key ring"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by pottzie on 2011-02-21
My system locks up when I try to enter my password to unlock the key ring. Key ring pops up when I am asked for password for a new wireless set up.
 I would like to run fsck, but can't once the system is mounted. What's the way to get fsck to run on a single-system set up? Also, is there a way to bypass the GUI keyring password verification, or even by going in via the Applications drop-down on the tool bar?

 Have had this install of Ubuntu 10.10 working for months now, without a problem. Problem only surfaced when trying to add a password for a new router. Ubuntu 32-bit, and the problem may be caused by the fact that I have to use ndiswrapper to get the receiver to work.
 Both the mouse and the keyboard freeze when I try to input the first letter of my password. Is that a symptom of X going out of whack?

---

### Post by cariboo on 2011-02-21
You can run fsck when you boot from the Live CD, this may solve your problem. You can always create a blank password for the keyring, Go to Accessories-> Passwords and Encryption, right click the current password and select change password.

---

### Post by pottzie on 2011-02-21
Setting the key ring password as blank worked. Thanks.

---

