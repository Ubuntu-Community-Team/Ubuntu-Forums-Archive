---
title: "keyring question"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by RaceNChase on 2010-04-15
Ok, journey of a noob, I wanted to try 10.04 but was having difficulties with the externals, such as wine, etc.  As external repos tend to be at 9.10 so I regressed to current production and will give 10.04 a few weeks being out before upgrading.  Also my Linux "friend" says that once everything is established the upgrades tend to go "smoothly" un huh guess i will have to wait and see.

The question I have is how do I turn off the "keyring" it is bothersome that it doesn't even have a remember my choice checkbox.  Every time I log in I have to approve the use of the wireless connection.  I know who cares, but it is slightly annoying and I would like to turn it off or atleast turn it down to where it remembers my answers.

thank you

---

### Post by empty_spaces on 2010-04-15
Try this first.
Right click on the Network Manager on the panel -> Edit connections -> Wireless tab -> Select your network -> Edit -> Check the box next to "Available to all users"
Restart and see if this solves your issue.

If the issue persists, Go to Applications -> Accessories -> Passwords and Encryption Keys.
In the passwords tab, Right-click on "Passwords:login" -> Change password. Enter your existing password, but leave the new password fields blank. Click OK for "Use unsafe storage". Restart computer.

This second method should work, if the first one doesn't.

---

### Post by RaceNChase on 2010-04-15
thank you!

---

### Post by empty_spaces on 2010-04-15
just curious, did the first method work or the second?

---

