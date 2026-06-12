---
title: "Netbook 9.10 Brightness Problem"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by SPazzo on 2009-11-23
I just installed a dual-boot of Ubuntu 9.10 with Windows XP on my new Netbook.  The netbook is a MSI Wind U123.  [Here are the specs.]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=4786234&CatId=3987")

When I was installing Ubuntu (with a thumbdrive made with Unetbootin) I accidentally pressed Function + F5; that is supposed brighten the screen.  After I hit that it the screen started going wonky.  It kept getting brighter and then darkening, and the little menu that shows the brightness bar came up, and the bar kept going up and down.

It finished the installation and restarted.  But when I got to the log-in screen it kept doing the brighter and darker thing.  If I hit Function + F5 (or F4 to darken) it doesn't stop.  If I log in it still does it for a minute or so and then stops.  If I hit Function + F5 (or F4) it does it again for a while.

It doesn't do this in XP.  Is there a way to get rid of this?  If not, is there a way to re-install Ubuntu completely *without* getting rid of XP?

Thanks!

---

### Post by SPazzo on 2009-11-24
UPDATE:

So I tried reinstalling Ubuntu over the old partition, it worked ok, but the brightness flickering problem still happens.

Right now I'm reinstalling Windows XP over everything using BartPE and [these]("http://www.vandomburg.net/installing-windows-xp-from-usb/") instructions.

If *anyone* has any tips or ideas PLEASE let me know.

---

### Post by Gadgetech on 2009-11-25
I have the same problem on my Wind U100, so I'm still running Jaunty on it. You could install Hardy or Jaunty over top of Karmic just like you're doing a fresh install. 

Instead of using guided partitioning during the install, select manual partitioning and select your current Karmic partition to be overwritten.

---

### Post by cybil on 2009-11-25
I am having the same issues on a LAM re-branded netbook.

---

### Post by SPazzo on 2009-11-25
> **Gadgetech said:**
> I have the same problem on my Wind U100, so I'm still running Jaunty on it. You could install Hardy or Jaunty over top of Karmic just like you're doing a fresh install. 

Instead of using guided partitioning during the install, select manual partitioning and select your current Karmic partition to be overwritten.

I did try installing Karmic over the old Karmic.  It didn't work. :p  I reset Windows completely, and now I'll just install Jaunty or Hardy (I haven't decided yet...).

---

### Post by cybil on 2009-11-25
Check out this post.  It fixed it for me, but the video is now sluggish :(
[http://ubuntuforums.org/showthread.php?t=1311491&highlight=karmic+brightness](http://ubuntuforums.org/showthread.php?t=1311491&highlight=karmic+brightness)

---

### Post by SPazzo on 2009-11-25
> **cybil said:**
> Check out this post.  It fixed it for me, but the video is now sluggish :(
[http://ubuntuforums.org/showthread.php?t=1311491&highlight=karmic+brightness](http://ubuntuforums.org/showthread.php?t=1311491&highlight=karmic+brightness)


OK, I think I'll just try installing Jaunty or Hardy.  Which one should I install?

---

### Post by cybil on 2009-11-25
I did not have the problem with Jaunty

---

### Post by SPazzo on 2009-11-25
[Gadgetech]("http://ubuntuforums.org/member.php?u=643576") also just told me that Jaunty should work.  Thanks to both of you, and I'm about to make a bottable USB drive.

---

