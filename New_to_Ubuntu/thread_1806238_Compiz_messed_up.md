---
title: "Compiz messed up"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by Elfyy on 2011-07-17
So, I was in Compiz and enable the cube and one of the conflicts was something with opengl. I thought I hit the right button but now Ubuntu is completely messed up... I can't see the toolbar or any other icons, can't open terminal w/ alt ctrl t. I can't do anything.... I'm on winxp right now. Any ideas??? Thanks!

---

### Post by Frogs Hair on 2011-07-17
For Unity 

Restart with the button on the computer , when the login screen comes up select your user name and enter the password .

Before login , select the recovery console from the session list below the greeter box on the bottom panel.

Enter, the code restart the computer . When login screen comes up again select Ubuntu from the session list .

```
unity --reset
```

For Classic Gnome . try this command from the recovery console .
```
gconftool-2 --recursive-unset /apps/compiz (reset)

```

---

### Post by Elfyy on 2011-07-17
> **Frogs Hair said:**
> For Unity 

Restart with the button on the computer , when the login screen comes up select your user name and enter the password .

Before login , select the recovery console from the session list below the greeter box on the bottom panel.

Enter, the code restart the computer . When login screen comes up again select Ubuntu from the session list .

```
unity --reset
```

For Classic Gnome . try this command from the recovery console .
```
gconftool-2 --recursive-unset /apps/compiz (reset)

```

I diddnt know what I had so I just tried both of those and neither worked... It didnt say really anything in cmd line after I entered those...

---

### Post by Blasphemist on 2011-07-17
Substitute this for the gconftool command above.
```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
sudo reboot
```

---

### Post by zathras1974 on 2011-07-17
I ran into the same issue and found that this is a known issue with 11.04. But don't dispair, there is [an excellent tutorial]("http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html") on how to get this all going over at Ubuntu4beginners. Just follow the instructions and you'll be good to go. :)

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

### Post by Elfyy on 2011-07-17
Thanks you very much! Blasphemist, your directions worked great! Zath I'm about to try that guide, hope it works!

---

### Post by Blasphemist on 2011-07-17
This tutorial is the best one I've seen.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

Glad the reset worked!

---

