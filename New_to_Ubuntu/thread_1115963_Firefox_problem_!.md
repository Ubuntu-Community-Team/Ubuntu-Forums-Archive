---
title: "Firefox problem !"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by alket on 2009-04-04
When I Zoom In (Ctrl +) Firefox to view a web page content, all images are scrambled, even if I zoom in just one time.

How to fix it ?

---

### Post by keplerspeed on 2009-04-04
Images are scrambled? As in the resolution of the image is really low, or is there just bits all over the place? Try to give us some more info about your problem. have you tried restarting or reinstalling firefox? Have you updated your system? What version of firefox are you using?

---

### Post by alket on 2009-04-05
I use 
screen resolution 1280x800
Intrepid Ibex with latest updates
Firefox 3.08

I had Ubuntu in another pc but it scrambled too.

---

### Post by blackened on 2009-04-05
We're not understanding what you mean by "scrambled".  Do you mean the entire Firefox window displayed garbage or just particular images in Firefox?

---

### Post by alket on 2009-04-05
Screenshot of firefox
[http://i40.tinypic.com/20rww5.jpg](http://i40.tinypic.com/20rww5.jpg)

---

### Post by blackened on 2009-04-05
You're zooming in on raster thumbnails of larger images, and it's only normal that they should pixelate. I don't think it's possible to change that behavior.

---

### Post by alket on 2009-04-05
What Im saying is that just with one Zooming it scrambles too much than usually, Firefox in Windows XP zooms perfectly.

---

### Post by ibizatunes on 2009-04-05
I had a similar issue, 
i fix it by go to place > home folder >  view hidden files > find .mozzila > right click and rename to .mozzila.old

reopen firefox and it worked

---

### Post by blackened on 2009-04-05
> **babaroga said:**
> What Im saying is that just with one Zooming it scrambles too much than usually, Firefox in Windows XP zooms perfectly.

Given to guessing, amateur that I am, I would say that this could be attributed to the differences between the way the two GIF libraries (Windows and Linux) dither enlarged images. But since I am not a dev, do not take this information for fact. Google was not helpful for seeking detailed information about the differences.

---

### Post by alket on 2009-04-05
> **ibizatunes said:**
> I had a similar issue, 
i fix it by go to place > home folder >  view hidden files > find .mozzila > right click and rename to .mozzila.old

reopen firefox and it worked

It's not working still.

---

### Post by doug1212 on 2009-04-05
Hi,
Have you tried going to View > Zoom > and checking Zoom text only.
This should do the trick.

---

### Post by alket on 2009-04-05
> **doug1212 said:**
> Hi,
Have you tried going to View > Zoom > and checking Zoom text only.
This should do the trick.

Yes it works, but not for the images

---

### Post by blackened on 2009-04-05
> **babaroga said:**
> Yes it works, but not for the images

I'm going to save you some trouble and tell you that you're probably not going to find something to make this work the way you want it to. Especially since there is nothing technically wrong with the way it is now. It could just be that the GIF libraries use two different dithering algorithms that produce very different quality images at that level of zoom. Still, you probably can't change that without editing and recompiling the library itself.

---

### Post by alket on 2009-06-12
I cannt understand this
I open google.com and Zoom it in maximum
it scrambles, but when i drag it  (no dropp), it has original quality.
Can I do some trick  to be quality like dragging ?

---

