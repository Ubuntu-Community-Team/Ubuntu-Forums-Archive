---
title: "flash in konqueror"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by nike007 on 2008-12-11
hey how do i get flash to work in konqueror, i downloaded the .deb package from adobe and installed it using gdeb thing. i then scanned for plugins, it finds the flash plugin but i dont know what to do after that.

videos in youtube just show a black screen, btw it works in firefox but imo firefox sucks so 

thanks 
nike007

---

### Post by nike007 on 2008-12-11
guys please help me .. ive tried all i can .. nothing makes it work ..

---

### Post by Cool G5 on 2008-12-11
Maybe [this]("http://freebsd.kde.org/howtos/konqueror-flash.php") can help.

Good luck :)

---

### Post by gimcrack on 2008-12-11
Any time I need fast help I google it. 

KeyWord: konqueror flash

[http://freebsd.kde.org/howtos/konqueror-flash.php](http://freebsd.kde.org/howtos/konqueror-flash.php)

If I can't find my answer at google then I move to a forum.

So I google for you your answer is in the link above.

Installing Flash

Since the Flash Player from Macromedia is only distributed in binary form and only for Linux, we need to install a wrapper to make it accessible for Konqueror. Install nspluginwrapper and the actual Flash Player linux-flashplugin7 from ports:

cd /usr/ports/www/nspluginwrapper && make install clean
cd /usr/ports/www/linux-flashplugin7 && make install clean

Setting up nspluginwrapper

Run

nspluginwrapper -v -a -i

This command lets nspluginwrapper search for installed plugins and generate wrapper libraries in ~/.mozilla/plugins. These wrapper libraries will also be visible to and usable by native FreeBSD builds of Firefox, Mozilla and Seamonkey.
Setting up Konqueror

In order for Konqueror to find the plugin for the Flash Player, you might have to add an additional search-path to the plugins-section of Konqueror's settings.

    * Open Konqueror.
    * In the Konqueror menubar, traverse the submenus until you arrive at:
      Settings -> Configure Konqueror -> Plugins
    * Proceed to the Scan tab.
    * Select the Scan for New Plugins button.

Plugins are now searched and if everything worked well, you should see an entry for the Flash-plugin when you switch to the Plugins tab.
Successful detection of the flash-plugin

The installation is finished and you can check if everything works at the Adobe Flash Website.

---

### Post by nike007 on 2008-12-11
ok so i had done all that before and even konqueror detects the plugins as flash but somehow flash content on adobe's site or youtube doesnt play still

thanks
nike007

---

### Post by waspbr on 2008-12-11
erased
apparently you already said it works in firefox

look out below

---

### Post by gjoellee on 2008-12-11
> **waspbr said:**
> does flash work in firefox?
yeah it is just to download the deb or add this command:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by nike007 on 2008-12-11
its finally working .. guess i'd just had to reboot aftre konqueror detected it

thanks guys
nike007

---

### Post by nike007 on 2008-12-11
funny .. it stopped working again

---

### Post by nike007 on 2008-12-12
any help

---

