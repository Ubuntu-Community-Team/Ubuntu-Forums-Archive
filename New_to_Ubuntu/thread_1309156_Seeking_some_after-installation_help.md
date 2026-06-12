---
title: "Seeking some after-installation help"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Sacred Flame on 2009-11-01
Hey guys, this is my first time on these forums and first Linux (and Ubuntu, for that matter) experience.

I managed to install everything pretty smoothly - I'm running Ubuntu 9.10 Karmic Koala on a Dell Studio XPS 13, dual-booted with Windows Vista. All my hardware works - wireless, graphics card - but I just have two questions that I need help with. 

1) What applications or software are recommended to be installed, other than the defaults? 
2) I tried applying a theme from dA, but I can't get it right. From my understanding, I need a .tar.gz, then drag it into the Theme Manager. The theme I tried to apply ([http://fratrip.deviantart.com/art/Gaia-Neue-Suite-100383098](http://fratrip.deviantart.com/art/Gaia-Neue-Suite-100383098)) is a .zip. I did get the emerald portion down, but there's no changes. Can anyone help out? I've done the whole move to the /.themes folder thing as well, and that failed. If anyone can help out, that'd be great.

Thanks in advance! :KS

---

### Post by ovroniil on 2009-11-01
[LIST]
[*]For additional multimedia support, install [restricted-extras]("https://help.ubuntu.com/community/RestrictedFormats") and [medibuntu]("https://help.ubuntu.com/community/Medibuntu").
[*]To watch flash videos install **Adobe flash player**.
[*]Also you can use [Ubuntu Tweak]("http://ubuntu-tweak.com/").
[*]And of course **Compiz**.
[/LIST]

---

### Post by ikisham on 2009-11-01
For the first item some people will say that you could install ubuntu-restricted-extras which are non-free software and include codecs, flash, java and maybe something else (if you want to know exactly what comes with it open the terminal and type apt-cache show ubuntu-restricted-extras).
The problem is that it install big things like java which you may not want.
If you want only Flash player then, in the terminal:
```
sudo apt-get install flashplugin-nonfree
```
And you don't need to worry about the codecs because when Totem (movie player) or Rythmbox (audio player) don't have a proper codec to play a file (like mp3) they will ask automatically if you want to install it.

*Add* - For extra software that you may like, open the Software Center and enjoy!

*AddII* - compiz is actually already installed but you need it's settings manager to tweak with it (it will show up under System>Preferences):
```
sudo apt-get install compizconfig-settings-manager
```
For the themes, you may like to have a look at gnome-look.org too.

---

### Post by Darce on 2009-11-01
What applications / software were you using under windows ?

---

### Post by davidryderuk on 2009-11-01
> For the themes, you may like to have a look at gnome-look.org too.


I second [www.gnome-look.org](www.gnome-look.org).

> The theme I tried to apply ([http://fratrip.deviantart.com/art/Ga...uite-100383098](http://fratrip.deviantart.com/art/Ga...uite-100383098)) is a .zip. I did get the emerald portion down, but there's no changes. Can anyone help out? I've done the whole move to the /.themes folder thing as well, and that failed. If anyone can help out, that'd be great.

The easiest way of getting that theme to work is:

1. Extract the folder "/Gaia Neue/Gtk/Gaia Neue" in your zip file.

2. Right click on the folder (Gaia Neue) and select compress from the menu.

3. In the window that comes up click on the create button. 

4. You should now have your tar.gz file, which can be dragged into the theme manager.

Edit: As a general rule compress anything you find inside a "Gtk" folder, if it hasn't already been done.

---

### Post by ovroniil on 2009-11-01
Some sources for Ubuntu software:

[LIST=1]
[*][All my apps]("http://allmyapps.com/")
[*][Get deb]("http://www.getdeb.net/")
[*][Source Forge]("http://sourceforge.net/softwaremap/")
[*][Linux software equivalent to Windows software]("http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software")
[/LIST]

---

