---
title: "installing wine ?"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by neil_1 on 2011-04-13
is installing wine on lucid recommended ?
if so 
all i have to do is add the ppa repository and then
sudo apt-get install wine ?

---

### Post by earthpigg on 2011-04-13
well, it wont break anything.

there is also no guarantee that it will make anything work either, as it is WINE.

so:

go for it, but keep your expectations low. 

lofty claims are often made about WINE. they don't always pan out. it isn't a magic yellow brick road, and no wizardry will make your Ubuntu system a perfect Windows sysem.

---

### Post by roger_1960 on 2011-04-13
Hi

You can install it straight from the Ubuntu software Center - this will configure it for you automatically (rather than having to run > wine config in terminal after installation.  It runs fine on Lucid but your experience depends on what you are trying to run in it!

---

### Post by Spyderkid on 2011-04-13
If the application is in the software centre just go for it! it can be easily removed if you don't want it afterwards

---

### Post by Karlchen on 2011-04-13
Hello, neil_1.

I would not recommend the Wine version which the official Canonical repositories offer to Lucid Lynx users. It is an old Wine v1.1.42, if I remember right. Personally I am running Wine v1.2.2 which I got from the WineHQ repository. (deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main)
Wine v1.3 is not a stable release, yet. So, use it at your own risk.
As stated before, in no case, expect Wine to provide a complete Windows environment.

Kind regards,
Karl

---

### Post by neil_1 on 2011-04-13
> **roger_1960 said:**
> depends on what you are trying to run in it!
utorrent and photoshop (:
> **Karlchen said:**
> Hello, neil_1.

I would not recommend the Wine version which the official Canonical repositories offer to Lucid Lynx users. It is an old Wine v1.1.42, if I remember right. Personally I am running Wine v1.2.2 which I got from the WineHQ repository. (deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main)
Wine v1.3 is not a stable release, yet. So, use it at your own risk.
As stated before, in no case, expect Wine to provide a complete Windows environment.

Kind regards,
Karl
i added the ppa repository to apt-get
what do i do after this ?

edit:
ubuntu rep shows wine1.2
[http://packages.ubuntu.com/lucid/wine](http://packages.ubuntu.com/lucid/wine)
so i would just apt-get install wine1.2 ?
or should i do it through the software manager?

---

### Post by roger_1960 on 2011-04-13
Hi

Look at this link:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=17](http://appdb.winehq.org/objectManager.php?sClass=application&iId=17)

and

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6824](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6824)

Looks like you may need the latest unstable version of wine......

In that case, follow the instructions on wineHQ for installation - I don't think its in the repos yet.

---

### Post by neil_1 on 2011-04-14
ok i installed wine1.2 nicely
how do i run a .exe in wine now ? :(
do i right click,open as wine ?

---

### Post by mastablasta on 2011-04-14
> **neil_1 said:**
> do i right click,open as wine ?
 
yes. try it ;-)
 
also you can do from terminal (e.g.)
 
wine setup.exe

---

### Post by computerandu on 2011-04-14
Follow this tutorial:

[http://computerandu.wordpress.com/2011/04/10/how-to-install-windows-application-exe-on-linux-ubuntu-with-wine/](http://computerandu.wordpress.com/2011/04/10/how-to-install-windows-application-exe-on-linux-ubuntu-with-wine/)

---

### Post by neil_1 on 2011-04-14
alright thanks guys :)

---

