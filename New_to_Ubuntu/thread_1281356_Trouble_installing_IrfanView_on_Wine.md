---
title: "Trouble installing IrfanView on Wine"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by Rumtscho on 2009-10-03
I want to run IrfanView from Wine, but it doesn't work so far. Tried following this tutorial: [http://www.wine-reviews.net/wine-reviews/wine/irfanview-423-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/wine/irfanview-423-on-linux-with-wine.html), but it doesn't work. IrfanView itself installed smoothly, but when I try to run it from the Start Menu in Wine, nothing happens, I only see a busy cursor for about a second. So I thought I'd try the /one option described in the tutorial. But I can't navigate to the .exe from the command line. I can get into /home/rumi/.wine/drive_c/, but from there I don't know how to change into Program files, and I guess that just renaming this folder would be a bad idea. The tutorial says you can go there with a backslash, like ```
cd /home/rumi/.wine/drive_c/Program\ Files/IrfanView
```, but it doesn't work, I get a "No such file or directory" error. The good old Dos trick of PROGRA~1 doesn't work either. 

So is there a way to go into that directory from the shell? Or a way to run the .exe with the /one switch from the GUI File Browser? Or do you know a better solution for running IrfanView?

---

### Post by Rumtscho on 2009-10-03
All right, just by looking at my own post I saw that I need a whitespace after the backslash - those people should change the font in their tutorial :) Now I got it running, but have a new problem. I don't want to type that every time when I want to open a picture. Is there a way to modify the IrfanView entry in the Applications menu so it starts with the /one switch from there?

---

### Post by diablo75 on 2009-10-03
From what I can see on IrfanView's website... this appears to be some kind of image viewer/editor...  You might try a free ("free" as in "freedom" and not "free" as in "free beer") open-source alternative for this, like Gimp (for editing), and the included image viewer (I don't know what it's called but I just double-click on any picture and it opens up for me).

---

### Post by Jerry N on 2009-10-03
I tried IrfanView with Wine and Crossover and my experience was that it didn't work well at all.  XnView (very similar to IrFanView) works fairly well under Crossover (and probably with Wine) except that manipulating the file tree is a bit clumsy.  There is an old Linux version of Xnview but it is basically worthless.  The new Xnview MP (MultiPlatform) alpha works, somewhat, but it's a long way from being ready for "prime time".  

BTW, GIMP does not provide the capabilities that Xnview and Irfanview provide.  There does not seem to be a Linux equivalent.

Jerry

---

