---
title: "I need help on installing video driver on my Ubuntu"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by seojunkim on 2011-08-14
I am a beginner in Ubuntu
I run Ubuntu 11.04 natty. I have encountered the problem that I cannot use my unity desktop.
I have tried installing Catalyst Control center 11.7 but it says that no driver is found. (In fact, I have installed the fglrx driver!) Which driver should I install? and How should I install the display driver?? I am very confused.

System
Intel Celeron M 530 @ 1.73Ghz
Phoneix Motherboard 
ATI Radeon x1250

Help would be much appreciated :)

---

### Post by 3rdalbum on 2011-08-14
Don't install the fglrx driver. If you read the notes and system requirements for it, you'll notice that your card is no longer supported by it. The Catalyst Control Center only works with fglrx, so you can't use that either.

Normally the default 'ati' open-source driver should be able to run your display and give you some 3D acceleration, enough to run Unity. But then, maybe on that particular card it can't give you 3D. I don't know enough about ATI to know about that specific card.

You can use Unity-2D which is a version of Unity that doesn't require 3D acceleration. It's in the Synaptic Package Manager. After installing it, you can log out and then click on your name, and choose Unity 2D from the popup menu at the bottom of the login screen.

---

### Post by Spock. on 2011-08-14
You could also try going to System > Administration > Additional Drivers and seeing if your GFX drivers are there.

---

### Post by 3rdalbum on 2011-08-14
> **Spock. said:**
> You could also try going to System > Administration > Additional Drivers and seeing if your GFX drivers are there.

They won't be. ATI's driver only supports Radeon HD and newer cards, not the Radeon X series. It's been this way since 2008.

---

