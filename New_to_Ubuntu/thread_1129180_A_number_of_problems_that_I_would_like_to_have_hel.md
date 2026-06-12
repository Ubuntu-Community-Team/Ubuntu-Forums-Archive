---
title: "A number of problems that I would like to have help with."
date: 2009-04-18
forum: New to Ubuntu
---

### Post by iamleaf on 2009-04-18
#1: I want to change the menu icon on my main panel. The Start icon. But Ubuntu doesn't let me replace the files from the Icon folder. (I'm using Tangerine icon theme) I understand that its supposed to have an svg extension and I have no idea how to edit the contents of an svg file. So I couldn't edit that one either. I've even tried using the configuration editor, that didn't work either.

#2: How do I use Emerald? I mean I import themes, I click on them. Nothing happens.

#3: I want to install an older version of WINE that will not crash IE. Which one should I install and how?

THANKS in advance >_<

---

### Post by cariboo on 2009-04-18
> #2: How do I use Emerald? I mean I import themes, I click on them. Nothing happens.

How are you importing themes? If you have a downloaded theme on your desktop, just right-click on the desktop and select Change Desktop background, then click the themes tab. Now just drag the downloaded theme to the theme window. Next select the theme for usage.

> #3: I want to install an older version of WINE that will not crash IE. Which one should I install and how?


IE crashes on Windows :) why do you expexct it not to in Wine. Have you tried [ie4linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page")?

Jim

---

### Post by hovzio on 2009-04-18
Are you running compiz?
If so give this a try after you have emerald set up;

```
emerald --replace &
```

This will start emerald (replace metacity with emerald..), this will not work after a reboot, you can manually add the command to System->Preferences->Sessions to have it "autostart" at boot :)

---

### Post by iamleaf on 2009-04-19
> **cariboo907 said:**
> 
IE crashes on Windows :) why do you expexct it not to in Wine. Have you tried [ie4linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page")?

No, I mean that when I use Winamp, the folder display doesn't come up, because it uses IE right (when I add media to library)? So it crashes. I want to install an older version that will not crash IE.... I heard that older versions support IE better.

And when I run the command --replace &, emerald only works when the terminal is still running...?

And any help with the start icon?

Thanks XD

---

### Post by pspsampsp on 2009-04-19
install compizconfig settings manager if you haven t all ready then in compiz config click effects and then under the effects tab find window decoration , where it says command replace /usr/bin/compiz-decorator or whatecer else it says with emerald --replace and click back. restart x and emerald should now work all the time.

---

### Post by me.translucent on 2009-04-19
wt i do is ..install conpiz config setting manager, install compiz fusion icon ...click on the icon ..it will appear in the upper panel click it ...select emrald theme manager .. and import the theme file .

---

### Post by northern lights on 2009-04-19
> **iamleaf said:**
> No, I mean that when I use Winamp, the folder display doesn't come up, because it uses IE right (when I add media to library)? So it crashes. I want to install an older version that will not crash IE.... I heard that older versions support IE better.

Why would rely on multiple Windows apps that have linux-native counterparts? I understand running an app in WINE that ncannot be replaced.

In your case however, amarok & firefox are more powerful than Winamp and IE. Why bother?

---

### Post by iamleaf on 2009-04-19
> **northern lights said:**
> Why would rely on multiple Windows apps that have linux-native counterparts? I understand running an app in WINE that ncannot be replaced.

In your case however, amarok & firefox are more powerful than Winamp and IE. Why bother?

Yeah, I suppose so. I just quit trying to install winamp. Only thing is I wish Ubuntu 8.04 would support Amarok 2. I'm using rhythymbox....

Well the emerald problem has been solved, thanks much!

Only prob is the start button now?
Anyone?

---

### Post by Linux&amp;Gsus on 2009-04-19
> **iamleaf said:**
> I have no idea how to edit the contents of an svg file.

*.svg files are vector graphic files. Inkscape would be the app for that.
In a terminal:
```
sudo apt-get install inkscape
```

Cheers,
L&G

---

### Post by northern lights on 2009-04-19
> **iamleaf said:**
> Only prob is the start button now?
Anyone?
The icon you're looking at is actually a .png, it's found under */usr/share/icons/THEME.NAME/PIXEL.SIZE/places/gnome-main-menu.png*. If you're using *Tangerine*, there's four different sizes of it:

/usr/share/icons/Tangerine/16x16/places/gnome-main-menu.png
/usr/share/icons/Tangerine/22x22/places/gnome-main-menu.png
/usr/share/icons/Tangerine/24x24/places/gnome-main-menu.png
/usr/share/icons/Tangerine/32x32/places/gnome-main-menu.png

---

### Post by JoshuaRL on 2009-04-19
> **iamleaf said:**
> Yeah, I suppose so. I just quit trying to install winamp. Only thing is I wish Ubuntu 8.04 would support Amarok 2. I'm using rhythymbox....


I think that if you liked WinAMP so much, you should try out Songbird.  Its open source, based on the mozilla engine, is themeable like WinAMP, and works great.  [Look here.](http://www.getdeb.net/app/Songbird)

---

### Post by iamleaf on 2009-04-19
Nah fuhgeddit. Songbird is quite screwy. :P Takes up my RAM I'm happy enough with rhythmbox, thanks for the tip though :)

---

