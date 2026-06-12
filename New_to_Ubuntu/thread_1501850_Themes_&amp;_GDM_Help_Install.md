---
title: "Themes &amp; GDM Help Install"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by greyfox82092 on 2010-06-04
Well, let me first say I like Ubuntu, I'm running the 10.04 ver., and it has been better then Windows Vista.

My only concern is that I have been trying to get several of the themes & GDM Logins to work, but to no avail. The two that I want the most are these:

[http://gnome-look.org/content/show.php/ArchDark?content=94030](http://gnome-look.org/content/show.php/ArchDark?content=94030) - GDM Login

And quite a few of the GTK 2.x themes. If these aren't supposed to be the proper themes, could someone redirect me?:)

I've loved Ubuntu so far, but I came in here off of a WindowBlinds high, and was looking to customize this a little more to my liking.

Please help me!](*,)

---

### Post by greyfox82092 on 2010-06-04
Please help. I have tried searching Google & here on the forums. I'm only familiar with Windows, and I am willing to learn how to do this. Please, I'm begging.:(

---

### Post by wojox on 2010-06-04
You can't changes the GDM in 10.04. You would have to uninstall some packages and install some older one's. 

I think I remember seeing a link some where to do this. Let me see if I can find it.

---

### Post by wojox on 2010-06-04
If you want to mess with this configuration try this in a terminal:

```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

---

### Post by towheedm on 2010-06-04
GDM cannot be themed anymore.  But it is highly customizable.  Check out the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

Hope this helps.

---

### Post by greyfox82092 on 2010-06-04
Aw...Rats.

So I'd have to downgrade to 9.x? It doesn't matter that much, though. Thank you for the help guys!

Tried the code, didn't work.

---

