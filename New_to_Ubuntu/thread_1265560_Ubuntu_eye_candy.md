---
title: "Ubuntu eye candy"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by silent463 on 2009-09-13
ok im new to ubuntu and i need help i wanna make my desktop UNIQUE i want something kind of like this 


[http://www.youtube.com/watch?v=kYgV2GlsufI&feature=PlayList&p=6129D193DE38AD24&index=4](http://www.youtube.com/watch?v=kYgV2GlsufI&feature=PlayList&p=6129D193DE38AD24&index=4)

this right here is what im wanting to do but as i said i am new to linux/ubuntu and i know VERY VERY LIITTLE so i would really be thankful for someone to show me how to do this if you send me a site message ill give you my info for msn/hotmail / Y! Messanger

---

### Post by Temposs on 2009-09-13
First you want to install the Custom Compiz Settings Manager, so open Applications->Add/Remove, and search for "ccsm". Install that program, and then it should be something you can open from System->Preferences. You can mess around with all the flashy effects that are available in Ubuntu from there.

Also, you can go to System->Preferences->Appearance and mess around with the themes. You can download new themes from the internet like at [www.gnome-look.org](www.gnome-look.org)

When you download a theme, save it to the desktop, then drag it into the Themes section of the Appearances application. If the theme is valid, it should automatically bring in the theme. If that doesn't work, you can also try saving the theme to ~/.themes

EDIT: In [www.gnome-look.org](www.gnome-look.org), the sections you want to look at initially are the GTK themes and the Metacity themes. Try out the other kinds of themes as you get more comfortable.

---

### Post by K7522 on 2009-09-13
Hello, and welcome to the Ubuntu community! I'll try to help you out as simply as possible.

The first thing you'll want to do is go to System > Preferences > Appearances, click on the Visual Effects tab and click Extra.

That should enable a few fun things, like wobbly windows.

Your next step will be to install the GUI for managing all the fun looks; you may do this by running the below code in Terminal.
```
sudo aptitude install compizconfig-settings-manager
```

You can then go to System > Preferences > CompizConfig Settings Manager.
Once in there you'll want to add a couple desktops, so open General Options, select the Desktop Size tab and give yourself a couple, I use 10.

Click Back in the bottom left, and click Desktop Cube, enable it on the left side and set up your behaviour, appearance and transparencies.

Skydome in Appearance is the backdrop, not your desktop background.

I set my Opacity During Rotation to 40, and When Not Rotating to 80

Cube Reflection and Deformation is your next step. You'll want to set Cube Caps to transparent and remove the default images. Set Deformation to None so it stays a cube.

There are many other options in there to play with. 

As for the Matrix look that is a screensaver that is layered over your desktop with xwinwrap.

The details for xwinwrap and an active wallpaper are detailed here:
[http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap](http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap)

It's best to set a black desktop paper when you do this! It also has the code for doing the matrix wallpaper there.

Hollar if you have any questions.

---

### Post by CatKiller on 2009-09-13
> **silent463 said:**
> ok im new to ubuntu and i need help i wanna make my desktop UNIQUE i want something kind of like this 

Surely that's a contradiction in terms?

Anyway, that video's pretty old.

Beryl's obsolete these days. It re-merged with Compiz to form Compiz-Fusion, which is installed by default. Most of the things that Beryl could do you can do with CCSM, as has already been described (but not having the panel static on the screen while everything else was transformed, which is a shame). That provides most of what's in that video; the cube, the skydome, the burn animation.

The icons on the right are kiba-dock, but that also isn't in active development at the moment. People have moved on to other docks, like Avant Window Navigator.

Drawing a screensaver on the desktop is pretty straightforward.

All of these have been discussed (at length) on these forums. You'll find out how to do it if you look.

---

### Post by jerrrys on 2009-09-13
here's a place to start

[http://www.google.com/search?q=how+to+custom+themes+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=how+to+custom+themes+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by steveneddy on 2009-09-13
This thread will answer all of your questions.

If not cruise the links in my sig.

[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by silent463 on 2009-09-13
well im new to this lol and its like everytime i enable something i dont see results to that action such as wabbly windows

---

### Post by Sealbhach on 2009-09-13
Have you enabled your graphics hardware driver? Look in System/Administration/Hardware Drivers and see if it's enabled.

.

---

### Post by K7522 on 2009-09-13
> **silent463 said:**
> well im new to this lol and its like everytime i enable something i dont see results to that action such as wabbly windows

I tried to be pretty descriptive in my directions in post #3, however after installing compizconfig-settings-manager if you are not seeing the changes you may not have the video drivers properly enabled, what video card do you have? You may have to go to System > Administration > Hardware Drivers and enable a restricted driver there.

---

### Post by silent463 on 2009-09-13
yes my video card is installed and such it waws working lastnight but nowe it's not working right

---

### Post by keplerspeed on 2009-09-13
To get the screensaver as the wallpaper, use xwinwrap. See my tut here: [http://www.keplerspeed.comuv.com/xwinwrap.html](http://www.keplerspeed.comuv.com/xwinwrap.html)

---

### Post by shaunsmith_99 on 2009-09-23
BUMP! I think this is a great thread for new Ubuntu Folks (like myself) and hope others folks can learn a thing or two like I did! Thanks!

---

