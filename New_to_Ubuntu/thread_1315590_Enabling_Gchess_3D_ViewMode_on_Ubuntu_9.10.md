---
title: "Enabling Gchess 3D View/Mode on Ubuntu 9.10"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Nightstrike2009 on 2009-11-05
Hiya everyone

I have come across and resolved the problem of Gchess's 3D View:
> No Python OpenGL support
No Python GTKGLExt support

by downloading the appropriate .deb files (on another pc at the moment but will share this info when I get back to own PC)

3D View now works but every time I click "Start New Game" it just ignores me and have to switch back to 2d view to start a new game then back to 3d once done. 

I know this is a minor complaint but its annoying, any idea how to fix this bug?

---

### Post by Excedio on 2009-11-05
System > Administration > Synaptic Package Manager

python-gtkglext1
python-opengl

All done :-)

---

### Post by Nightstrike2009 on 2009-11-05
Not quite Excedio;
> **My Myself earlier;**
I have come across and resolved the problem of Gchess's 3D View:
No Python OpenGL support
No Python GTKGLExt support
by downloading the appropriate .deb files (**on another pc at the moment but will share this info when I get back to own PC)**

The files I have fixed it with are: 
[COLOR="DarkGreen"]
freeglut3_2.4.0-6.1ubuntu1_i386.deb
libgtkglext1_1.2.0-1ubuntu1_i386.deb
python-gtkglext1_1.1.0-3.1build1_i386.deb
python-opengl_3.0.0-0ubuntu1_all.deb[/COLOR]

As I promised earlier which is the same as Excedio suggested but I have done that and thats why I started this thread, thanks for trying to help though. 

Anyone any ideas how to fix this problem?

---

### Post by Excedio on 2009-11-05
Interesting. Once I installed the packages that I mentioned...everything worked perfectly for me.

---

### Post by Nightstrike2009 on 2009-11-10
I've now downgraded to Ubuntu 9.04 as well as this issue bluetooth wasn't working, had sound issues and 3G Vodafone Modem had a connection problem with the internet.

Not happy at all with 9.10 should still be in beta, If anyone can solve the chess problem with 9.10. please post your results here, I give up with 9.10. :(

---

