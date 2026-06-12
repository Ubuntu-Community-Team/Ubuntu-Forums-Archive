---
title: "Lubuntu?"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by coldReactive on 2009-10-29
Where is the ISO for Lubuntu? There's supposed to be one this release. :(

---

### Post by Korrode on 2009-10-29
I'm also hoping to see a Lubuntu release :)

---

### Post by Incendia on 2009-10-29
> **Korrode said:**
> I'm also hoping to see a Lubuntu release :)
 
 
I've never seen Lubuntu before. Screenshots? :]

---

### Post by hthury on 2009-10-29
Thought it was a joke... lol ubuntu or something like this...

It's LXDE Ubuntu, I have just googled it.

---

### Post by shae on 2009-10-29
Lubuntu was not scheduled to be released as a CD in this version.  I believe the CDs will come in Lucid Lynx.

---

### Post by coldReactive on 2009-10-29
> **hthury said:**
> Thought it was a joke... lol ubuntu or something like this...

It isn't, and sadly, Lubuntu is much faster and takes up much less RAM than both Xubuntu and Ubuntu. (It has also been said that Xubuntu takes up more RAM than Ubuntu does.)

> **shae said:**
> Lubuntu was not scheduled to be released as a CD in this version.  I believe the CDs will come in Lucid Lynx.

Test ISOs were made, and a newsletter I found on google said that Lubuntu would be released soon (but the newsletter was from the 25th.)

---

### Post by Hospadar on 2009-10-29
You could just install somthing else (let's say you install the desktop version, since the kernel is compiled with more desktop-oriented switches).  Then totally remove gnome:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
(or if you installed kubuntu: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome))

Then:
```
sudo apt-get install lxde
```

That said, it's possible that lubuntu will be a little different than just installing the lxde packages, but probably not too much.

---

### Post by coolbrook on 2009-10-29
```
sudo nm-applet
```

...assuming you use Network Manager, and check the system settings to ensure that it's running as a startup application.

---

### Post by drzarkov on 2009-10-29
I've been hoping for a full release as rumored as well. Something to revive my collection of antique laptops. Maybe soon we'll see something fully assembled but for now there's a meta-package to create your own Lubuntu. I just happened to stumble across this last night while scrounging for news on the real deal:

[https://launchpad.net/ubuntu/+source/lubuntu-meta](https://launchpad.net/ubuntu/+source/lubuntu-meta)

I'm DLing the alternate install CD to try this out on my Thinkpad 570e, gonna rip out the Gnome bloat and replace with this package. Now if I could just find the 9.10 powerpc alt install to do the same to my Graphite Clamshell.

Let me know if anyone digs up any more info on Lubuntu, I thought the RC versions showed real potential once you figured out how to actually install. Just needed a bit of polishing. Wish somebody would get the word out a little better, not that we need time and resources wasted on ginormous signs in Times Square, but I could throw a little Lubuntu release party.

---

### Post by ranch hand on 2009-10-29
I actually have a LiveCD of Lubuntu but it is a LiveCD only.  It is very nice.  It is also very small (under 300Mb download).

I really like pcmanfm.

---

### Post by drzarkov on 2009-10-30
Pcmanfm _is_ great. Thunar gives me headaches and Gnome/Nautilus is too much for my decrepit old hardware.

Those LiveCD's (I'd found two) could be installed to your hard drive if you ran the installer as root. From terminal:

sudo ubiquity --desktop gtk_ui
Then the familiar GUI install begins.

I'm gonna check out this Lubuntu meta-package as soon as I've backed up the vanilla Karmic I just installed. I so desperately would love to see a real lightweight Ubuntu with some community support. The CrunchBang I'm running is amazing but a rough transition for people like me who avoid command line and wallow in the comfort a more traditional Ubuntu.

---

### Post by ranch hand on 2009-10-30
> **drzarkov said:**
> Pcmanfm _is_ great. Thunar gives me headaches and Gnome/Nautilus is too much for my decrepit old hardware.

Those LiveCD's (I'd found two) could be installed to your hard drive if you ran the installer as root. From terminal:

sudo ubiquity --desktop gtk_ui
Then the familiar GUI install begins.

I'm gonna check out this Lubuntu meta-package as soon as I've backed up the vanilla Karmic I just installed. I so desperately would love to see a real lightweight Ubuntu with some community support. The CrunchBang I'm running is amazing but a rough transition for people like me who avoid command line and wallow in the comfort a more traditional Ubuntu.

Thanks a lot.  I never even thought about running the installer as root.  I are smart.

I think that crunchbang is  overrated and not near as light as folks claim.  Seemed about like xubuntu size wise.

---

