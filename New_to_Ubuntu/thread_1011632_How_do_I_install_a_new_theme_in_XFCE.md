---
title: "How do I install a new theme in XFCE?"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by doctorbighands on 2008-12-15
I'm trying to install Mac4Lin, but I'm an Xubuntu noob. In Gnome, it's a simple drag-and-drop, but not so (apparently) in XFCE. How do I do it? I've downloaded the tar.gz file to the Desktop, and that's as far as I've come.

Thank you!

---

### Post by Sorivenul on 2008-12-15
Manually in Terminal:
```
sudo cp name_of_theme.tar.gz /usr/share/themes && cd /usr/share/themes && sudo tar -xvf name_of_theme.tar.gz
```

You could always do it graphically using Thunar as root:
```
gksudo thunar
```
Then move the archive to /usr/share/themes and extract.

---

### Post by doctorbighands on 2008-12-15
I did it using the terminal, and it seemed to do everything correctly. However, when I go to User Interface Preferences, the theme doesn't show up in the list.

---

### Post by Sorivenul on 2008-12-15
Link to the theme you downloaded?
It's possible the theme wasn't packaged for direct extraction and some moving may have to be done.  If there is a folder inside the folder you extracted with a name matching the theme, copy that folder into /usr/share/themes and check if the theme is available then.

---

### Post by doctorbighands on 2008-12-15
Here is the download page where I got Mac4Lin:

[http://sourceforge.net/project/showfiles.php?group_id=204373&package_id=243878&release_id=625515](http://sourceforge.net/project/showfiles.php?group_id=204373&package_id=243878&release_id=625515)

---

### Post by Jack Harkness on 2008-12-15
Also check your folder and file permissions on the theme you installed.  I had that happen back when I was using XFCE and I finally figured out that the theme permissions were set to "None".  Check one of the themes you have that works, then check the permissions on your new one and set them to match if they don't already.

---

### Post by doctorbighands on 2008-12-15
Okay, I'm getting somewhere: I successfully managed to install the GTK theme and activate it. Now, I need to install the Emerald theme for the title bars and the icon theme. I have no idea how to do either of those!

---

### Post by doctorbighands on 2008-12-15
I figured out the title bars...now if I could just get the icons right...

---

### Post by Sorivenul on 2008-12-15
Icons will go in /usr/share/icons in their respective theme subfolder.

---

### Post by mudrain911 on 2008-12-23
Do you have emerald installed? By default Xubuntu uses Xfwm...

---

