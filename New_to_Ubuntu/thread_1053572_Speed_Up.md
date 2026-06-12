---
title: "Speed Up"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by DeadRobot on 2009-01-28
Are there any tricks or ways to speed up Ubuntu in general?

---

### Post by kaibob on 2009-01-28
Have a look at the following:

[http://www.polishubuntu.piczo.com/optimizeubuntu8.04forspeed/?cr=2](http://www.polishubuntu.piczo.com/optimizeubuntu8.04forspeed/?cr=2)

Be sure to have a good backup before starting.

---

### Post by RichardLinx on 2009-01-28
Yes. Just do a google search for "Speed up Ubuntu" and you'll be presented with links to multiple guides. 
[http://www.google.com.au/search?q=Speed+Up+Ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com.au/search?q=Speed+Up+Ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)
The first thing I do after installing Ubuntu and getting a few necessary packages I go through a process of deleting a lot of things I don't use. (eg. Games). After deleting all unwanted packages I run the autoremove and autoclean commands.

```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```

If you don't mind changeing which DE you use then you could switch to something lighter like xfce. There are also guides to speed up the boot process.
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

EDIT: If you use compiz you could always set it to use minimum effects or customize it to your liking so that It puts less demand on your hardware.

---

