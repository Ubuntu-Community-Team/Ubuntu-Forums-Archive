---
title: "Failure to boot with Glib warning on Desktop using Lucid"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by mikodo on 2010-09-05
Hello everyone,

The last 24 hours or so, icons/applets, or whatever they are properly called, have failed to be placed in the panels. First the date and time and then the trash icon. Both times re-booting, produced them in the panel as before.

This morning when starting my computer, it didn't boot into the desktop with the following message given :

```
(process:327 Glibwarning**: getpwuid_r(): failed due to unknown user id (O)

```I am the only user on this desktop computer and have never had this problem before. All update are always installed, as offered.

I did Ctrl + Alt + Delete and the system booted and produced the desktop,  as per normal.

Does anyone have any ideas, what might be happening and what can be done to correct this behavior?

Thank you.

---

### Post by ivanovnegro on 2010-09-08
> **mikodo said:**
> Hello everyone,

The last 24 hours or so, icons/applets, or whatever they are properly called, have failed to be placed in the panels. First the date and time and then the trash icon. Both times re-booting, produced them in the panel as before.

This morning when starting my computer, it didn't boot into the desktop with the following message given :

```
(process:327 Glibwarning**: getpwuid_r(): failed due to unknown user id (O)

```I am the only user on this desktop computer and have never had this problem before. All update are always installed, as offered.



I did Ctrl + Alt + Delete and the system booted and produced the desktop,  as per normal.

Does anyone have any ideas, what might be happening and what can be done to correct this behavior?

Thank you.

Today is my first day when appeared the same warning before login to my system, but I hadnt problems on my machine, I logged in without problems and eveything is working well but I dont know what this mysterious message will say to me.
Im on Mint 9 and I installed on the notebook of my sister yesterday Mint 9 LXDE, the same warning before login but the machine works.

---

### Post by inameiname on 2010-09-08
Here is a large thread about the same thing. Unfortunately, there is no solution yet. It's a bug that started in Lucid, to what we think Plymouth and/or EXT4 file system might be the main culprit(s).

[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

---

### Post by ivanovnegro on 2010-09-08
> **inameiname said:**
> Here is a large thread about the same thing. Unfortunately, there is no solution yet. It's a bug that started in Lucid, to what we think Plymouth and/or EXT4 file system might be the main culprit(s).

[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

Thanks for the info.

---

### Post by mikodo on 2010-09-08
Hello, From this thread:

[ http://ubuntuforums.org/showthread.php?t=1443231]("http://ubuntuforums.org/showthread.php?t=1443231")

People are wondering if the bug is in ureadahead. They are noticing that this behavior is happening after a disk check. I got the warning a second time today, right after an earlier boot ran a disk check. Hmm.....

Thanks for pointing out the thread.

---

