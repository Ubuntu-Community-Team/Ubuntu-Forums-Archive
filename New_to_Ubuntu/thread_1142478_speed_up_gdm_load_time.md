---
title: "speed up gdm load time?"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by matthew.ball on 2009-04-29
Hi,

This guy ( [http://beans.seartipy.com/2006/10/01/how-to-speed-up-booting-into-gnome-a-gentoo-wiki-tip/](http://beans.seartipy.com/2006/10/01/how-to-speed-up-booting-into-gnome-a-gentoo-wiki-tip/) ) mentions something about starting gdm at boot? I'm not really sure what it means, but it would be interesting if this really did speed up the gdm boot time...

Just asking for someone who understands what the article says if they could offer some advice - I have a feeling it might not work for Ubuntu?

I don't really know, I assume not simply because it's not there.

---

### Post by skymera on 2009-04-29
I don't think this applies to Ubuntu as the article talks about XDM and is based on Gentoo.

But +1 for wanting to know how to speed up GNOME login.
Mines much slower than previous Ubuntu versions

---

### Post by kpkeerthi on 2009-04-29
You can look in System -> Administration -> Services and turn off the services you don't need. As for me, I have bluetooth and cups disabled as I have no need for them. If you are not sure what to turn off, ask us.

This article is pretty dated (2006!) and is for Gentoo. The init system ubuntu employs is different from Gentoo. Don't loose sleep over this; the Ubuntu devs have done commendable job in optimizing and speeding up the boot for you. Enjoy ubuntu!

---

### Post by matthew.ball on 2009-04-29
Yeah, I'm running bare minimum services and no desktop effects.

gdm still takes twice as long as - what I assume to be - the kernel...

---

### Post by skymera on 2009-04-29
Boot is very fast, login is slow.

Seems Canonical have taken some of the boot steps out which load at login.
That's all i can think it to be.

As for services, i run 2. GDM and DBUS

---

### Post by billgoldberg on 2009-04-29
You want faster GDM load time?

Don't use GDM, use a cli login and start x manually.

---

### Post by Praxicoide on 2009-04-29
You can also try slim, as a lighter alternative to gdm. That is what I have on my Xubuntu.

---

