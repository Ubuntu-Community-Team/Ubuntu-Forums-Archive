---
title: "Sound preferences menu"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by jontheid on 2010-12-01
Ok, I've got Xubuntu 10.10 with all the latest updates running on a Toshiba Satellite L30.

It looks great, and runs well.
Inbuilt sound works great, straight out of the box, lovely.

I also have a usb headphone set that I only want to use some of the time (when listening to music on headphones, skype etc). The drivers for this installed automatically, all seems to be ok.

In Ubuntu there is a nice sound preferences menu where you can choose what device to use for system sounds, video conferencing etc.

This doesn't seem to exist at all in Xubuntu 10.10.

In fact, I don't know how to set up system sounds at all.

Any help would be greatly appreciated.

Jon

p.s. I did manage to get my Canon Pixma iP1800 printer working though! I posted the solution on here today on a thread started by people who coudn't install theirs.

---

### Post by jontheid on 2010-12-01
This now solved by the brilliant folks on IRC chat
#xunbuntu
on the Freenode server.

It turns out that you need to install a package called pavucontrol
which is a pulse audio volume control / management thing

Just type 

sudo apt-get pavucontrol

Then you can turn on system sounds in pavucontrol, then you need to enable them in settings - xfce4 settings manager - appearance - settings

Cheers
Jon

---

