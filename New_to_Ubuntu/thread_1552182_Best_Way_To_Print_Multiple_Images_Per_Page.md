---
title: "Best Way To Print Multiple Images Per Page"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by justinmiller87 on 2010-08-13
I have a bunch of 1"x1" and 2"x2" images that I want to print at actual size. Now obviously, it would be a huge waste of paper, trees and time to print these one at a time. Is there something like the Windows photo print wizard that lets one select photos and prints them in the most efficient manner per page?

---

### Post by Paul820 on 2010-08-13
> sudo apt-get install gnome-photo-printer

Should be what you are looking for, you can choose different sizes and preview before you print.

---

### Post by justinmiller87 on 2010-08-13
Perfect. Thanks.

---

### Post by lenooh on 2011-07-11
gnome-photo-printer is pretty broken - it does not remember settings and it does not fit images per page by itself.

shotwell (version 0.9 and up) has the feature you are looking for. Simply open shotwell photo manager, select the images you want to print, go to File -> Print... in the window that opens select Image settings -> Autosize and select the number of images per page.

If you are using KDE (kubuntu), you can do it with gwenview (or any other KDE imaging application) if you installed kipi-plugins. Go to Plugins -> Printer assistant ... and follow the steps.

---

### Post by AlexanderDGreat on 2012-09-02
@lenooh - you sir are simply amazing, your idea of using shotwell was most simple, efficient and very helpful.

Cheers for your answer! Thanks it worked like a charm. :)

---

