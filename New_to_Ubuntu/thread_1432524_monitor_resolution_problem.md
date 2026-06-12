---
title: "monitor resolution problem"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by Bob Appleby on 2010-03-17
I playing with System/preferences/display and set the screen resolution one step lower (640x480) than it was automatically set by ubuntu 9.10 when first loaded. The control panel at  the top of the screen was "squashed" such that System is no longer available for resetting resolution. Is there another way of running System or must I reload 9.10?

---

### Post by m4nm4n on 2010-03-17
[edited for me being a dumbass]
:p

---

### Post by pj_kare on 2010-03-17
I just tried what I suggest below and it worked.

**Right click anywhere on desktop and select Create Launcher, leave as Type: Application and enter the following, though comment is not really needed.
Name: Display
Command: gnome-display-properties
Comment: Change screen resolution

Just delete launcher once you have finished with it.
Hope this works for you :D

---

### Post by Bob Appleby on 2010-03-18
Indeed, what you suggest brings up the display preferences window. After choosing the correct resolution, clicking on Apply or Close does nothing but change the size of the display preferences windows. Any ideas as to what is going on?

---

### Post by Bob Appleby on 2010-03-18
I had to rotate the screen 90 degrees to see the whole display properties at once. Then it worked perfectly. Thank you very much.

---

### Post by pj_kare on 2010-03-19
> **Bob Appleby said:**
> I had to rotate the screen 90 degrees to see the whole display properties at once. Then it worked perfectly. Thank you very much.

I didn't actually lower MY resolution when I tried what I suggested to you, and really had no idea what you would be able to see of the display preferences window once you had it open,  but I am glad you were able to work it out. :)

---

