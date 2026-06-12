---
title: "Gnome menu crashed"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-04-04
Hi all,
 I successfully installed Gnomenu, which is a very cool thing. I then installed a theme, and after installing it, I think it crashed. So, I still have it as a selection in the panel add-ons, but it won't launch. I tried deleting it from my usr file, but it won't let me, and re-installing it did not seem to fix it. What gives?
Thanks

---

### Post by jimreynold2nd on 2009-04-04
I never actually used GnoMenu, but I believe if you didn't have to enter your password when you install/change theme, then the setting/themes are going to be stored in your home directory (basically the password is needed to write anything outside of your home directory).

So I think what you should do is (backup)delete the .gnomenu (or .GnoMenu, or something similarly named that you can recognize that it's a setting directory for gnomenu) in your home directory and restart gnome/gnomenu. Btw, that dir is probably hidden.

---

