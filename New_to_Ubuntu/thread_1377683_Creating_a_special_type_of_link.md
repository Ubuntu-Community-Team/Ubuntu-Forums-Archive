---
title: "Creating a special type of link"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by bcoffield on 2010-01-10
Hi all,

Here's what I'm trying to do, and I know its possible because I did it on my old install but can't, despite trying a variety of things, figure it out again in my fresh install.  (Tangent:  Two thumbs up for doing a fresh install over upgrading...been upgrading the same installation for the past 4 or 5 releases and with a new hard drive did a fresh install.  Wow, just generally snappier and cleaner than my 9.10 upgrade.)

I have a program that is a .exe and when I run it, I right click on it and select "Open with Mono"  and everything is peachy.

How do I create a shortcut to this program so that it will open it with mono?  I want to create a shortcut to place in my taskbar so that one click and its open...  As it stands now I have a link to the folder and then have to right click, open with mono...

Thank you!

---

### Post by spiky001 on 2010-01-10
How about if you right click on desktop then create launcher?

---

### Post by bcoffield on 2010-01-10
Yes, I can create a launcher for it but when I double click on the newly created launcher nothing happens, because, it seems to me, that the attempt to open it is not being successfully routed through mono....

---

### Post by spiky001 on 2010-01-10
Can you not do it as you do in windows right click the exe move to panel only a guess tho out of my depth abit here just trying to help

---

### Post by Excedio on 2010-01-10
Try running the program with mono through the terminal. Then look to see what the correct command was that executed the program correctly.

---

### Post by bcoffield on 2010-01-10
@spiky -  I appreciate the thoughts.  I tried to make a link by right clicking on the exe and selecting create shortcut and then moved it to my desktop.  When i double clicked the shortcut nothing happened...

@excedio - in the terminal i changed to the directory where the .exe is located and then typed:  mono filename.exe

that worked...

I guess the question becomes, when I "create launcher" what exactly do i put in the command area.  mono filename.exe doesn't work... how do i write it to include the path?

---

