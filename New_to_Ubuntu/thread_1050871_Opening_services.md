---
title: "Opening services"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by andr3w on 2009-01-26
I installed through the alternate cd.
I enabled root. (Why?)
In case of compromise, I'd like root to have a pwd.

I'm logged in as the regular user. I've put myself in the sudoers file.
I can't open services!

The menu's properties say: "services-admin"  
I tried putting gksu before that. -doesn't work
I tried opening it in the run dialog with gksu behind it, -doesn't work.
I can't open it. Why not?

I haven't edited anything, I just installed.
Why in the world does it say that Truecrypt is running?
(And it's not in the processes menu)

So, I can't even look @ what starts up with the computer.

It looks like the other admin programs are opening fine.
[[IMG]http://img172.imageshack.us/img172/1641/screenshotzs9.th.png[/IMG]](http://img172.imageshack.us/my.php?image=screenshotzs9.png)

Tried this [http://www.mail-archive.com/gnome-list@gnome.org/msg01873.html](http://www.mail-archive.com/gnome-list@gnome.org/msg01873.html) -doesn't work.
[URL="http://bbs.archlinux.org/viewtopic.php?id=42910"]
This[/URL] isn't working.
This [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/112102/comments/1](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/112102/comments/1) doesn't work.

---

### Post by gettinoriginal on 2009-01-26
Have you tried this:
sudo adduser **your_user_name** admin

---

