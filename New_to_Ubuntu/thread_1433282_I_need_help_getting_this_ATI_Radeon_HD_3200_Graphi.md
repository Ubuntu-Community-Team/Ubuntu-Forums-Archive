---
title: "I need help getting this ATI Radeon HD 3200 Graphics Card to work properly."
date: 2010-03-18
forum: New to Ubuntu
---

### Post by Missy375 on 2010-03-18
I am totally new to Ubuntu and I will try and explain my problem as best I can.

I am using Ubuntu 9.10 Karmic

I tried to enable the Visual Graphics and it told me that my driver was not activated. But I had Activated it before I tried turning on the Visual Graphics. Am I missing a package or something. And if I need to code using terminal or other wise could you provide step by step help. I'm sorry to be such a pain but I could really use some help. Thank you.

---

### Post by sandyd on 2010-03-18
> **Missy375 said:**
> I am totally new to Ubuntu and I will try and explain my problem as best I can.

I am using Ubuntu 9.10 Karmic

I tried to enable the Visual Graphics and it told me that my driver was not activated. But I had Activated it before I tried turning on the Visual Graphics. Am I missing a package or something. And if I need to code using terminal or other wise could you provide step by step help. I'm sorry to be such a pain but I could really use some help. Thank you.
A: Did you use System -> Administration -> Hardware drivers.
B: This may sound stupid, but did you restart your computer?

---

### Post by QIII on 2010-03-18
In Karmic, the AMD/ATI HD cards are driven by AMD/ATI's Catalyst 9.10, which is in the repositories.

Do what Carlee says above, then look for "catalyst" in Synaptic.  I believe you want the "Catalyst Control Center"  (sorry, I'm not at my Ubuntu machine.  Still earning my tainted bread at work on a Windows machine...)  Install that from Synaptic.

CCC 9.10 will allow you to configure your graphics.


Just as a warning!  DON'T upgrade to Lucid (10.04) until the new version of Catalyst is available for it.  Through 9.12 (at least), Catalyst is incompatible with the Xserver version in Lucid, and you will not be able to use your machine.  AMD/ATI plans to have a new pre-release of Catalyst available for the Lucid repositories when Lucid is in final release.  They've done that a couple of times.

Everyone but Ubuntu users will have to wait until the release version of Catalyst is available.

---

### Post by GeoPrude on 2010-03-18
> **Missy375 said:**
> I am totally new to Ubuntu and I will try and explain my problem as best I can.

I am using Ubuntu 9.10 Karmic

I tried to enable the Visual Graphics and it told me that my driver was not activated. But I had Activated it before I tried turning on the Visual Graphics. Am I missing a package or something. And if I need to code using terminal or other wise could you provide step by step help. I'm sorry to be such a pain but I could really use some help. Thank you.

Welcome to ubuntu :)

---

