---
title: "Ubuntu Loading screen Karmic 9.10"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by erilidon on 2009-12-13
How would I go about changing the loading screen in Karmic (I have attached a screen shot of the window I am talking about.)

I have already changed my login window background and theme using gdm.. just not sure how to change the loading screens background. 

Thanks

---

### Post by NCLI on 2009-12-13
That's fairly easy. Just run the command "gksudo nautilus /usr/share/images/xsplash", then replace the image with the filename closest to your screen resolution with the image you want. Just make sure to rename it to have exactly the same name as the image it replaces.

Here's [a thread on the subject]("http://ubuntuforums.org/showthread.php?t=1338401").

---

### Post by erilidon on 2009-12-13
Thanks, thats good to know. What I ended up doing was renaming /usr/bin/xsplash to keep it from loading at all.

---

