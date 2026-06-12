---
title: "Installing Ubuntu 8.04 w/o Grub"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by malura on 2009-08-19
I've seen similar posts on this, and they all mention that you'll see an option for it during the alternate install. I didn't see an option for installing Grub on anything else. Did I miss something? Is there some sort of option I'm supposed to select that allows me to see the Grub dialogue box (I dunno, like expert mode)?

---

### Post by LewRockwell on 2009-08-19
> **malura said:**
> I've seen similar posts on this, and they all mention that you'll see an option for it during the alternate install. I didn't see an option for installing Grub on anything else. Did I miss something? Is there some sort of option I'm supposed to select that allows me to see the Grub dialogue box (I dunno, like expert mode)?

so do you WANT grub installed?

or

did it install when you DIDN'T want it?

we just weren't sure exactly what the trouble-call was/is?

however, we might direct your attention to:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

.

---

### Post by pedro3005 on 2009-08-19
Did you use the normal installer or the alternative installer? The normal installer is via GUI, the alternative via command. I don't know much, but from what I understood, you only get that option on the alternative installer.
EDIT: OMG LewRockwell stop beating me to the posts! lol

---

### Post by Bodsda on 2009-08-19
> **malura said:**
> I've seen similar posts on this, and they all mention that you'll see an option for it during the alternate install. I didn't see an option for installing Grub on anything else. Did I miss something? Is there some sort of option I'm supposed to select that allows me to see the Grub dialogue box (I dunno, like expert mode)?

When using the GUI installer towards the end when it asks you to review the information given, there is an advanced button that allows you to select the destination of the grub files. If you dont then grub is installed to the beginning of the device you specified for / or the beginning of the device specified for /boot. (/boot taking precedence over /)

In the alternate installation I dont believe grub is mentioned unless you say to go back a step, then you are presented with a list of stages of the install, from which you can choose grub.

Hope this helps,

Kind regards,
Bodsda

---

### Post by malura on 2009-08-19
Sorry about the confusion in my first post. What I meant to say was that I was looking for a way to install Ubuntu to a hard drive without installing grub on the same hard drive (installing ubuntu w/o grub). Reason being is that I'm installing it on my old man's PC, and he gripes when things are...different. Anywho, Bodsda Nailed this post on the head. Thanks a bunch to all who replied.

---

### Post by LewRockwell on 2009-08-19
> **malura said:**
> Sorry about the confusion in my first post. What I meant to say was that I was looking for a way to install Ubuntu to a hard drive without installing grub on the same hard drive (installing ubuntu w/o grub). Reason being is that I'm installing it on my old man's PC, and he gripes when things are...different. Anywho, Bodsda Nailed this post on the head. Thanks a bunch to all who replied.

in those cases we often suggest installing the grub anyway and configuring it so that the desired operating system is automatically booted after a very short grub time-out(say three to five seconds)

that way it's fairly easy for everyone to do their own "thing"

.

---

