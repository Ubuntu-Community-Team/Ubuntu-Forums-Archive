---
title: "Kubuntu won't let go"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by abooks on 2009-11-14
I'm trying to remove a faulty kubuntu and install a new Ubuntu, but I keep getting this:

A display manager is a program that provides graphical login
capabilities for the X window system
Only one display manager can manage a given X server, but multiple
display managers are installed.
Please select which display manager should run by default. 

It has a little OK at the bottom, but it doesn't work. I'm guessing I need to go into Konsole and fix something manually, but what, where and how?

---

### Post by ajgreeny on 2009-11-14
I'm not quite sure what you mean, but if you want to move from kubuntu to ubuntu, having installed kubuntu first, you can simply use the following commands
```
sudo apt-get install ubuntu-desktop
apt-get remove kubuntu-desktop
apt-get autoremove
```The first will obviously install everything needed for a standard ubuntu with gnome desktop, the second will remove the metapackage kubuntu-desktop, and the third will then remove all the dependencies of kubuntu-desktop, leaving you with a pure gnome setup.

---

### Post by abooks on 2009-11-14
I thought there must be a vestige of Kubuntu left. I ran install ubuntu, and remove Kubuntu, but not autoremove. I went in to package mgr and tired to zap all the OTHER kubuntu stuff, but I got the same error ms I'm getting try to run autoremove:

~$ sudo apt-get autoremove
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I'm tellin' ya, this is the OS that wouldn't die! Is an Undead OS worse than The Dark OS?

---

### Post by bacardiandwatermelon on 2009-11-14
You could try booting into recovery mode and then use the netroot, and try it again :-)

---

### Post by alienclone on 2009-11-14
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by ajgreeny on 2009-11-15
> ~$ sudo apt-get autoremove
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
This suggests that synaptic or something was open when you tried the teminal command.  Only one application or utility can use apt or dpkg at any time, so shut synaptic and try again, or see the link from alienclone, and try that.

---

### Post by sandyd on 2009-11-15
> **abooks said:**
> I'm trying to remove a faulty kubuntu and install a new Ubuntu, but I keep getting this:

A display manager is a program that provides graphical login
capabilities for the X window system
Only one display manager can manage a given X server, but multiple
display managers are installed.
Please select which display manager should run by default. 

It has a little OK at the bottom, but it doesn't work. I'm guessing I need to go into Konsole and fix something manually, but what, where and how?
tab key might be some help.
wonder why everybody just can't figure it out.........

---

### Post by kio_http on 2009-11-15
Try

```
sudo killall xorg
```

---

### Post by abooks on 2009-11-18
Originally Posted by abooks  View Post
I'm trying to remove a faulty kubuntu and install a new Ubuntu, but I keep getting this:

A display manager is a program that provides graphical login
capabilities for the X window system
Only one display manager can manage a given X server, but multiple
display managers are installed.
Please select which display manager should run by default.

It has a little OK at the bottom, but it doesn't work. I'm guessing I need to go into Konsole and fix something manually, but what, where and how?
tab key might be some help.
wonder why everybody just can't figure it out.........

Carlee gets the Prize: I am now Kubuntu free!

NOTE TO HER AND OTHER SERIOUS GEEKS: Remember, this is "absolute Beginner" forum. . .we're like two year-olds: we say "NO!" a lot, we can walk, sometimes even run, but we crash a lot.
__________________

---

