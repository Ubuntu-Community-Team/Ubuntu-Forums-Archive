---
title: "How do I get &quot;Desktop Cube&quot; effect to work?"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by amsgwp on 2009-05-15
I installed CCSM and checked Desktop Cube and disabled Desktop Wall and when I hit ctrl+alt+arrows..nothing happens.  I've also tried enabling 3d rotation but still nothing.  

If I uncheck desktop cube and recheck desktop wall it works perfectly (desktop wall works perfectly, not cube).

I read somewhere to export my settings, reset to default, but that didn't work either.

---

### Post by lindsay7 on 2009-05-15
I am going by memory as I do not have Ubuntu on this computer, but when you go the the compiz settings you need to go to the general settings and set the horizontal setting to 4 for a cube.

Also, as I remember, you use ctrl+alt+left mouse button.  You can find a lot on how to set this up on you tube

---

### Post by bacardiandwatermelon on 2009-05-15
You need to add "rotate cube" not just "desktop cube"

---

### Post by Lunx on 2009-05-15
You also need to make sure you have **Extra** checked in** System --> Preferences --> Appearance --> Visual Effects**.

---

### Post by HairyIguana on 2009-05-15
I found that no matter which of these options used, none of the effects would work until I installed the proprietary driver for my graphics adaptor.
Try the following;

System > Administration >  Hardware Drivers

Then select the driver for your graphics card and click activate.
All you need do then is reboot the computer and you should be good to go.

---

### Post by amsgwp on 2009-05-19
Okay, thanks everyone.

The first response was my problem.  I needed 4 horizontal.  

I am still having an issue.  When I hit ctrl+alt+down it doesn't turn into a cube, it stays as a flat wall that I can zoom left and right, but it doesn't have the shape of a cube.  Any ideas?

I tried making a video of it but I can't figure out gtk-recordmydesktop.

But essentially the desktops are all in a flat row when I hit ctrl+alt+down.

---

### Post by amsgwp on 2009-05-19
Figured it out.  I'm retarded. Didn't realize that the desktop rotate had a different hotkey then the desktop cube.

---

