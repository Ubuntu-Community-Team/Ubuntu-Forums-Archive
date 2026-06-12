---
title: "Stuck at black screen, no desktop"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by dman535 on 2008-12-10
My machine has been running fine (dell d600) was playing around with some desktop apple themes and now my laptop hangs at the black screen with the white circle (black dots zipping around)I have tried a package restore from the recovery console and it doesn't look like its completing. Any suggestions on how to fix ?

Thanks

Derek.-
ubuntu-8.10-desktop-i386.iso

---

### Post by Michael.Godawski on 2008-12-10
> was playing around with some desktop apple themes
hey dman535, 
what exactly did you install? Have you tried to reconfigure the xserver?```

sudo dpkg-reconfigure xserver-xorg
```


[LIST]
[*][http://www.newlinuxuser.com/screen-resolution-got-all-funky-try-dpkg-reconfigure-xserver-xorg/](http://www.newlinuxuser.com/screen-resolution-got-all-funky-try-dpkg-reconfigure-xserver-xorg/)
[/LIST]

---

### Post by dman535 on 2008-12-10
The last things I changed were:
1. Installation of the AWN Stacks Applet
2. Tried to install Global Menu Applet

Here is a link to what I installed:
[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)

I still get the Ubuntu splash screen, get the screen flicker (which it did before) and then it just goes to a black screen with the white circle icon. Hard drive is not busy - so I am assuming its waiting for something or is locked up.

I reconfigured the xserver and it made no change.

D.-

---

### Post by mapes12 on 2008-12-10
Hello Derek

My desktop environment has screwed up a few times before but I have always been able to get it back with ```
sudo apt-get --reinstall install ubuntu-desktop

```
Mark

---

### Post by dman535 on 2008-12-10
I tried to reinstall the desktop.

I am getting unmet dependencies errors.

libgtk2.0-0 (>=2.14.1) but 2.12.9-4ubuntu3 is to be installed

I tried to do a package repair - but it seemed like the machine was having trouble resolving a bunch of URLS

---

### Post by Michael.Godawski on 2008-12-10
Can you please post your sources.list:

```
cat /etc/apt/sources.list
```

---

### Post by balloooza on 2008-12-10
Try booting up the computer and get to the GRUB screen by pressing escape when it tells you too at startup (grub loading stage 1.5 press esc to enter menu) 

When you see screen with a few choices choose the option with (recovery mode) by it. Wait a while, then when a screen comes up chose xfix (or somthing like that)

I hope this dose something, but it will not fix the package error.

---

### Post by balloooza on 2008-12-10
A little off topic, but if you still want an apple theme, you could try mac4lin v 1.0 (I use it) and get the latest repositorys for the awn dock (those are old)

---

### Post by balloooza on 2008-12-10
dman535, I belive your problem is with the mac menu, for a few reasons. One is that the installation of that applet requires you to use a different version of libgtk, and that version is outdated (assuming you are using 8.10, the latest release) this package is a big part of the gnome desktop and it cannot function without it. Can you boot into that recovery mode


> **balloooza said:**
> Try booting up the computer and get to the GRUB screen by pressing escape when it tells you too at startup (grub loading stage 1.5 press esc to enter menu) 

When you see screen with a few choices choose the option with (recovery mode) by it.

and when the screen loads up go to the shell and type 

```
apt-get install fluxbox
```

this will install a tiny desktop with limited features. But it will help you undo the changes you made to the gnome configuration (who wants to sit typing on a black screen where you don't have a mouse)

To use fluxbox finish the instalation in recovery mode and then type 

```
init 3
```
this gives you yet another blinking line, but with a login. Login to your favorite account (note the password will not do anything when you type, but it is still working) when you log on use this to start fluxbox
```
fluxbox
```

but you should see a blank desktop with a mouse and a bar at the bottom. Here you can reverse the process by undoing whatever you did with the website you were following.

You can use the fluxbox right click menu to open up firefox and synaptic package manager, and undo all the changes you made.

I hope this helps you figure it out, and you will mostlikly be able to use your laptop while you are still figuring out the problem. But the first place to start would be to "reverse engineer" the guide that got you into this problem.

---

### Post by dman535 on 2008-12-10
I am getting that same error when I try to install fluxbox.

I think one element I was missing - was setting up the network adapter before I tried to update ubuntu. So I did a manual configuration of the network adapter - did a sudo get-updates -f - it updated all the packages and booted up 

Thanks to all for the help !

---

