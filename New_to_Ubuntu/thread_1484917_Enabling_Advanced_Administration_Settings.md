---
title: "Enabling Advanced Administration Settings"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by cvp on 2010-05-16
I feel retarded having to ask this, but Google has not been helpful.

The [Ubuntu Guide](http://ubuntuguide.org/wiki/Ubuntu:Lucid) makes frequent mention of some **System > Administration > Advanced** menu, but I don't have an "Advanced" entry.
Surprisingly, Ubuntu Tweaks wasn't helpful for this, either.

This all started when I became interested in changing my default login theme. My **System > Administration > Login Screen** gives me a very simple dialog box that will only let me change whether it plays a sound, whether to log on automatically, and what my default session is, whereas this mythical **System > Administration > *Advanced* > Login Manager** gives options about themes, among a whole lot else more.

How do I enable access to this "Advanced" Administration wonderland?

Thanks.
-cvp

---

### Post by warfacegod on 2010-05-16
I'm guessing you are running either 9.10 or 10.04. There is no Advanced tab in the Login Screen in either. The guide is referring to GDM 2.20 and GDM 2.28 is now in use instead.

You'll want this: [http://ubuntuforums.org/showthread.php?t=1358026](http://ubuntuforums.org/showthread.php?t=1358026)

---

### Post by cvp on 2010-05-16
Awesome.

Okay, next question:
Now that I'm looking at this...
[img]http://img94.imageshack.us/img94/9506/loginsettings.png[/img]
...how do I change the theme to something I found on [art.gnome.org/themes](http://art.gnome.org/themes)?

I've downloaded the tarball of the theme, which contains images for the background and miscellaneous doodads, as well as an **XML** file and a **.desktop** file. I saw somewhere someone trying to install themes by putting them in ~/.themes, but that doesn't seem to affect the menu choices.

I appreciate your help so far.

Thanks,
-cvp

---

### Post by Excedio on 2010-05-16
> **cvp said:**
> Awesome.
 
Okay, next question:
Now that I'm looking at this...
[IMG]http://img94.imageshack.us/img94/9506/loginsettings.png[/IMG]
...how do I change the theme to something I found on [art.gnome.org/themes]("http://art.gnome.org/themes")?
 
I've downloaded the tarball of the theme, which contains images for the background and miscellaneous doodads, as well as an **XML** file and a **.desktop** file. I saw somewhere someone trying to install themes by putting them in ~/.themes, but that doesn't seem to affect the menu choices.
 
I appreciate your help so far.
 
Thanks,
-cvp
 
System > Preferences > Appearance
 
When that opens, go to the Themes tab. Drag & Drop the tarball on top of the Appearance window.

---

### Post by warfacegod on 2010-05-16
Some themes come as .deb, those you can double click.

---

### Post by cvp on 2010-05-16
> **Excedio said:**
> System > Preferences > Appearance
 
When that opens, go to the Themes tab. Drag & Drop the tarball on top of the Appearance window.
It keeps telling me that they're not valid themes. I've tried this with multiple themes, all from [art.gnome.org/themes](http://art.gnome.org/themes).
I've tried dragging the tarballs (the **.tar.gz** files -- just so you know that I know what a tarball is), the extracted directories, the XML files in the extracted directories... to no avail.

---

### Post by warfacegod on 2010-05-17
Unpack them and manually place them in usr/share/themes. You'll need to be root to move them there.

---

### Post by 3rdalbum on 2010-05-17
> **cvp said:**
> It keeps telling me that they're not valid themes. 

You can't use GDM (login window) themes anymore. And you could never drop them onto the Appearance window anyway because the Appearnce window is for GTK (controls), Metacity (windows) and icon themes.

With the GDM login window you can specify a "wallpaper" and a GTK theme to use. You'll need to extract the GTK theme into /usr/share/themes.

---

