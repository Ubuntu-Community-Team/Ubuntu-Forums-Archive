---
title: "Need a system file 10.04"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by k33bz on 2011-07-09
Been trying to get my mic working with second life, although I got it working with removing pulseaudio and installing esound, then using this tutorial to get my hotkeys back for volume [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/400973/comments/11]("https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/400973/comments/11"). 

I have now abandoned all of this, I removed the two files that the tutorial above had me install, removed esound and reinstalled pulseaudio. However I am still getting the old glade volume hotkey graphics. I would like the ones back I had. I am thinking this is the file I need, if anyone on 10.04 gnome has the file I would appreciate it very much:

/usr/local/bin/gnome-sound-properties

Thanks

---

### Post by shiman6 on 2011-07-09
Have you tried to "sudo dpkg --reconfigure -a [package name]" it?

---

### Post by k33bz on 2011-07-09
> **shiman6 said:**
> Have you tried to "sudo dpkg --reconfigure -a [package name]" it?

Just tried that and I got this:
```
keebler@mobile:~$ sudo dpkg --reconfigure -a gnome-sound-properties
[sudo] password for keebler: 
dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
keebler@mobile:~$ 

```

---

### Post by k33bz on 2011-07-09
> **k33bz said:**
> Just tried that and I got this:
```
keebler@mobile:~$ sudo dpkg --reconfigure -a gnome-sound-properties
[sudo] password for keebler: 
dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
keebler@mobile:~$ 

```


Tried --configure instead of --reconfigure and that showed Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by shiman6 on 2011-07-09
> **k33bz said:**
> Just tried that and I got this:
```
keebler@mobile:~$ sudo dpkg --reconfigure -a gnome-sound-properties
[sudo] password for keebler: 
dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL)
[*].

Options marked
[*] produce a lot of output - pipe it through `less' or `more' !
keebler@mobile:~$ 

```

I did that all wrong. My bad. I re-read your post and noticed this wouldnt help you at all XD

Ill look into it to try to help.

---

### Post by k33bz on 2011-07-09
Anyone else want to take a stab at this?

To make it more clarified of what I am looking for. Right now I have a widget that pops up when I use my keyboard volume controls, looks like something that would go on a Mac. I think its ugly, my opinion anyway. What I had before was when I used the keyboard hotkeys the volume app on the panel would pop out under the panel, which was sleek, not like the bulky thing that pops out now in front of my screen on the bottom. I just want to get rid of that hideous widget.

Thanks

---

### Post by shiman6 on 2011-07-09
> **k33bz said:**
> Anyone else want to take a stab at this?

To make it more clarified of what I am looking for. Right now I have a widget that pops up when I use my keyboard volume controls, looks like something that would go on a Mac. I think its ugly, my opinion anyway. What I had before was when I used the keyboard hotkeys the volume app on the panel would pop out under the panel, which was sleek, not like the bulky thing that pops out now in front of my screen on the bottom. I just want to get rid of that hideous widget.

Thanks

You do know that the file you mentioned in your first post isnt a configuration file, but an executable?

---

### Post by shiman6 on 2011-07-09
> **k33bz said:**
> Anyone else want to take a stab at this?

To make it more clarified of what I am looking for. Right now I have a widget that pops up when I use my keyboard volume controls, looks like something that would go on a Mac. I think its ugly, my opinion anyway. What I had before was when I used the keyboard hotkeys the volume app on the panel would pop out under the panel, which was sleek, not like the bulky thing that pops out now in front of my screen on the bottom. I just want to get rid of that hideous widget.

Thanks
A shot in the dark, but does every notification pop up on the bottom? Because that could be a libnotify issue.

---

### Post by k33bz on 2011-07-09
> **shiman6 said:**
> You do know that the file you mentioned in your first post isnt a configuration file, but an executable?

Well I already deleted that file, along with the glade file that is in a different directory. I still have that hideous volume control widget. It is the one they had back from 9.04. I only placed those two files in my system, and they are gone now, even the zipped folder I got them from.

---

### Post by k33bz on 2011-07-09
> **shiman6 said:**
> A shot in the dark, but does every notification pop up on the bottom? Because that could be a libnotify issue.

Actually no, no other notification pops up down at the bottom, and all are still unified with compiz, emerald, and cairio dock, themes that I have enabled.

---

### Post by terrykiwi83 on 2011-07-09
couldn't you go into the package manager (Synaptic) and search for the package, remove it then re-install it?

---

### Post by k33bz on 2011-07-09
> **terrykiwi83 said:**
> couldn't you go into the package manager (Synaptic) and search for the package, remove it then re-install it?

It does not show up in Synaptic, and the other programs that are associated with I have already purged and reinstalled, still get same results.

---

### Post by k33bz on 2011-07-10
Bump

---

### Post by k33bz on 2011-07-12
I just fixed this by upgrading to 10.10.

---

