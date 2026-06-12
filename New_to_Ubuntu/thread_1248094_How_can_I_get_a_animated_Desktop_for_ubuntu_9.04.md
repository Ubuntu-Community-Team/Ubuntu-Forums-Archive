---
title: "How can I get a animated Desktop for ubuntu 9.04"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by Seankn on 2009-08-23
Hello I'm new to the forums...

I'm trying to get some program that you can put a video as a background. 

I really prefer a .DEB file so I don't have to do compiling...( I hate it) 

Or if there is no .Deb file please give me a link for really good step by step directions.

Thanks :)Seankn:)

---

### Post by pedro3005 on 2009-08-23
Try
[http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/](http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/)

---

### Post by loomsen on 2009-08-23
Shantz provides xwinwrap...

[http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap](http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap)

---

### Post by Seankn on 2009-08-23
The Deb file was not found

---

### Post by Seankn on 2009-08-23
Well i have installed this software and i can not get it to work :(

---

### Post by shantzg001 on 2009-08-24
Hey Seankn. Could you please list what you did to run it and what exactly was the issue you faced?

---

### Post by cataztrophe on 2009-08-24
@pedro and loomsen
thnx for your share dude!

---

### Post by Seankn on 2009-08-24
Ok First I went to [http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap](http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap) then downloaded it, Saved it to my desktop. Then i double clicked the file then installed the x86_64. 

Then really i have no idea what do next... And i did not understand the directions

---

### Post by sandyd on 2009-08-24
> **Seankn said:**
> Ok First I went to [http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap](http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap) then downloaded it, Saved it to my desktop. Then i double clicked the file then installed the x86_64. 

Then really i have no idea what do next... And i did not understand the directions

these commands are to be used in the terminal
```

xwinwrap [-g {w}x{h}+{x}+{y}] [-ni] [-argb] [-fs] [-s] [-st] [-sp] [-a] [-b] [-nf] [-o OPACITY] [-sh SHAPE] [-ov] -- COMMAND ARG1...
Options:
-g    - Specify Geometry (w=width, h=height, x=x-coord, y=y-coord. ex: -g 640x480+100+100)
-ni   - Ignore Input
-d - Desktop Window Hack. Provide name of the "Desktop" window as parameter
-argb - RGB
-fs   - Full Screen
-s    - Sticky
-st   - Skip Taskbar
-sp   - Skip Pager
-a    - Above
-b    - Below
-nf   - No Focus
-o    - Opacity value between 0 to 1 (ex: -o 0.20)
-sh   - Shape of window (choose between rectangle, circle or triangle. Default is rectangle)
-ov   - Set override_redirect flag (For seamless desktop background integration)
-debug - Enable Debug messages
```

for example
```
xwinwrap -ov -fs -- /usr/lib/xscreensaver/glmatrix -root -window-id WID
```

---

### Post by Seankn on 2009-08-24
Thanks!!! Ill try it when i get home...

---

### Post by Seankn on 2009-08-24
Ok I got it to work but i have no icons and i cant right click on the Desktop is this suppost to happen?

---

### Post by sandyd on 2009-08-25
its normal
you see, it replaces your entire desktop. which means no right click, icons, or any other operation on the desktop

---

### Post by coldReactive on 2009-08-25
> **carlee said:**
> its normal
you see, it replaces your entire desktop. which means no right click, icons, or any other operation on the desktop

So how do you get them to integrate into the animated desktop?

If you can't, why use it?

---

### Post by shafin on 2009-09-28
See this:
[http://www.gnome-look.org/content/show.php/Animated+Desktop+%28GUI%29%28EN%26ES%29?content=88248](http://www.gnome-look.org/content/show.php/Animated+Desktop+%28GUI%29%28EN%26ES%29?content=88248)

---

