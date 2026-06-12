---
title: "Ubuntu asks twice for my password after screen lock"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by Blutkoete on 2010-11-19
Hello!

Since today, when the screensaver starts and the system is locked, I have to enter my password twice before I can work again.

After the first time, the desktop pops up for about one second, then it switches back to the locked screen and I have to enter the password a second time. I think it has something to do with the screen saver, but I haven't changed that or any lock screen options for weeks.

Is that a known bug and/or something I can do about it?

Thank you,

Blutkoete

---

### Post by Blutkoete on 2010-11-19
A short addition: It actually happens this way:

1) I enter my password; the system accepts it and shows me the desktop.

2) After one or two seconds, the screen saver appears again for a second, followed by the the login window

3) I enter my password again, the system accepts it and shows me the desktop.

Maybe the screen saver is kind of deactivating too slow? Is there a log or something to check that?

It happens since the last update.

---

### Post by darrenleeweber on 2010-11-26
Exactly same problem for me on Ubuntu 10.04 with Gnome desktop and the screen lock option on.  This is on Lenovo ThinkPad T61.

---

### Post by uiarchitect on 2010-12-03
Solution to this problem is posted here - [http://ubuntuforums.org/archive/index.php/t-503976.html](http://ubuntuforums.org/archive/index.php/t-503976.html)

---

### Post by revnoah on 2013-01-12
For me, the problem was caused by an unsuccessful install of the fingerprint scanner software. Commenting out a line in common-auth did the trick for me.

[http://ubuntuforums.org/showpost.php?p=5477383&postcount=8](http://ubuntuforums.org/showpost.php?p=5477383&postcount=8)

---

### Post by overdrank on 2013-01-12
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

