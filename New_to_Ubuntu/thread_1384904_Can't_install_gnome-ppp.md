---
title: "Can't install gnome-ppp"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by K-Bar on 2010-01-18
[SIZE=2]After getting wvdial to work and an ISP that is not philosophicaly opposed to my using Linux, I gather the next step is to run gnome-ppp. When I try do do that I get a message saying package is not installed, you can install is with sudo apt-get install gnome-ppp. When I try to do that I get a message saying package not found. I then tried to install it with a full path to where it is: sudo apt-get install /usr/share/apt-install/desktop/gnome-ppp and get the same message.[/SIZE]
 
[SIZE=2]What is going on here?[/SIZE]

---

### Post by alwayshere on 2010-01-19
[http://packages.ubuntu.com/hardy/i386/gnome-ppp/download]("http://packages.ubuntu.com/hardy/i386/gnome-ppp/download")

[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html]("http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html")

If you still have trouble to install it mybe your software sources settings need to be set better eg: In drop box "download for main server" and tick the first 4 boxs there

then run 

 sudo apt-get update

then to install gnome ppp

sudo apt-get install gnome ppp 

then to starti it 

gnome ppp

---

### Post by Bartender on 2010-01-19
K-Bar -
You gotta be online to get it.  Can you get online with pppconfig or with wvdial?  You may have to go into Synaptic and "Reload" all the package data before you can get gnome-ppp.

sudo apt-get update is the same thing as having Synaptic Reload.

BTW, I'm not an expert at the command line but I don't think that longer command you typed in is appropriate.  Linux knows where to install gnome-ppp.  The problem in your case appears to be that it can't make contact with the servers.

---

### Post by Silvertones on 2010-01-19
Get on line and use the synaptic package mgr.

---

### Post by K-Bar on 2010-01-19
> **Bartender said:**
>  You may have to go into Synaptic and "Reload" all the package data before you can get gnome-ppp. 
Thanks, that did it. I now launch gnome-ppp from my desktop.
 
The last step is to upgrade my modem driver.  I am currently using the free verson of hfsmodems which has limited download speed.  Once I install the full verson everything should be peachy.

---

### Post by _duncan_ on 2010-01-20
A word of caution about purchasing the full version.

Modem drivers are kernel-specific. The version you're buying may or may not work with newer kernels. It is normal for a specific Ubuntu version to have 2 or more kernel upgrades within the 6-month period before a new Ubuntu version comes out (which will have yet another kernel).

Better check with linuxant if what you are paying for covers upgrades to newer kernels in the future. Otherwise, you may end up having to pay them again.

---

### Post by K-Bar on 2010-01-24
Thanks for the warning Duncan.  I did upgrade to the full version (internet works much better now) and in the confirmation e-mail I received it said I was licensed for such and such a version or later,so it sounds like that does include free upgrades.

---

