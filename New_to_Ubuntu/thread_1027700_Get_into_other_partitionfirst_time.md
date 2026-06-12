---
title: "Get into other partition/first time"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by powell on 2009-01-01
Ok, a little back story first.  I have been using Windows since ~1995/1996 and have never used a different OS until today.  My XP has had 3 different hard drives, from registry error to consistent blue screens and pretty expensive software.  So I popped in the LiveCD in today just to see how it is, thought it looked great, and partitioned it to dual boot.  I have a few questions...

How to get to the WinXP partition?

Is installing/updating applications the same as in Windows?

Is there anything else I need to know about Linux?

Thanks guys

---

### Post by hyper_ch on 2009-01-01
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by freesitebuilder on 2009-01-01
This answers a lot of your questions:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

And this has just started, but hopefully will build up to a good resource:
[https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Education/Resources](https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Education/Resources)

---

### Post by tegnoto89 on 2009-01-01
If you partitioned it to dual boot, you should get a screen when you start your computer asking which OS to boot to.

No, to install programs in ubuntu, you can use the package manager (under system -> administration) and look up programs, and select them for installation.  For other programs you can use .DEB files which will add the program to the package manager (this way is doing it like windows).

Or you can open a terminal (for things in the repositories) and type:

sudo apt get-install (whatever you're installing here).  For example:

sudo apt-get install amarok


Hope that helps.

---

### Post by kestrel1 on 2009-01-01
Grub will normally set up the boot menu so that you can select your other OS (Windows)
Installing or updating apps is not really the same in Linux. With Ubuntu you can use the synaptic Package Manager to install applications that are held in the Ubuntu repositories or you can use a terminal & use apt or aptitude:
```
sudo apt-get install 'name of package'
```
To install other apps you may need to do a bit more work unless you can find a .deb file for the install.
I am sure everyone on the forum will help you in anyway that they can.
Welcome to the world of Linux, a better way to look at the world of computers.

---

### Post by powell on 2009-01-01
Hey thanks guys, I'm looking over the tutorials and wiki and other stuff youp osted.

---

