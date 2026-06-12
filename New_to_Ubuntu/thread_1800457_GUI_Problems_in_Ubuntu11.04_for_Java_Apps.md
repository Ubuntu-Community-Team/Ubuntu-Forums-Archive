---
title: "GUI Problems in Ubuntu11.04 for Java Apps"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by sabyasachi087 on 2011-07-09
Hii All, am quiet new to ubuntu and linux.  Few days back i installed Oracle XE and Oracle JDeveloper. I managed to install and its working fine. But whenever i start any java app,either JDeveloper or SQL Developer,all the menu bar got invisible and all application starts without any border there after unless i restart the box.  I dont Know is it a stability issue with this new distro or my faulty installation.Can any one help??

---

### Post by wildmanne39 on 2011-07-09
> **sabyasachi087 said:**
> Hii All, am quiet new to ubuntu and linux.  Few days back i installed Oracle XE and Oracle JDeveloper. I managed to install and its working fine. But whenever i start any java app,either JDeveloper or SQL Developer,all the menu bar got invisible and all application starts without any border there after unless i restart the box.  I dont Know is it a stability issue with this new distro or my faulty installation.Can any one help??
Hi, did you install these through software center? What are your system specs? Are you running natty and have you changed any setting in compiz?

---

### Post by vhogemann on 2011-12-06
Got this from another post,

It seems to be some kind of issue around XOrg and SQL/J Developer... The only solution was to use another XServer on top of XOrg.

Install Xephyr (or XNest) and a light WM, such as icewm:

[INDENT]sudo apt-get install xserver-xephyr icewm
[/INDENT]
Edit the jdev startup script ( <YOUR_MID_HOME>/jdeveloper/jdev/bin/jdev ) and add these lines:

[INDENT]Xephyr :2 -ac -screen 1024x768 &
icewm --display :2 &
export DISPLAY=:2[/INDENT]

---

### Post by beew on 2011-12-06
It is a bug because of the global menu.

[https://bugs.eclipse.org/bugs/show_bug.cgi?id=330563](https://bugs.eclipse.org/bugs/show_bug.cgi?id=330563)

A simple solution is to get rid of the global menu
```

sudo apt-get remove indicator-appmenu
```There is another work around here, just change aptana to whatever it is for your apps(it is the same problem)

[http://blog.lukebennett.com/2011/07/05/menu-issue-with-aptana-studio-3-on-ubuntu-11-0/](http://blog.lukebennett.com/2011/07/05/menu-issue-with-aptana-studio-3-on-ubuntu-11-0/)

---

