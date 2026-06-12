---
title: "keyring"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by loyaleagle on 2009-03-02
Hello everyone,

Just a question. I seem not to understand the keyring thing all that well. I tried to look up the subject by searching this forum, but came up with more questions then answers.

Here is my issue:
1) When I sign into Ubuntu, it asks me for the keyring password in order to get full functionality of the Gnome Do Google plugins. Why? and How can I avoid this in the future.

2) My wireless does not sign on automatically when I boot up and it asks me for the keyring password every time. Very annoying.


Thank you for any suggestion on how to fix these small issues.

---

### Post by loyaleagle on 2009-03-03
Found this explanation and answered my own questions.... sorry!

Seahorse is Gnome's keyring manager (The one that opens when you go to Applications/Accessories/Passwords and encryption keys).

And the keyring is the way how programs can store their important encryption keys and passwords etc, so that you don't have to type them all the time yourself.

If you use the normal login (typing user name & password to login) the keyring gets unlocked automatically, but if you are using automatic login instead you need to give keyring password before programs can access keys & passwords stored in keyring. Removing the keyring password solves this, if you don't need the security.

---

