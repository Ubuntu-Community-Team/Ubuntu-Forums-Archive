---
title: "updating gnome-do?"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by ntrgc89 on 2009-03-19
Hi, I'm wondering how I can update gnome-do from 0.6 to the recently released 0.8. I've looking all over but can't find a simple "update" solution. Something this simple should not be so complicated....

Any help is much appreciated, thanks!

---

### Post by jlochhead on 2009-03-19
It is reasonably simple. They provide a PPA for 32 bit users and a .deb file for 64 bit users.

[https://launchpad.net/do](https://launchpad.net/do) and take a look.

---

### Post by jlochhead on 2009-03-19
I have had problems with the most recent one though, the notification, applets and one of the themes did not work.

---

### Post by ntrgc89 on 2009-03-19
I'm a little confused, how do I use the information you provided to get it to update? I tried adding "https://edge.launchpad.net/do/0.8" to the repositories, but that didn't work.....

---

### Post by jlochhead on 2009-03-19
Are you on 32 bit or 64 bit?

---

### Post by ntrgc89 on 2009-03-19
32

---

### Post by jlochhead on 2009-03-19
Assuming you are on Intrepid:

Go to System > Administration > Software Sources > Third Party Software

Add:

deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main

Make sure they are checked.

Download. [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x28A8205077558DD0](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x28A8205077558DD0)

Go to the Authentication tab. Click import key and import the key you downloaded from the link above.

Close software sources and your repository should update.

It is now in Synaptic for you.

If you don't use Intrepid check for the other repository links at [https://launchpad.net/~do-core/+archive/ppa](https://launchpad.net/~do-core/+archive/ppa)

---

### Post by ntrgc89 on 2009-03-19
I didn't have them checked..... that was the issue....

Thanks for your help and patience while I worked through some silly issues!

---

