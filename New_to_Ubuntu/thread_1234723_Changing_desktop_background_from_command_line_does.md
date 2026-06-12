---
title: "Changing desktop background from command line doesn't work"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by Sapfeer on 2009-08-08
Hello!

I'm using Ubuntu 9.04 and I'm trying to change desktop background from command line, but it doesn't working...
```
[ lenovo-y510ka@user Sat 08 Aug 2009 02:00:50 PM MSD ]
/home/user $ sudo gconftool-2 -t string -s /desktop/gnome/background/picture_filename "/home/user/walls/jaunty-sunset.jpg" 

[ lenovo-y510ka@user Sat 08 Aug 2009 02:00:53 PM MSD ]
/home/user $ gconftool-2 -a /desktop/gnome/background
 picture-filename = /home/user/walls/jaunty-sunset.jpg
 draw_background = true
 picture_options = zoom
 color_shading_type = solid
 picture_opacity = 100
 picture_filename = /home/user/walls/desktopography/2008/Wheathump-1280x960.jpg
 primary_color = #68684b4b3333
 secondary_color = #68684b4b3333

```
What is the difference between picture-filename and picture_filename properties?.. Why gconftool-2 doesn't set correct values?..

---

### Post by CatKiller on 2009-08-08
Don't use sudo.

You might also need to switch the "set" and "type" entries in your command. Using ```
gconftool-2 -s -t string /desktop/gnome/background/picture_filename "/path/to/image"
``` just worked fine for me.

---

### Post by starcannon on 2009-08-08
Doh CatKiller beat me to it.

This command worked for me:
```

gconftool-2 -t string -s /desktop/gnome/background/picture_filename "/home/starcannon/Pictures/sample.jpg"

```There are likely some flags you can throw to cause scaling, background color choice, etc... but thats the basic command right there; note, there is no need for sudo.

GL

---

### Post by Sapfeer on 2009-08-08
Thanks all! Without sudo it works fine... But still, the difference between picture-filename and picture_filename is unclear for me...

cheers

---

### Post by Liolikas on 2009-08-08
Just different file names.

---

### Post by CatKiller on 2009-08-08
Given that the picture-filename entry probably didn't exist until you created it, I don't know what to tell you.

---

### Post by starcannon on 2009-08-08
> **Sapfeer said:**
> Thanks all! Without sudo it works fine... But still, the difference between picture-filename and picture_filename is unclear for me...

cheers

A dash - is just an entirely different character than an underscore _ , it's the same as the difference between an A and an Z, they are just different, they have different [ascii codes]("http://www.cs.utk.edu/%7Epham/ascii_table.jpg") and everything.

---

