---
title: "Restoring Previous Settings"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by Kyler2 on 2008-12-21
I was playing around with the resolution settings for my computer screen, and when I went to return to the original settings, it doesn't look identical to how it was before, and that is throwing me off.

Is there a way to restore my computer to say the previous day's settings? Or am I going to have to get used to this change?

Thanks.

---

### Post by Tatty on 2008-12-21
did you back up your xorg.conf file before you started messing?  If so then simply replace the current xorg.conf with the backup.

If not then you could reset your graphics to their default state using:
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by IamReck on 2008-12-21
If you made back ups from the previous day there would be, just check in /etc/X11 to see if there are any backups.  Filename would be along the lines of xorg.conf.2008<month><day><time(24 hour clock).

What is different from the way it was before?

---

### Post by Kyler2 on 2008-12-21
The major difference is just the shapes of the windows and also it seems that the entire system is running a bit slower than before.  One example is instead of the nice volume screen that fades in and out when adjusting the volume, it is much more blocky and appears and disappears.  I am a complete beginner to Ubuntu, so if I would have had to make the conscious decision to create a back-up file, I probably didn't.

---

### Post by Tatty on 2008-12-21
> **Kyler2 said:**
> The major difference is just the shapes of the windows and also it seems that the entire system is running a bit slower than before.  One example is instead of the nice volume screen that fades in and out when adjusting the volume, it is much more blocky and appears and disappears.  I am a complete beginner to Ubuntu, so if I would have had to make the conscious decision to create a back-up file, I probably didn't.

Thats the first thing a new linux user tends to learn, always back up what you are about to mess with ;)

Try reconfiguring xorg with the command in my last post.

---

### Post by IamReck on 2008-12-21
Sounds like you have a different theme.  Don't know what to do about the system being slower.

Right click on your Desktop, click Change Desktop Background, and go to the Themes tab, and select the one that looks like the one you want.

---

### Post by Kyler2 on 2008-12-21
Thanks Tatty!  The command worked, I really appreciate everyone's help.  That was a great way to learn the lesson to back everything up, without having done any serious damage.

Kyler.

---

