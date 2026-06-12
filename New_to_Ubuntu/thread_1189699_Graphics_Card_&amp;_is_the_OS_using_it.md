---
title: "Graphics Card &amp; is the OS using it?"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by JoeNZ on 2009-06-17
Hello from NZ,

I have an ATI Radeon 9250 graphics card with 128mb. This may sound dumb but besides being able to adjust visual effects up or down, is there a way of telling whether the OS is using the graphics card and it's available memory? 

Also, I have downloaded the latest official ATI driver - ati-driver-installer-8.28.8 - for this card. Is it worth installing it or should I stick with the Ubuntu supplied driver?

I don't have the most powerful system around but I would like to squeeze every ounce of blood out of it without compromising performance. I'm not a fan of sluggish systems.

Regards
JoeNZ

---

### Post by khalis on 2009-06-17
Anyone please correct me if I'm wrong.

Older ATI cards are generally well supported by the open source drivers.  Specifically, the Radeon 9250 has hardware 2D and 3D acceleration ([https://help.ubuntu.com/community/RadeonDriver#Full%203D%20support%20(r100%20and%20r200%20series](https://help.ubuntu.com/community/RadeonDriver#Full%203D%20support%20(r100%20and%20r200%20series)).  You can test this by opening a terminal and typing 'glxinfo | grep direct' and you should see:

direct rendering: Yes

Video memory (the memory available to the video card) is only used as a video buffer and storage for graphic-specific data (pixel, vertex, shader data).  So unless you're playing newer games that require more than 128MB, its non consequential.

Unless you experience a specific graphics-related bug with your current drivers, there's no reason to upgrade to the latest.  The latest and greatest drivers aren't always stable on older hardware and will often actually degrade performance as they optimize them for newer hardware.

---

### Post by JoeNZ on 2009-06-17
Sweet. I will stick with what I have already.

I ran the command glxinfo | grep direct and got "yes".

Having a play with compiz settings at the moment.

---

