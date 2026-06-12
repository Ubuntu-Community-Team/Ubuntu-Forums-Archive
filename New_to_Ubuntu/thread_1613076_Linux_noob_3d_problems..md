---
title: "Linux noob 3d problems."
date: 2010-11-04
forum: New to Ubuntu
---

### Post by thewraith420 on 2010-11-04
Hi everyone, i'm new to linux and trying out ubuntu 10.10 on the advice of a freind. So far i'm installed and everythings gone pretty smooth but i'm haveing some problems with getting my intigrated video working correctly. It's an ATI Radeon Xpress 200 Series. apparently fglxr dosen't support this anymore and the x.org drivers dont seem to help.  any help would be appreciated. Thanks.

---

### Post by Daniel0108 on 2010-11-04
Hi!
Amd released drivers for linux ;)
Just search for the ati driver on the amd homepage, and download it for linux.
That should work :)
Yours,
Daniel

---

### Post by waynefoutz on 2010-11-04
> **thewraith420 said:**
> Hi everyone, i'm new to linux and trying out ubuntu 10.10 on the advice of a freind. So far i'm installed and everythings gone pretty smooth but i'm haveing some problems with getting my intigrated video working correctly. It's an ATI Radeon Xpress 200 Series. apparently fglxr dosen't support this anymore and the x.org drivers dont seem to help.  any help would be appreciated. Thanks.

your correct, the fglxr drivers won't work with your card. The best you are going to get is with the ones installed out of the box. They should work pretty good. They are about 80% of where they should be on my system.

---

### Post by thewraith420 on 2010-11-04
> **waynefoutz said:**
> your correct, the fglxr drivers won't work with your card. The best you are going to get is with the ones installed out of the box. They should work pretty good. They are about 80% of where they should be on my system.

Well.. I'd have no problem using the installed drivers but it seems anything openGL gets distorted

---

### Post by thewraith420 on 2010-11-04
> **Daniel0108 said:**
> Hi!
Amd released drivers for linux ;)
Just search for the ati driver on the amd homepage, and download it for linux.
That should work :)
Yours,
Daniel


Correct me if i'm wrong but, i thought the fglxr drivers were the proprietary ati ones...

---

### Post by Daniel0108 on 2010-11-04
so, you tried to install the drivers, supported by ubuntu team AND the drivers from the ati page?
for me only the drivers from the ati page worked correctly :PPP
Yours,
Daniel

---

### Post by eriktheblu on 2010-11-04
I have one of those cards myself and can honestly say you aren't going to get great performance out of it. If you want tolerable drivers, you probably will need to downgrade to an earlier version of Ubuntu (8.04 I'd say)

---

### Post by Daniel0108 on 2010-11-04
> **eriktheblu said:**
> I have one of those cards myself and can honestly say you aren't going to get great performance out of it. If you want tolerable drivers, you probably will need to downgrade to an earlier version of Ubuntu (8.04 I'd say)

oh, okay :P I downloaded drivers from the amd page... that was enough for me.
But I don't play many games on Ubuntu.

---

### Post by mcduck on 2010-11-04
> **Daniel0108 said:**
> so, you tried to install the drivers, supported by ubuntu team AND the drivers from the ati page?
for me only the drivers from the ati page worked correctly :PPP
Yours,
Daniel

That would be pointless, since Ati's drivers don't support the OP's GPU.

Ati dropped support for most of it's "old" hardware from the proprietary drivers some years ago, so anything older than that will only work with the open source drivers now. (or a very old version of the fglrx driver, that doesn't work with any up-to-date Linux distribution since it requires old version of X.org)

---

### Post by thewraith420 on 2010-11-06
hello again guys, thanks for the replys.. i'm considering downgrading to 8.04 now if it will fix my openGL. I know the card isnt the greatest anyways but should still allow me to play some games that support openGL.

---

### Post by waynefoutz on 2010-11-06
> **thewraith420 said:**
> hello again guys, thanks for the replys.. i'm considering downgrading to 8.04 now if it will fix my openGL. I know the card isnt the greatest anyways but should still allow me to play some games that support openGL.

 That will work, but unfortunately 8.04 is dead in April. It's probably a good idea to go ahead and install it, and learn as much as you can about Ubuntu between now and the end of April. When 11.04 comes out, they will take down 8.04's repositories so synaptic will no longer work, which means you won't be able to install software, unless you compile it yourself, and you will not get any security updates. After it dies, you can install Debian 5 (Lenny) [http://www.debian.org/]("http://www.debian.org/")which is about the same thing as 8.04, but without the hand holding that Ubuntu gives you, so it's not quite as easy to learn. Other than that though, it's pretty much identical, so much so that you can still come to this forum for help, because Ubuntu spawned from Debian, so under the hood, they are exactly the same. Or you could jump in with both feet into Debian now, it's up to you. Debian 5 runs an older version of Xorg that will work with your card's older driver, same as 8.04. Make sure you get Lenny, 5.0. On the download page you'll see there are 20 cds or 5 dvds. You don't need them all, the first DVD is pretty much all you need, the first CD will work if you have the computer hooked to the internet during the install. 

Another option is Mepis, [http://www.mepis.org/]("http://www.mepis.org/") which is another Distro like Ubuntu, but it's based on Debian 5. It has the KDE desktop instead of Gnome, but it is set up for beginners, so it has a pretty easy learning curve. The older fglrx drivers should work on this distro as well, although I've never tried it.

I have a laptop with a slightly newer card, but same brand, as what you have, only not new enough. I was running Debian up until a week ago, when I tried the latest open source drivers out on a live cd and decided they were good enough to have the laptop come back home to Ubuntu. 

good luck.

---

