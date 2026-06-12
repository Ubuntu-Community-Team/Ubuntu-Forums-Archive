---
title: "Some Questions On Making ubuntu attractive?"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-05-19
1.Can i have different wallpaper on different sides of desktop
2.i have a wallpaper on the top of the desktop cube ,how to add a wallpaper to its bottom
3.is there any other software other than compiz to customize ubuntu ,(i tried compiz fussion too but it starts compiz only)
4.I will ask when i get a doubt :p

---

### Post by Crandom on 2009-05-19
Compiz Settings Manager is a good start - it will allow you to edit all the compiz fusion effects. Get it by typing this into a terminal window:
```
sudo apt-get install compizconfig-settings-manager
```

This will allow you to put different "Cube Caps" onto the cube by editing the options in the plugin called "Cube Caps".

[http://gnome-look.org/](http://gnome-look.org/) provides hundreds of themes/login windows/everything else that you would want to customize your gnome desktop with.

The current theme engine is metacity, you can install "Emerald Theme Manager" to make use of other themes that use the "Oxygen", "Murrine" and other types of theme engines.

Wallpapers on separate workspaces has been promised for a long time but it hasn't (at least to my knowledge) been implemented yet (there is a Brainstorm Idea on [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/) that I can't find anymore).

gnome-color-chooser allows you to change the colors of your gnome desktop. You can add and remove gnome panels so you can only have one at the bottom/top or two at the side (or 30 from the top if you want) by right clicking on any current gnome-panel.

startupmanager allows you to edit the bootscreen (managed by a program called usplash), and you can all colours and pictures to grub by using gfxboot.

If you want any details of how to make any of these work just reply or just google there names (perhaps on [http://www.google.com/linux](http://www.google.com/linux) ?). There are hundreds more things you can do, this is just a short introduction.

---

### Post by rogueleader12345 on 2009-06-15
You can also add new GUI's to Ubuntu like KDE, XFCE, and choose which one you want to load when you log in. To do KDE, you need to go to Synaptic and search kde-desktop. Mark it for installation and apply. Then, restart, and at your login window, click Sessions, and choose KDE! It makes it easy if you like GNOME and KDE both, but don't want to install Ubuntu and Kubuntu both.

---

### Post by SoftwareExplorer on 2009-06-15
You can have different wallpapers on different sides of the cube with compiz, but there is a tradeoff: you can't see the files on your desktop if you're using gnome.

---

### Post by SoftwareExplorer on 2009-06-15
By the way, if you are interested, I will go and research/try to remember how I did it. It was something with gconf and turning of the desktop in gnome.

---

### Post by PukingPenguin on 2009-06-15
Making ubuntu attractive?

Try doing ```
sudo apt-get me_a_beer
```

at least twelve times. 


That should make ANYTHING attractive...


:popcorn:

---

### Post by QIII on 2009-06-15
Including your wife...

Budda bump...ching!

---

### Post by raymondh on 2009-06-15
> **SoftwareExplorer said:**
> By the way, if you are interested, I will go and research/try to remember how I did it. It was something with gconf and turning of the desktop in gnome.

Disable nautilus

---

### Post by PukingPenguin on 2009-06-15
> **QIII said:**
> Including your wife...

Budda bump...ching!

Tell me...
What did you THINK I was talking about?!

YOUR wife?!

:D

---

### Post by H2SO_four on 2009-06-15
> **QIII said:**
> Including your wife...

Budda bump...ching!

+1 demerit point! lol :)

---

### Post by SoftwareExplorer on 2009-06-15
> **raymondhenson said:**
> Disable nautilus

Here's how I did it:

```
Alt + F2
```
then
    ```
gconf-editor

```
Browse to apps > nautilus > preferences > show_desktop and unselect it.

---

