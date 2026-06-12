---
title: "Customize grub2 menu problem"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by ubume2 on 2010-06-18
I don't know if this is an absolute beginners question, but here goes.

I've read some of the tutorials and helps.  I triple boot Lucid, Karmic, and Windows XP.  I want the menu entry to show Ubuntu Lucid, Ubuntu Karmic instead of the the names used in grub.cfg.

Following advice on one tutorial, I put in custom menu entries into /etc/grub.d/06_custom.

I  do get the custom entries first in the grub menu, but at the tail end I also get what is written into grub.cfg.

All of the tutorials recommend against changing grub.cfg.

Is there a way to override grub.cfg to get only the entries in 06_custom?

Thanks

---

### Post by Irony on 2010-06-18
> **ubume2 said:**
> Is there a way to override grub.cfg to get only the entries in 06_custom?
No.

When it comes to simple, clean custom configuration Grub 2 is a big step backwards from Grub 1.

In fact it just a big step backwards, with files all over the place.

---

### Post by oldfred on 2010-06-18
Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
OR Partial Custom:
I used drs305's command to limit Ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

You can also modify scripts to put in different names but you have to be willing to modify scripts rather than text files.

General info:
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by ubume2 on 2010-06-18
They don't make it easy do they?

Oh, for the days of stage 1 and menu.lst!

Thanks.

---

### Post by Irony on 2010-06-18
Did I mention how much I loath Grub 2.

---

### Post by oldfred on 2010-06-18
You must not have been here with all the issues on grub legacy. It often did not find windows and we had to create manual entries. Users regularly put windows stanzas into the "magic" area and wondered why after a kernel update their windows entry disappeared.

Yes you have to edit in two different places if you want custom entries, but custom entries are rarely required for the average user. You really only have to edit /etc/default/grub/

I look at it as a trade off. Only advanced users want that much customization and because it offers more features it is more complexs and the default works better for the average user.

---

### Post by Irony on 2010-06-18
Really Grub 2 is just awful.

---

### Post by Zintha on 2010-06-18
> **Irony said:**
> Really Grub 2 is just awful.
Its fantastic!
Until you use the version before it, then you realize how it really -really- is a step back.

---

### Post by ubume2 on 2010-06-19
[QUOTE=oldfred;9479334]Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
OR Partial Custom:
I used drs305's command to limit Ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

The drs305 post really helped clean up the grub menu.  Thanks oldfred!

---

### Post by ubume2 on 2010-06-19
Thanks oldfred. Following the drs305 thread really helped clean up the grub menu.

---

### Post by oldfred on 2010-06-19
Glad it worked. You are welcome.

If you could add solved, others may find thread and see a solution.

---

### Post by Irony on 2010-06-22
> **Zintha said:**
> Until you use the version before it, then you realize how it really -really- is a step back.
Yup, Grub 2 is the most horrible thing to hit a distro since the most horrible thing you can think of, here are the words of one expert on the subject; [http://shallowsky.com/blog/linux/grub2-lightning.html](http://shallowsky.com/blog/linux/grub2-lightning.html)

---

