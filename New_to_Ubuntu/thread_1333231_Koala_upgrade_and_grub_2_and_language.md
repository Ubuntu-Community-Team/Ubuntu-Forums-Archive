---
title: "Koala upgrade and grub 2 and language"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by zhanglini on 2009-11-21
Hey,
I just upgraded my laptop from 9.04 to 9.10 and when I boot, it still says "stage grub 1.5", I thought Koala has 2.0 now.  How do I fix this?
And I used to have CHinese as my default language, now it is all English.  If I go to the "Options" at the login screen, and choose "other language", there is no language option there, do I need to install something?
Thanks in advance!

---

### Post by davec64 on 2009-11-21
Have alook and see where the installer put Grub2.
I have a number of IDE drives and I later added a SATA drive previously my first drive in Jaunty was an IDE drive (boot) however, Karmic decided the SATA drive was the first one and installed Grub2 here incorrectly. Reinstalling Grub2 to my IDE drive solved my problem.

As far as the language goes, i'm not sure! Do you need to add some language packs?

All the best

:)

---

### Post by zhanglini on 2009-11-21
Well, I have only one HD, partitioned into /, /boot, /home and swap.  So grub 2 should not have been misplaced, right?

How do I check and add language packs?

---

### Post by davec64 on 2009-11-21
By the sounds of it, Grub2 never installed.

Have a look here:
[https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")

Looking at that page it implies Grub2 isn't installed during an upgrade:

> GRUB 2 will be installed by default on NEW installations of Karmic. If you have upgraded from Jaunty 9.04 to Karmic 9.10 you can follow the install instructions for Jaunty 9.04 below. 

That should get you up and running with Grub2!

Right then, the Language problem!

Once you're in to the system try:

System >> Administration >> Language Support

And see if you can add additional languages.

Hope that helps! Post back and let me know how you got on! :)

Dave

---

### Post by zhanglini on 2009-11-21
Well, I got the language part by using "language support".  When I installed grub 2, I ended up with "error 15", both menu.lst and grub.cfg were NOT there.
So I reinstalled:p and all is well.
Thanks Dave!

---

### Post by davec64 on 2009-11-21
Nice one! :)

---

