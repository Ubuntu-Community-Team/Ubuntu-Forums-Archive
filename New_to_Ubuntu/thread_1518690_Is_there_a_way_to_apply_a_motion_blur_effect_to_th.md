---
title: "Is there a way to apply a motion blur effect to the mouse cursor?"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by diablo75 on 2010-06-27
I was just watching a tutorial video for some music software I used in Windows and they were running the demo off of a Mac.  One of the neat things I'm noticed about this Mac was that when the user moved their mouse cursor real fast across the screen the cursor actually motion-blurs.  I found a website that does a fantastic flash-based demonstration of what this looks like.  Check this link out and in their little mouse settings box, check off Motion Blur and move your mouse around real fast.

[http://www.patrickbaudisch.com/projects/highdensitycursor/demo/highdensitycursor.html](http://www.patrickbaudisch.com/projects/highdensitycursor/demo/highdensitycursor.html)

So I was wondering if there is an effect like this that can be enabled in Compiz.  Anybody know?

---

### Post by -humanaut- on 2010-06-27
Do you have a Nvidia card by chance?

---

### Post by diablo75 on 2010-06-27
Yeah, I have an nVidia card.  I think it's a 9600 GSO or something nice like that.

---

### Post by diablo75 on 2010-07-04
Bump.

---

### Post by stderr on 2010-07-05
I don't think so. 

You can get a blaze of stars around the cursor by enabling the Show Mouse plugin in CCSM, reducing the Radius setting to its lowest and initiating it. Whilst not what you want, you could grab the source code (sudo apt-get source compiz-fusion-plugins-extra), src/showmouse/showmouse.c, and use that as a base to create a custom plugin.

Quite a lot of work though...

As an aside, by playing with the showmouse settings you can create some interesting effects anyway.

edit: You might also be able to draw inspiration from the source for the Motion Blur plugin.

---

