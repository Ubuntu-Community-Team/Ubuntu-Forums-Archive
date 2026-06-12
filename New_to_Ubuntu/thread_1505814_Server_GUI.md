---
title: "Server GUI"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by Failboat88 on 2010-06-09
Is it possible to boot into a gnome desktop then log in later with no gui after you got everything configured?

---

### Post by davidmohammed on 2010-06-09
probably - educated guess that you might like to try.

install server

then login

install the gui via 

sudo apt-get install ubuntu-desktop

reboot

to remove the desktop

reboot into recovery mode and drop to a terminal shell

sudo apt-get remove ubuntu-desktop

reboot.

---

### Post by Darkness Des on 2010-06-09
Close. I'm not sure how to answer the question, but I know that what you're doing will not work. ubuntu-desktop is a small package with a LOT of dependencies (you'll know what I'm talking about if you've ever installed a different desktop environment). I suggest using Aptitude, it handles dependencies well and can removed orphaned packages.

---

### Post by crispy_420 on 2010-06-09
Maybe a different/lighter gui since this will be temporary so FluxBox or the like. But you will also need a login manager to select session type (eg. gdm).

But no matter how you look at it you will be installing lots of packages that will need to be later removed.

Edit: you could always remove just the login manager (gdm, kdm, etc.) you went with to stop others from seeing that there is a gui.

---

### Post by bodhi.zazen on 2010-06-09
> **Failboat88 said:**
> Is it possible to boot into a gnome desktop then log in later with no gui after you got everything configured?

Yes it is possible, but it does not help much.

configuring a server is primarily editing config files, so it does not matter much if you are using vim, nano, or gedit.

If you want a graphical interface, look at webmin, or similar.

[http://woodel.com/](http://woodel.com/)

---

### Post by SRST Technologies on 2010-06-09
It's pretty easy to install gnome-desktop, then edit inittab to not boot into graphical by default.  Then instead of uninstalling gnome after doing all the configuration the easy way, you just reboot the server when you're done editing with the proper inittab entry in place so that the GUI does not automatically start up.  In this method, if you need to edit in the future and can't do it from the command line you don't have to continually install and uninstall Gnome.  Just use startx.

---

### Post by KdotJ on 2010-06-09
I agree with bodhi.zazen, it really doesn't help much. It is simple to edit the config files via the shell and vim helps with colour highlighting. 
In my opinion, it will be good practise to set up and configure stuff just using the shell, as well as moving around the file system and learning commands. Just my 2 pence...

---

### Post by drdos2006 on 2010-06-09
Check this out before you do anything. I found it very, very useful.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by A_M_S on 2010-06-09
Webmin is an excellent tool for local and remote configuration of Ubuntu Server

---

### Post by SRST Technologies on 2010-06-10
I am strongly suggesting AGAINST using webmin as it is no longer in the repositories and would not be updated as needed when a new version comes out.

---

### Post by bodhi.zazen on 2010-06-10
> **SRST Technologies said:**
> I am strongly suggesting AGAINST using webmin as it is no longer in the repositories and would not be updated as needed when a new version comes out.

I would have to disagree with that advice, it sounds as if you are not familiar with webmin. The webmin project has both .deb and a repository available:

[http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

> Supported Debian-based Distributions  

Webmin has been tested on all regular Debian releases, Ubuntu Linux,  and derivatives like Xandros and APLINUX.Repo:


> If you like to install and update Webmin via APT, edit the /etc/apt/sources.list  file on your system and add the line : 

deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib  

You should also fetch and install my GPG key with which the repository  is signed, with the commands :

 cd /root
wget [http://www.webmin.com/jcameron-key.asc](http://www.webmin.com/jcameron-key.asc)
apt-key add jcameron-key.asc   You will now be able to install with the commands : apt-get update
apt-get install webminYou will have to run those last commands as root (sudo)

Webmin is far more functional on a server then gnome (or any X Desktop).

See : [http://www.webmin.com/demo.html](http://www.webmin.com/demo.html)

Gnome/KDE/XFCE/Fluxbox/etc do not have graphical tools to perform server tasks.

---

### Post by Failboat88 on 2010-06-11
Thanks for the advice. I think webmin looks like it will work for me. I'm plotting making a home file server that won't be used as a desktop.

---

