---
title: "Getting different Desktop Environments"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by zer010 on 2009-08-30
I'm trying to be able to choose between "DE"s at login. I found something for it once while googlin' around, but can't seem to find it again.  I'm runnin' an Ubuntu Jaunty install, so I'm runnin' GNOME.  How do I get to install and switch between GNOME and Xubutnu, or KDE at login.  As per my sig, I'm looking more for Xubuntu GUI(Xfce?) Any help is Greatly appreciated!  Thanks!  :)

---

### Post by pedro3005 on 2009-08-30
Run at terminal:
'sudo apt-get install kubuntu-desktop' for KDE
'sudo apt-get install xubuntu-desktop' for XFCE
'sudo apt-get install fluxbox' - personal recommendation

---

### Post by wojox on 2009-08-30
Then logout, login choose options > sessions and pick a DE.

---

### Post by zvacet on 2009-08-31
[Here]("http://psychocats.s465.sureserver.com/ubuntu/xfce")

---

### Post by zer010 on 2009-08-31
Well, all that is helpful, but now I'm curious about trying other DE's.  Although I know my choises are quite limited, due to the limits of my pc.  I'm sure that Compiz is out of the question.  Now I'm also curious as to what DE's others use.  So what do you use and why? Screencaptures welcome!

---

### Post by earthpigg on 2009-08-31
> **zer010 said:**
> I'm sure that Compiz is out of the question.  Now I'm also curious as to what DE's others use.  So what do you use and why? Screencaptures welcome!

compiz most certainly is **_not_** out of the question! compiz is just another Window Manager that runs under a DE.

in any desktop environment, run this command to get compiz up and running:

```
compiz --replace
```

to turn it back off, you will need to know what window manager you where previously using. for example, gnome uses metacity as the WM:

```
metacity --replace
```

im a fan of LXDE. very lightweight (makes xfce4 look horribly bloated), doesn't use a lot of hard drive space, and easy to use.

```
openbox --replace
```

would be how to re-enable lxde's WM after playing with compiz in lxde.

---

### Post by halitech on 2009-08-31
> **zer010 said:**
> Well, all that is helpful, but now I'm curious about trying other DE's.  Although I know my choises are quite limited, due to the limits of my pc.  I'm sure that Compiz is out of the question.  Now I'm also curious as to what DE's others use.  So what do you use and why? Screencaptures welcome!

compiz is more reliant on a decent video card capable of doing good 3d graphics with a driver that works as well. The Radeon 7500 is a decent card but the ATI drivers are not so good if you are using 9.04. Might work better if you were running 8.04 instead of 9.04.

Personally I use a customized Debian Lenny install with XFCE and selected apps based on what I do with my desktop. Don't see the point in having things installed that I don't use. My laptop is built on the same base with apps I need on there. I'm currently thinking of putting LXDE on it to see if there are any differences in speed.

---

### Post by matsuzine on 2009-08-31
I really like jwm.  You have to do some configuring to get menus, but it runs snappy.

I have full ubuntu 9.04 + jwm on 10-yo computer that barely used to run xp, and it boots / loads apps in seconds.

---

### Post by CatKiller on 2009-08-31
It's all about LXDE, man :)

---

### Post by pedro3005 on 2009-08-31
GNOME can be good too:
[http://img188.imageshack.us/img188/7118/screenshotvqs.png](http://img188.imageshack.us/img188/7118/screenshotvqs.png)

---

### Post by zer010 on 2009-09-01
Well, I tried fluxbox a little, and... it's interesting.  However it said I needed emacs to get a wallpaper?  Well, I did get my GNOME wallpaper by switching to Nautilus.  After that, I couldn't get back to the flux navigator.  I'm sure it takes some getting used to.  For right now I'll stick with GNOME.  So what's the remove command to wipe out fluxbox?  Something like : sudo auto-remove fluxbox ?

---

### Post by pedro3005 on 2009-09-01
```

sudo apt-get purge fluxbox

```

---

### Post by zer010 on 2009-09-01
> **pedro3005 said:**
> ```

sudo apt-get purge fluxbox

```

Thanks! Perhaps I'll try it again sometime.

---

