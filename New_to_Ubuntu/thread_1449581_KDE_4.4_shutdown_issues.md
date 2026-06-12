---
title: "KDE 4.4 shutdown issues"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by vivek40 on 2010-04-08
Hii! went about installing KDE 4.4 on my ubuntu 9.10 yesterday. Everything went perfect.. and it got installed but the problem is unique I dont have any shutdown icon/button. All I have is logout, sleep,hibernate,lock,switch user.can someone help please!


(How i installed KDE4.4---1.added the repository-
deb http:[COLOR=#000000]**//**[/COLOR]ppa.launchpad.net[COLOR=#000000]**/**[/COLOR]kubuntu-ppa[COLOR=#000000]**/**[/COLOR]backports[COLOR=#000000]**/**[/COLOR]ubuntu karmic main
2.enabled unsuported updates for karmic backport
3.sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install kubuntu-desktop)

Thanks
Vivek

---

### Post by Mykk on 2010-04-08
> **vivek40 said:**
> Hii! went about installing KDE 4.4 on my ubuntu 9.10 yesterday. Everything went perfect.. and it got installed but the problem is unique I dont have any shutdown icon/button. All I have is logout, sleep,hibernate,lock,switch user.can someone help please!


(How i installed KDE4.4---1.added the repository-
deb http:[COLOR=#000000]**//**[/COLOR]ppa.launchpad.net[COLOR=#000000]**/**[/COLOR]kubuntu-ppa[COLOR=#000000]**/**[/COLOR]backports[COLOR=#000000]**/**[/COLOR]ubuntu karmic main
2.enabled unsuported updates for karmic backport
3.sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install kubuntu-desktop)

Thanks
Vivek

I had the same problem when i was messing about with mine, i cant remember exactly how i managed to solve the issue though. It was something like changing GDM to KDM in a menu within the terminal. There is a code you can use to do it - ill try and dig it out for you. I should have it written on one of the many millions of post it notes scattered around my desk at work haha!

*EDIT*

Thats a bit of luck, i found the post it note - try this:

sudo dpkg-reconfigure kdm 

From there you can change your default display manager.

Hope this helps.

---

### Post by vivek40 on 2010-04-09
Thanks Mykk!!!

---

### Post by Mykk on 2010-04-09
> **vivek40 said:**
> Thanks Mykk!!!

No problem :)

---

### Post by bunty on 2010-11-21
thanks for sharing that trick, but this is only a work around really. 

Why can't I use the DM of my choice , and what the hell has the DM got to do with whether or not there there is a shutdown option on the kde "leave" menu ?

Whatever the DM I still need to be able to shutdown the computer and the one thing that won't be needed for shutdown is a DM , it's irrelevant. 

:?

---

