---
title: "Removing entry from Grub"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by ginger.wombat on 2010-03-24
Hi!!

I have been using ubuntu on and off in its various forms for a few years now, and have just installed Karmic. Great job!!!! However, just after installing and running software update, I used computer janitor to remove the old kernel and headers. 

In previous versions I could sudo gedit /etc/grub/menu.lst, now I cannot!!

I have found that I now have to run update-grub as root as a cfg file automatically generates the list. 

My problem is that after doing this, the old kernel still appears as an option on boot. 

It's  not a huge problem, I just don't like the look of it!!!

Ta.

---

### Post by asmoore82 on 2010-03-24
I believe the file must still be there for it to be in the generated list...

Double check that all of the old kernel packages are gone from the "obsolete" section in synaptic
-OR- run this to see:
```
aptitude search "?obsolete"
```

---

### Post by ginger.wombat on 2010-03-24
Command returns nothing.
I can't find the obsolete section in Synaptic package manager.

---

### Post by andrewthomas on 2010-03-24
search for linux-image in synaptic and delete the ones that you don't want (along with the headers)

---

### Post by ginger.wombat on 2010-03-24
Ta muchly. Job done.

---

### Post by egalvan on 2010-03-24
Ubuntu-Tweak is recommend over Computer Janitor.

Does a better job of cleaning up.

As for the GRUB menu list, this is totally different in the new GRUB2.

The old method of editing menu.lst no longer exists.

hermanAB has a good web site, with excellent info on the new methods.

home page
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

GRUB2 page
[http://members.iinet.net.au/~herman546/p20.html](http://members.iinet.net.au/~herman546/p20.html)

---

### Post by ginger.wombat on 2010-03-25
ubuntu-tweak good!

---

