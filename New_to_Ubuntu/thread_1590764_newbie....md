---
title: "newbie..."
date: 2010-10-08
forum: New to Ubuntu
---

### Post by jjex22 on 2010-10-08
give in to the deb side...
Hi there,

I have been using Gentoo for, well years to be honest. Unfortunately Gentoo and I have filnally divorced due to irreconcilable differences, it used to be a case of spend days installing and building - then reep the rewards of a tailor made OS, but towards the end, either I'd gotten to old to be bothered maintaining her, or, as I strongly suspect she'd become an aweful lot more needy and moany.

Enter Ubuntu - when I first heard about Ubuntu a few years ago I had a quick play on it, but was at that time a RHEL3 or 4 customer and Ubuntu was young, (the other woman?) and then I didn't really hear much about it again until 2 or 3 years of years ago when it was everywhere, but I was happy in my marriage so stuck by Gentoo. 

Now just as I'm looking to ditch the old girl I hear that Ubuntu (that I had heard was a very heavy system, sorry but it's what people are saying) had a mini.iso that would install a base system and let you do the rest (hurrah!) and I've got to say after half a decade on the gentoo side, just setting up a base system in half an hour sold me to ubuntu!

just a quick couple of questions

1) I've found an online guide to help me with the apt side of things (having only used portage and yum before!) but I'm not having any luck finding out how you boot into the gui. I've found loads on how to boot into the non graphical side of things, I just can't seem to find out how you go the other way. ATM I'm loging in then running startx to get into xfce. Ive installed slim for the login so I'm ready to go, just need your help guys and girls!

2) Is there any way to choose what a package installs, I know there's no USE in ubuntu, just wondering if there's another way to cut options like gnome and kde support from packages?

Thankyou in advance and I look forward to solving many problems together!

J

---

### Post by andrewthomas on 2010-10-08
Do you have the xubuntu-desktop meta-package installed?

---

### Post by k33bz on 2010-10-08
Please dont make multiple post saying the EXACT same thing

[http://ubuntuforums.org/showthread.php?t=1590750]("http://ubuntuforums.org/showthread.php?t=1590750")

---

### Post by andrewthomas on 2010-10-08
> **jjex22 said:**
> 
2) Is there any way to choose what a package installs, I know there's no USE in ubuntu, just wondering if there's another way to cut options like gnome and kde support from packages?


J
Not short of compiling it yourself.  Although I thought this was why you didn't like Gentoo.

---

### Post by jjex22 on 2010-10-08
No, I still liked the portage system and USE was very useful (haha) but it just seemed like more and more updates were buggy and needed more work just to keep on top of things. I accept that this is part of Linux, but to my it seemed that some of the quality had gone.

Some how claws mail solved my problem - after I installed claws, and ran update again it now boots (slowly) into xfce!

---

### Post by The Cog on 2010-10-08
Installing xubuntu-desktop will pull in loads of packages. I know there's  a gnome-core package (and gdm for the login GUI). You could try looking for something like xfce-core I suppose. I tried xfce for the first time last week. I was very pleasantly surprised - I had heard it was lightweight and was expecting it to be feature light but it seemed to have pretty much everything I want - come the 10.10 release, I will probably try it again. I did notice that it used gdm as the login manager.

---

### Post by cek on 2010-10-08
Buggy updates are par for the course for a rolling release distro like gentoo.  Going to ubuntu will be quite a shock.  Not to steer you away, but have you considered trying Arch?  Arch is a rolling release distro very much like gentoo, but is not a source based distro.  The package manager pacman, will seem very familiar to a user of portage.

If you're like me however, eventually the allure of that fine grained control fades, and you just want to be up and running as fast as possible.

I moved off gentoo in about 2002, tried Arch for a while, then ubuntu, and just installed kubuntu 10.10 last week.

---

