---
title: "What's messed up now... Does this have to do with Compiz?"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by Lucypie on 2011-08-11
Yay. After installing Compiz, everything starts flubbering up. On another post I postedd, I was told how to disable compiz. I really don't want to disable it because I *LOVE* my visual effects. But if all these problems string from Compiz, I shall.. Please don't say download an ything because I am on limited internet. When the internet resets (which I have no idea when that is) I will maybe DL a few things but not much. Anyways, on to the problem...
 

Ubuntu 11.04 using the classic theme.
4GB RAM, 300GB (I think) HDD 

When I go to places and click on a folder or something, it goes to the bottom and says "Opening ......" and then after about 20 second, disappears. When I log out / log in / restart  it returns to normal for a short time. Sometimes my desktop disappears with it. :/ So what's wrong?

---

### Post by CatKiller on 2011-08-11
Running ```
nautilus
``` in a Terminal window might let you see any error messages that could help you diagnose the problem.

---

### Post by Lucypie on 2011-08-11
alyssa@ubuntu:~$ nautilus

(nautilus:17309): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by Lucypie on 2011-08-11
I just when into ubuntu classic (no effects) mode. Now I can't even click my icons. I opened one folder, and I cannot open any more. I can't do anything/ What the heck!

---

### Post by CatKiller on 2011-08-11
How about ```
nautilus --no-desktop
``` or ```
dbus-launch nautilus
``` (found from [this bug report]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/334806"))

---

### Post by ajgreeny on 2011-08-11
If you can get to a terminal try command ```
gconftool-2 --recursive-unset /apps/compiz-1
```to reset compiz to the default for 11.04.

---

### Post by yaddoshi on 2011-08-11
Do you know what type of hardware your system has for graphics (ie: nVidia, ATI or AMD, Intel)?  If so, are you using the default drivers that ship with Ubuntu or are you using proprietary drivers (if you are using Intel video you can disregard this question).

Do you have the latest updates and kernel installed?

What steps did you follow in order to install Compiz?

Just a quick note - the Ubuntu dev team is moving away from X11 for desktop rendering, consequently special effects and such that used to work great in 10.10 or earlier may not behave as expected in 11.04 and 11.10.

If it was my system, I'd try to revert it back to the state it was in before installing Compiz.  Ubuntu 11.04 already ships with certain desktop effects, but adding unsupported packages could cause issues.  I'd also make sure I have all updates installed and that I was running on the latest available kernel.

After getting it back to that original state, I would probably try to figure out whether the issues are caused by graphics drivers.  

If I had installed proprietary drivers for my ATI/AMD/nVidia graphics card, I would try uninstalling them and test how Compiz behaves with the default drivers that ship with Ubuntu.  

If I was just using the default drivers to begin with, I would try using the proprietary drivers recommended by Ubuntu (usually a notification will show up in the system tray if proprietary drivers are available shortly after the system has booted up for the first time, but you can also find them under System > Administration in the Ubuntu Classic menus).

If I had tried the proprietary drivers that are recommended by Ubuntu and I had also tried the open source drivers that ship with Ubuntu and neither are working, I would try the drivers available for the card manufacturer.  I don't personally use nVidia products in any of my systems so I can't offer you much support there, but you can download ATI/AMD graphic drivers straight from [AMD]("http://www.amd.com") and there is a guided Howto on how to install their drivers [available here]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide") (this link is also on their LINUX driver page).

Good luck! :)

---

### Post by Lucypie on 2011-08-11
First one opens with no error, second opens,. but with error.


Initializing nautilus-gdu extension

(nautilus:31323): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:31323): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:31323): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:31323): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:31323): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:31323): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:31323): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:31323): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.



and after running these commands I now am able to click icons again and open folders.... at least for now.

---

### Post by CatKiller on 2011-08-11
OK, so it might be related to the system to mount and display drives on the Desktop. GDU is gnome-disk-utility, as far as I can tell. Might explain why --no-desktop helped. I don't really have any other ideas at the moment.

Glad it's currently working, though.

---

