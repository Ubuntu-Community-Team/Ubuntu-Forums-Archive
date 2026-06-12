---
title: "Compiz Cube"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by nj73 on 2010-03-30
Sorry I'm a linux noob...
I installed compizconfig and used a guide to try and set up the 3d desktop cube, but it isn't working at all. Nothing has changed; I still have two workspaces and switch between them when I press Ctrl-Alt-Right/Left. 
I have expo, desktop cube, rotate cube, and cube reflection/deformation turned on. What am I doing wrong?
Oh, and I'm using Ubuntu 9.10.

---

### Post by 00arthuryu on 2010-03-30
change your desktop horizontal size from 2 to 4, it should be under desktop size in general options  :D

---

### Post by admiralspark on 2010-03-30
Haha, 30 seconds on google got me this:
With the 4 desktops as mentioned above, hold down Ctrl+Alt+Left Mouse Button and move the mouse to zoom et all.

---

### Post by ssulaco on 2010-03-30
[http://wiki.compiz.org/Plugins/Cube](http://wiki.compiz.org/Plugins/Cube)

---

### Post by quadproc on 2010-03-30
> **nj73 said:**
> Sorry I'm a linux noob...
I installed compizconfig and used a guide to try and set up the 3d desktop cube, but it isn't working at all. Nothing has changed; I still have two workspaces and switch between them when I press Ctrl-Alt-Right/Left. 
I have expo, desktop cube, rotate cube, and cube reflection/deformation turned on. What am I doing wrong?
Oh, and I'm using Ubuntu 9.10.
I went through the same experience and eventually learned that certain things must be set up in certain way to get it  to work.

One thing: set up your screens to a 4x1 array.  To do this, right click on the array of rectangles in the bottom bar, right next to the trash can.  Select Preferences, choose 4 columns and 1 row.

Another thing: in System > Appearance > CCSM, click on Rotate Cube.  At the bottom of this new window is an entry called Zoom.  Set this to some value near 0.3.  Also, select Rotate Cube.

Now, try ctrl-alt-right arrow.  Your cube should rotate.  Use ctrl-alt-left arrow to rotate the cube back.  Now, pick some window and drag it off of the edge of the screen.  The cube will rotate under the window and your window will now be on a new cube surface.

You need the 4 columns and 1 row because the cube has four sides so you need four places to put things one the "sides" of the cube.  You need some amount of zoom because the image needs space to grow into when you do the rotation.

You might find this writeup useful: [http://www.ghacks.net/2009/05/25/enabling-the-cube-in-compiz/](http://www.ghacks.net/2009/05/25/enabling-the-cube-in-compiz/)

Enjoy!

quadproc

---

