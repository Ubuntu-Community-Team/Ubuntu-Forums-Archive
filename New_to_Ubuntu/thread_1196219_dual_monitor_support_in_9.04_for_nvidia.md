---
title: "dual monitor support in 9.04 for nvidia"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by pablolie on 2009-06-24
i am using the nvidia 180 driver with ubuntu 9.04 desktop, plain vanilla other than that. i have 2 monitors and would like ubuntu to use them, but can't set them up via the nvidia x server settings application.

i try to configure them both as separate x screens, but when i try to save the config file so i can restart the x server, it tells me 

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'

what is wrong there? what are the drawbacks of twinview should i not be able to fix this?

---

### Post by fooman on 2009-06-24
i use separate x-screen...not sure about twinview.

to setup dual screens,  you will need to run nvidia-settings *as root*.

run this command in a terminal:

```
gksu nvidia-settings
```

configure your monitors, apply,  then save to x configuration file.

hope that helps.

---

### Post by pablolie on 2009-06-24
> **fooman said:**
> i use separate x-screen...not sure about twinview.

to setup dual screens,  you will need to run nvidia-settings *as root*.

run this command in a terminal:

```
gksu nvidia-settings
```

configure your monitors, apply,  then save to x configuration file.

hope that helps.

thanks, it helped some - at least now i can run both monitors. however it seems buggy. the system will not remember the fact i configure one screen to be to the left of the other (it inverts the sequence), nor does it allow me to open separate, and Firefox will hang if I try to open another instance of it on the second x-screen...

---

### Post by sdbrogan on 2009-06-25
Firefox needs a separate profile for each X screen : start firefox (from the terminal or make a launcher) using this option :

firefox -P

You'll get a menu asking which profile to use; create a new one, use that, & you're off

---

### Post by lazyart on 2009-06-25
Use TwinView, put the screens where you want them (X Server Display Configuration->set position to Aboslute if screens are not the same resolution, or use Left Of, Right Of if they are).

Hit Apply, then Save to X Configuration File (you did run nvidia-settings as root, right?)

They will stick that way, and you can float windows from one display to the other.  And it looks fun when you rotate the cube. :)

---

### Post by warlock_handler on 2009-06-25
hi guys... any idea how to get a task bar or new panel to your secondary monitor...I have 2 monitors.. and i have setup twinview on them... and on is righoff the primary one... any idea how to get a task bar in the second monitor... i have so many windows open... its hard with only one task bar on one monitor... when i used 8.10 i could just add new panel.. and drag and drop it to the second monitor....
help guys help :D

---

### Post by pablolie on 2009-06-25
thanks a lot everybody -

by combining diferent pieces of advice from the suggestions above i now have exactly what i was looking for - hurrah! ;-)

in the end i went for twinview, seemed easier to tweak and more stable. but that may just be my impression given what i needed.

cheers!

---

