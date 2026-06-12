---
title: "Icons (trivial)."
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Blåbär on 2009-02-15
Hey.

I have a pretty trivial question here... is there any way to set up so you're desktop-icons aren't gigantic? I'm currently on a 24" screen, and despite my high resolution I still get 1" icons for .pdf files, for example.

While we're at it. Any ideas of how to install .sh files? (tried to install something called "veetle" in order to stream on-line TV, but nothing seemed to recognize the format).

Thanks a bunch for listening.

/BB

---

### Post by namegame on 2009-02-15
For the icons, I'm not exactly sure. (I don't use icons :P) You could try using a different icon theme to see if that is your problem.

For the .sh files. You first need to make the file executable. You can do this in the command line with the following command:

```
 sudo chmod +x filename.sh
```

Then you can run the file from the command line with ./filename.sh

---

### Post by Blåbär on 2009-02-20
Thanks.

---

### Post by Bölvaður on 2009-02-20
> **namegame said:**
> 

```
 sudo chmod +x filename.sh
```

Then you can run the file from the command line with ./filename.sh

just because you have 4 posts and therefore perhaps not command line literate...sudo = run as super user (have all the permissions/is not needed if the file is located in your /home directory),  chmod = change the permissions of the file, +x = allow to be executable

this can also be done by right clicking the file &#8594; properties &#8594; check the "allow file to execute as a program"
and then double click it.


about the icons. you can right click &#8594; stretch icon
also this can be due to you zooming too much in nautilus.
(lets teach you something by going a strange way)

Alt+F2
Type: nautilus ~/Desktop
and hold down Ctrl and then press either - or use the scroll wheel to make the icons bigger/smaller.
(if you are an advanced user, this place is always empty, the desktop is only used for tasks you are currently doing before you move it to a proper place)

There can be a problem with icons if you installed one that is not very particularly well done. So you can just go to [http://www.gnome-look.org/]("http://www.gnome-look.org/") download desired icon theme.
System &#8594; Preferences &#8594; Appearance
have the theme tab open and drag the icon file you downloaded into there.
you can do the same for most themes.

enjoy

---

### Post by keithwwalker on 2009-02-21
Yes, but is there a way to sell a maximum desktop icon size by default?  Seems repetitive to stretch each icon...

---

