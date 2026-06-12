---
title: "System Restore for Ubuntu 9.04?"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by Zavie A. on 2009-05-19
So, I screwed up Ubuntu on my computer a bit :( 

In a poor attempt to update my video drivers I edited some of the things in the "/etc/X11/xorg.conf" menu and now GNOME won't let me log on to my account. I will sign in, it will begin to log in and then just set me right back on the login screen.

XFCE will however...but only for a few minutes then it kicks me off.

So I was wondering if there was any way to do some sort of system restore, like there is in Windows, which will allow me to set back all my settings without having to reinstall. 

Thanks in advance. :)

---

### Post by Sef on 2009-05-19
Did you back up your xorg before editing?

---

### Post by Zavie A. on 2009-05-19
unfortunately no :(

but I remember what I changed and how It looked before I changed it.

---

### Post by nimajiman on 2009-05-19
Hi there,

Did you back up your /etc/X11/xorg.conf file before editing it? Always a good idea. If so you should be able to restore the old file.

Haven't done anything like this for ages but going from my memory you could try this. 

If you can get to the Ubuntu login screen when you turn on the computer, before you try and log in, press [Ctrl] + [Alt] + [F1]. You will get a console screen. Type your usual username and password, and it will log you in to a basic command line.

If you are not sure whether you have any backups of xorg.conf, type

```
cd /etc/X11
```

then

```
ls
```

See if there are any xorg.conf.XXXXX files (e.g. xorg.conf.backup or xorg.conf.failsafe) or anything else that looks like an older version of xorg.conf.

If there is, type:

```
sudo mv /etc/X11/xorg.conf.XXXXX /etc/X11/xorg.conf
```

(replace xorg.conf.XXXXX filename with whatever is appropriate)

Basically you are just replacing your current xorg.conf with an older one that *hopefully* is working. Try restarting (type 'restart' at the console) and see if you have any luck!

Of course if you don't have a backup of that file then you will need to try something else, so let us know.

To my knowledge there isn't a 'system restore' feature in Ubuntu as of yet, although there are some backup programs that might do a similar job. I haven't tried any of these though.

Good luck!

---

### Post by nimajiman on 2009-05-19
Ah sorry didn't see previous posts.

---

