---
title: "video mode not supported"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by jonaldo on 2009-03-30
Hi guys i am new to Ubuntu and seem to have hit a problem already!!

I had to install the 8.10 alternate version because of some graphics issue. Everything is fine until i get to the Ubuntu logo screen with the loading bar underneath. Once the loading bar is full, the monitor loses its signal and displays the message 'video mode is not supported'. 

Can anyone help me with this? The graphics card is a radeon rs9600. :confused:

---

### Post by willz06jw on 2009-04-22
It's a problem with your Xorg settings.  You should check your Xorg.0.log (located at /var/log/Xorg.0.log) for errors.  

In threory there shouldn't be any video problems right after you install.  What type of monitor are you using?  If the Xorg.0.log doesn't help I would recommend reporting the error to launchpad.  If you do this remember to include all of the hardware specs in quesion.

---

