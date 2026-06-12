---
title: "How can I fix this?"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by slowsmoke on 2009-11-15
You are unable to play in 3D mode due to the following problems:
No Python OpenGL support
No Python GTKGLExt support

Please contact your system administrator to resolve these problems, until then you will be able to play chess in 2D mode.

---

### Post by coldReactive on 2009-11-15
I think it's...
```
sudo apt-get install python-opengl python-gtkglext1
```

in applications . accessories . terminal

sudo won't show asterisks/text when you enter your password, the cursor won't even move, just enter the password and hit enter.

---

### Post by slowsmoke on 2009-11-15
> **coldReactive said:**
> I think it's...
```
sudo apt-get install python-opengl python-gtkglext1
```in applications . accessories . terminal

sudo won't show asterisks/text when you enter your password, the cursor won't even move, just enter the password and hit enter.
Thank you, this worked.

---

### Post by slowsmoke on 2009-11-15
> **coldReactive said:**
> I think it's...
```
sudo apt-get install python-opengl python-gtkglext1
```in applications . accessories . terminal

sudo won't show asterisks/text when you enter your password, the cursor won't even move, just enter the password and hit enter.

Also I was wondering if you can help me on this issue.  I installed a game called trigger.  When I try to play it my screen go black and I get a message saying my input signal is out of range?  What could this be?

---

### Post by coldReactive on 2009-11-15
> **slowsmoke said:**
> Also I was wondering if you can help me on this issue.  I installed a game called trigger.  When I try to play it my screen go black and I get a message saying my input signal is out of range?  What could this be?

The game could be trying to force a certain refresh rate or something. What graphics card do you have? If you have nvidia, have you made sure that you set "Sync to vblank" on for OpenGL?

---

### Post by slowsmoke on 2009-11-15
> **coldReactive said:**
> The game could be trying to force a certain refresh rate or something. What graphics card do you have? If you have nvidia, have you made sure that you set "Sync to vblank" on for OpenGL?

nvidia GeForce 7600gs with 512.  Please excuse my ignorance, but what is "Sync to vblank" on for OpenGL?

---

### Post by coldReactive on 2009-11-15
> **slowsmoke said:**
> nvidia GeForce 7600gs with 512.  Please excuse my ignorance, but what is "Sync to vblank" on for OpenGL?

System > Settings/Preferences

there should be an nvidia control panel. In there, under OpenGL Settings, there should be a sync to vblank checkbox.

---

### Post by slowsmoke on 2009-11-15
> **coldReactive said:**
> System > Settings/Preferences

there should be an nvidia control panel. In there, under OpenGL Settings, there should be a sync to vblank checkbox.
sync to vblank is now checked and is still not working...

---

