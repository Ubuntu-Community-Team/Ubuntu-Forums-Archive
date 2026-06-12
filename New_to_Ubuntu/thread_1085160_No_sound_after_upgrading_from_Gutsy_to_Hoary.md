---
title: "No sound after upgrading from Gutsy to Hoary"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by MiffTheFox on 2009-03-02
Okay, this PC originally had Ubuntu Gutsy installed, I've since switched over to Kubuntu, and just now I've upgraded to [s]Hoary.  (Or something, I don't know how to check the current version in Kubnutu.)[/s] Hardy.

Anyways, since the upgrade I've no longer had sound.  I tried running kmix and turning the volume up to no avil.

I don't know if it's related, but when I start up Aduacious, I get a "broken GTK engine message":

> 
**Broken GTK engine in use**

Audacious has detected that you are using a broken GTK engine.

The theme engine you are using, *Qt*, is incompatible with some of the features used by modern skins.  The incompatible features have been disabled for this session.

To use these features, please consider using a different GTK theme engine.


This is what I get when I run asoundconf list:
```

Names of available sound cards:
NVidia

```

I'm using the nVidia beta driver (NVIDIA-Linux-x86-171.06-pkg1.run).

Please help! :confused:

---

### Post by halitech on 2009-03-02
how did you upgrade? if you do in fact have hoary, that is a major step backwards, not upgrade

---

### Post by MiffTheFox on 2009-03-02
> **halitech said:**
> how did you upgrade? if you do in fact have hoary, that is a major step backwards, not upgrade

I ran
```

update-manager --devel-release

```
and clicked the Upgrade button next to the "New distribution release" version.

Okay, I got confused, what I really have is Hardy, not Hoary (I was just trying to remember the name of the "H" release...)

```

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04
Release:        8.04
Codename:       hardy

```

---

### Post by halitech on 2009-03-02
ok :)  

I'm not real sure on the sound. could you give us the output of
```
aplay -l
```

---

### Post by MiffTheFox on 2009-03-02
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by halitech on 2009-03-02
ok, doesn't look like an issue with the hardware or the software as far as the card goes. I'd say something to do with the qt theme it was talking about.

---

### Post by MiffTheFox on 2009-03-02
> **halitech said:**
> ok, doesn't look like an issue with the hardware or the software as far as the card goes. I'd say something to do with the qt theme it was talking about.

Apparently not.  Going into kcontrol and setting the "GTK Styles and Fonts"->"Use another style"  to Human gets rid of the theme error message but I still can't get sound... :-(

---

### Post by halitech on 2009-03-02
I've never used KDE so not sure what tools are available there so will just bump this and hope someone else can help

---

