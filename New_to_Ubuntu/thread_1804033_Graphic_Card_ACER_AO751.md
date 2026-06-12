---
title: "Graphic Card ACER AO751"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by niko001 on 2011-07-14
I am running latest Ubuntu version on my Acer netbook. Problem now is that any videos have a jerky movement. I had no problems while running windows while watching any videos. Any help?

---

### Post by macaholic on 2011-07-14
Does this happen with all videos, or just flash videos?

---

### Post by niko001 on 2011-07-14
Videos mostly...while using banshee or movie player.

Just a side note, I noticed that even while scrolling the browser it is a bit jerky.

---

### Post by niko001 on 2011-08-21
Any help? Thanks

---

### Post by 3rdalbum on 2011-08-21
My research indicates that your netbook uses the GMA500 graphics chip; this is known as Poulsbo. Unfortunately, this GPU is not very well supported on Linux because it's not actually made by Intel: [http://en.wikipedia.org/wiki/Intel_GMA#GMA_500_on_Linux](http://en.wikipedia.org/wiki/Intel_GMA#GMA_500_on_Linux)

You might want to find the gma500 repository; it's a kind of like a place on the Internet you can tell Ubuntu Software Center about, to allow it to install software from that place. The repository apparently contains a driver for the gma500 GPU.

That would probably be your first step.

---

### Post by niko001 on 2011-08-22
Thanks I will try as I do not have any experience in using linux as this is the first time trying.

---

