---
title: "GIMP wont load"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by NewbyA1 on 2009-09-27
Absolute newbie to Ubuntu 9.04 and loving it. After using it a few times it will not start up past the login. When trying to log in in safe mode with graphics it says that it is unable to find GIMP. I can log in in terminal but from there have no idea how to fix the problem. Can someone please help me.
 
Machine is AMD 1400Mz processor
500Mb RAM
Dual Boot with WindowsXP and Ubuntu
Ubuntu boots off primary drive
 
Many Thanks

---

### Post by ajgreeny on 2009-09-27
It sounds as if there is a problem with gimp, but why that should stop you booting to a full gnome desktop, I can't imagine.  Anyway it could be worth trying to either install or reinstall gimp, and see if that gives you any more success.

From your terminal login run ```
sudo apt-get install --reinstall gimp
```

---

### Post by gali98 on 2009-09-27
Have you been messing with your xorg.conf?
Messing up Gimp shouldn't mess with your graphics configuration.
Did you recently try to enable restricted drivers or use Envy-ng?
Kory

---

### Post by NewbyA1 on 2009-09-27
Thanks I will try that.

---

### Post by NewbyA1 on 2009-09-27
I have not made any changes. Frankly I dont know how to make any changes. Thanks for trying to help me anyway.

---

### Post by sandyd on 2009-09-27
[http://ubuntuforums.org/showthread.php?t=120742](http://ubuntuforums.org/showthread.php?t=120742)
seeif playing with your BIOS settings help.

---

### Post by NewbyA1 on 2009-09-28
Still no joy. I get to the login, enter my user name and password and then the screen goes black except for the arrow pointer. The mouse works at this point but nothing else loads as normal. If I select the option to load the terminal window it loads, but if I select to load the graphics in safe mode it tells me that it cannot find Gimp? Now I know Gimp is a program for photos and images so I don't know why it won't load if it cannot find Gimp?
 
Any other ideas I might try?

---

### Post by sandyd on 2009-09-28
perhaps the dialog says gimp without the "i"?

---

