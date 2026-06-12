---
title: "This is my video card... can I install 9.04?"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Nutopia on 2009-05-15
I was in the process of upgrading when I realized the video card problems. I ran: lspci | grep VGA

and got:

01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]


Will I have a problem with 9.04?

---

### Post by linsux on 2009-05-15
> **Nutopia said:**
> I was in the process of upgrading when I realized the video card problems. I ran: lspci | grep VGA

and got:

01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]


Will I have a problem with 9.04?

Yes, it will work. But you will have to remove the Fglrx driver and make sure it use RadeonHD.

---

### Post by Nutopia on 2009-05-15
Thanks - I'm all upgraded and things are looking good so far. How do I get the RadeonHD driver installed? I see where to disable the fglrx driver, but have not done so yet because I can't find where to get the other enabled.

---

### Post by Duskao on 2009-05-15
With that card you will be able to use either the new fglrx 8.600 (9.4 catalyst) or you can use the Radeon/RadeonHD drivers. I believe there is some 3d support for your video card with the open source (Radeon/RadeonHD) drivers but they still aren't up to the fglrx drivers. If you want to use the fglrx driver then I would suggest EnvyNG. It makes the installation very simple and will find the best driver for your video card with your system. In 9.04 with my vid card (Radeon 4850) the 2d in fglrx is kinda messed so it mostly only works with 3d stuff, which it seems to do fine. If you mostly use 2d go for the open source drivers. Hope that helps.

---

### Post by Duskao on 2009-05-15
For the RadeonHD I believe that you go into synaptic and do a search for RadeonHD. Like I said, I BELIEVE that is how you do it. I would like some clarification on this as well.

---

### Post by Nutopia on 2009-05-15
Package Manager allows me to download the following:
X.Org X server -- AMD/ATI r5xx, r6xx display driver

I've installed it - but not sure how to switch from fglrx to RadeonHD now.

---

