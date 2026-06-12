---
title: "Gnome Power Manager"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by RealG187 on 2009-03-06
I have Gnome Power manager on my laptop, I want to put it onto my other laptop with a fresh install (hard drive finally came in the mail) but when I right click and goto add to panel I cannot see it there, I go on my fist laptop and when I goto add to panel I don't see it there. It's already there,I don't know how I got it there, all I know is I want it on both laptops but I can't see it in the applet list!

---

### Post by rafac24 on 2009-03-06
Try terminal

```
sudo gnome-power-manager
```

See if that pulls it up.

---

### Post by RealG187 on 2009-03-06
The thing in the lower right hand corner appears.

Maybe that's why I didn't see it before.

It makes sense about the battery since I haven't used this laptop in a while because it didn't have a hard drive (the other one failed, it's in a data recovery lab now) and the new one just came in today.

I think after I start using it again that will go away. Right now it says my battery is at 100%

---

### Post by rafac24 on 2009-03-06
Two more tasks I can recommend:

1. Be sure that Gnome-Power-Manager is checked for startup. To do this:

```
sudo gnome-session-properties
```
Check the box for the power manager.

2. Check the boxes under preferences so that your gnome-power-manager shows in the Panel.

```
sudo gnome-power-properties
```

---

### Post by RealG187 on 2009-03-07
I don't think that first one needs to be done as sudo, its the same thing when  you goro system --> preferences --> sessions and I never had to enter my password/authenticate

sudo gnome-power-properties gives nothing, but I think sudo gnome-power-preferences does (the same thing when you right click the applet)

But thanks for thr quick reply

---

