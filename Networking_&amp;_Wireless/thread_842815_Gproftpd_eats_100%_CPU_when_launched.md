---
title: "Gproftpd eats 100% CPU when launched"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by austin987 on 2008-06-27
Howdy,

I'm about to go on a vacation, and before leaving, was checking our ftp/fileserver for any problems and showing my coworker how to administrate some things. When testing gproftpd, I found that it's eating 100% of cpu, and never drawing it's screen. I'm not sure what's changed between now and when it last worked. The box is an old dual cpu pentium 3, running xubuntu feisty. Proftpd works fine, just can't do any GUI configuration. Firefox/etc., are not eating crazy amounts of cpu, so not sure what to investigate first. Any help is greatly appreciated.]

---

### Post by austin987 on 2008-06-30
bump

---

### Post by austin987 on 2008-07-01
Found a similar report here:
[http://ubuntuforums.org/archive/index.php/t-285995.html](http://ubuntuforums.org/archive/index.php/t-285995.html)

as well as a bug report:
[https://bugs.launchpad.net/ubuntu/+source/gproftpd/+bug/74368](https://bugs.launchpad.net/ubuntu/+source/gproftpd/+bug/74368)

administrator@SERVER1:/home/administrator$ sudo gproftpd

** (gproftpd:8922): WARNING **: Couldn't find pixmap file: gproftpd.png

(gproftpd:8922): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

I've tried copying/moving/symlinking /usr/share/icons/gproftpd.png to /usr/share/pixmaps/gproftpd.png, but it makes no difference.

---

