---
title: "LXDE minimal system but with network manager and nm-applet"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by keithpeter on 2009-05-08
Hello All

I like the LXDE window manager. I used it along with a XUBUNTU install on an old P3 laptop, and I'm using it now on my Asus P1 barebones box.

Some people install an Ubuntu server or Ubuntu CLI system and then add Xorg and the minimum bits they need. I'd like to try this approach BUT I need to have the full network manager functionality available (automatic recognition of wired, wireless and mobile phone network modems) and an 'applet' that allows me to switch wifi networks and to use the mobile phone modem when plugged in.

What do I need to install? What kind of desktop manager will allow nm-applet to work? Is the network manager part of a base install?

Pointers to explanations of linux networking for idiots welcome.

---

### Post by keithpeter on 2009-05-10
Hello

**Bump and New Question**: network-manager-gnome pulls down 130Mb of stuff (CUPS and so on). Can you dismantle this large package and install just the stack that is needed to get the nm-applet and the network manager working? If so, how do you find out which packages are needed?

**What I tried (Asus 701)**

I found that using the Ubuntu minimal installer iso and installing as far as a command line system and then

```
 sudo apt-get install xorg xterm gdm lxde menu firefox network-manager-gnome flashplugin-nonfree
 sudo /etc/init.d/gdm start
```

gets me the basic lxde desktop with leafpad &c and Firefox with flash, and the network manager installed. 

Using the procedure at

[http://ubuntuforums.org/showthread.php?p=7210414#post7210414](http://ubuntuforums.org/showthread.php?p=7210414#post7210414)

gets the nm-applet (the panel entry that lets you change from wifi to G3 modem to wired connection) autostarting when you start the system.

The whole installation plus abiword and notecase takes 1.18 Mb by the way.

---

### Post by keithpeter on 2009-05-13
Hello All

I'm bumping this one more time.

Is it possible to 'unbundle' the network-manager-gnome package so that only the Internet relevant stuff is installed?

I love Ubuntu 9.04's ability to 'just work' with a modem, a wifi card and wired connection using this system.

PS The minimal system above was 1.18Gb of course.

Cheers

---

### Post by billgoldberg on 2009-05-13
> **keithpeter said:**
> Hello All

I like the LXDE window manager. I used it along with a XUBUNTU install on an old P3 laptop, and I'm using it now on my Asus P1 barebones box.

Some people install an Ubuntu server or Ubuntu CLI system and then add Xorg and the minimum bits they need. I'd like to try this approach BUT I need to have the full network manager functionality available (automatic recognition of wired, wireless and mobile phone network modems) and an 'applet' that allows me to switch wifi networks and to use the mobile phone modem when plugged in.

What do I need to install? What kind of desktop manager will allow nm-applet to work? Is the network manager part of a base install?

Pointers to explanations of linux networking for idiots welcome.

Networking will work without having any kind of graphical enviroment installed.

It's been a while but I'm pretty certain these are the commands;

```
ifconfig eth0 up
```

```
dhclient eth0
```

Use ifconfig to see if it's eth0 or something else.

NM-applet is made for "gnome-panel".

You can try WICD instead of Network-Manager to have a graphical way of connecting to your networks. (wicd-client is the graphical front end).

---

### Post by kerry_s on 2009-05-13
i agree you should try wicd instead.

start with:

**sudo apt-get install xorg gdm lxde wicd synaptic**

that is enough to get you into gui, then you can use synaptic to add what ever else you want.

---

### Post by gn2 on 2009-05-13
Is Wicd in the Ubuntu repos now, or do you still have to add the Wicd repo to sources.list?

---

### Post by imdano on 2009-05-13
It's in the Jaunty repos, yes.

---

### Post by gn2 on 2009-05-14
Cool, not before time :)

---

### Post by keithpeter on 2009-05-15
> **billgoldberg said:**
> 

You can try WICD instead of Network-Manager to have a graphical way of connecting to your networks. (wicd-client is the graphical front end).

I'll try that one and see what happens. Thanks all.

---

### Post by kerry_s on 2009-05-15
you could always just do it manually or use a script.
i use a script for mine, so i don't have the overhead of a network manager.

---

### Post by Artemis3 on 2009-05-15
> **kerry_s said:**
> i agree you should try wicd instead.

start with:

**sudo apt-get install xorg gdm lxde wicd synaptic**

that is enough to get you into gui, then you can use synaptic to add what ever else you want.

Try slim instead of gdm... You should avoid large gnome libraries and maybe take some hints from xubuntu. There are more lightweight alternatives such as epdfview, midori, abiword/gnumeric, openbox you could use for your light distro.

---

### Post by keithpeter on 2009-05-16
> **Artemis3 said:**
> Try slim instead of gdm... You should avoid large gnome libraries and maybe take some hints from xubuntu. 

**Edited**: I tried Ubuntu Minimal with CLI on some unused space on my desktop, then

```
sudo apt-get install xorg xterm slim lxde firefox flashplugin-nonfree

```

gdm got installed anyway as I was asked which window manager I wanted to use. I suppose it comes as part of LXDE?

I'm using Firefox now with two windows open and free is showing about 130Mb in use. I'll try the Debian Lenny net install next, unless it stops raining :-)

**Edited**: could not get Lenny netinstall + xorg xdm and fluxbox to pick up the nvidia card at all. All attempts to get nv working at proper resolution failed and the nvidia package would not compile. Similar story with Jaunty minimal + xdm/fluxbox. What is there extra in LXDE?

---

### Post by Ozitraveller on 2009-11-05
I found this :

sudo aptitude install --without-recommends lxde

here:
[http://wiki.dennyhalim.com/ubuntu-minimal-desktop#toc13](http://wiki.dennyhalim.com/ubuntu-minimal-desktop#toc13)

I haven't tried it so don't know whether it works.

---

