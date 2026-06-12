---
title: "Glunar clock applet"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by techno-mole on 2009-10-24
hello.

im running the beta of karmic 64bit (although with the recent updates its probably the rc)

i did have the glunar clock applet installed and running on my gnome panel, but after some of the recent updates it no longer runs, all i get when trying to add it to a panel is 

```
The panel encountered a problem while loading "OAFIID:GNOME_GLunarclockApplet".
do you want to delete the applet from your configuration ?
```

sometime i will get a message saying lunar clock applet closed unexpectedly, would you like to reload, if i select yes it will then give me the error message above.

i have been looking for bugs related to this, but as yet i havent found any, probably looking in the wrong place knowing me.

any advice would be appreciated.

cheers

---

### Post by wojox on 2009-10-26
Have you tried deleting it and reinstalling it from Synaptic?

---

### Post by dracodos on 2009-11-03
I have the same issue with 9.10 final 64 bit. I installed the 64bit deb package from jaunty and that worked: [https://launchpad.net/ubuntu/jaunty/amd64/glunarclock](https://launchpad.net/ubuntu/jaunty/amd64/glunarclock)

I haven't had a chance to submit a bug report yet (haven't registered) but it doesn't look like anyone else has either. If i get a chance i'll try to submit it tonight or tomorrow.

---

### Post by dracodos on 2009-11-04
ok there is a bug report on it in launchpad:
[https://bugs.launchpad.net/ubuntu/+source/glunarclock](https://bugs.launchpad.net/ubuntu/+source/glunarclock)

Also make sure when you load the jaunty release of glunarclock that you lock it so it won't attempt to update it. We'll just have to wait until the karmic release is fixed (or they decide to just use the juanty one instead ;)

---

### Post by techno-mole on 2009-11-13
cheers, ill subscribe to the bug as well, i did try the 64bit jaunty version but it crashes with the same error.

---

