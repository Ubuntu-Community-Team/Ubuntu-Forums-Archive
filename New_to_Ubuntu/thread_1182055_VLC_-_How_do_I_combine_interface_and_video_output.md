---
title: "VLC - How do I combine interface and video output?"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by NotoriousMOK on 2009-06-08
I'm not entirely sure if VLC was changed, or if I fat-fingered an option by mistake, but when I play a video in VLC, I get one window with the output, and another small window with playback controls etc.  This used to be combined in one window.  Can somebody tell me what I did wrong and/or how to correct this to display all on one window?

Thanks!

---

### Post by reeseslover531 on 2009-06-08
If you are using Jaunty, this is a bug in the version of VLC that was included with Jaunty. To fix this update vlc to 1.0 using this [PPA]("https://launchpad.net/~kow/+archive/ppa") It is pretty straight foward, good luck!

---

### Post by SaaTeeVaaGreen on 2009-06-08
try opening vlc and go to tools>preferences and in the interface section check the box that says 'integrate video in interface'. this should do it for you

---

### Post by andrew.46 on 2009-06-09
Hi reeses,

> **reeseslover531 said:**
> If you are using Jaunty, this is a bug in the version of VLC that was included with Jaunty. To fix this update vlc to 1.0 using this [PPA]("https://launchpad.net/~kow/+archive/ppa") It is pretty straight foward, good luck!

A small nitpick: not actually a bug but a deliberate strategy taken by the vlc devs. But I certainly agree that an upgrade to vlc 1.0 rc2 is an excellent move. I have been using it since it came out and it appears rock solid.

Andrew

---

### Post by NotoriousMOK on 2009-06-10
Upgrading to RC2 did the trick -- thanks for your help!

---

### Post by andrew.46 on 2009-06-10
Hi NotoriousMOK,

> **NotoriousMOK said:**
> Upgrading to RC2 did the trick -- thanks for your help!

Great news! Mind you rc3 is out now :-).

Andrew

---

### Post by Hilko on 2009-06-16
> **reeseslover531 said:**
> If you are using Jaunty, this is a bug in the version of VLC that was included with Jaunty. To fix this update vlc to 1.0 using this [PPA]("https://launchpad.net/~kow/+archive/ppa") It is pretty straight foward, good luck!

It worked. Thanks ! But I wouldn't call it "straight forward". I had to manually download and install seven packages, all in exactly the right order.

libx264-67
x264
libvlccore
libvlc2
vlc-nox
vlc
mozilla-plugin-vlc

and why is this a 'strategic move' of the developpers ?

---

### Post by kpkeerthi on 2009-06-16
> **Hilko said:**
>  I had to manually download and install zeven packages, all in exactly the right order.

libx264-67
x264
libvlccore
libvlc2
vlc-nox
vlc
mozilla-plugin-vlc
You dont have to manually download and install from the PPAs. The [PPA]("https://launchpad.net/~kow/+archive/ppa") has instructions on how to install the packages from it using package managers.

---

### Post by Hilko on 2009-06-16
oops. I didn't see the instructions. But it works now anayway.

---

### Post by kpkeerthi on 2009-06-17
> **Hilko said:**
> oops. I didn't see the instructions. But it works now anayway.
It will. But when the PPA is updated you will not receive the updates automatically. You have to download and install the updated packages manually, in the order you followed before.

---

### Post by Hilko on 2009-06-18
Oh no! I want the automatic updates. How can I undo what I have done and enable automatic updates ?

---

