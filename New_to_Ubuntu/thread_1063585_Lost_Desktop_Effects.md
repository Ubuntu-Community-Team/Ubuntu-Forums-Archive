---
title: "Lost Desktop Effects"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by mpl34 on 2009-02-08
Hey,

I was messing around trying to increase the performance of my system and decided that ending plasma may be a good choice, it wasn't. I lost the title bar on all my windows losing the ability to move, minimize, maximize, and close my windows with a simple click of the mouse.

However i fixed this problem but have now lost all my desktop effects, i fixed the title bar problem with a recovery boot and then selecting the option to fix x server.

This is beginning to irritate me as i really enjoyed my alt-tab feature and an assortment of others including trasparency. 

Any help would be much appreciated.

---

### Post by GCoffee on 2009-02-08
I take it you have the compiz effects manager installed? (something like CCSM, i will check when i boot into ubuntu) if so you should be able to add all your effects again through it... unless  you are using something else to manage your effects..

GC.

---

### Post by txcrackers on 2009-02-08
When in doubt, just log out and go to a console (CTRL+ALT+F1). Login and delete the $HOME/.kde directory. This will have the unfortunate effect of completely removing all of your **desktop** customizations and application settings (e.g. don't do this if you've got personalized data you're not willing to lose).

---

### Post by mpl34 on 2009-02-08
Yes i do have compiz effects manager installed however i did fix the problem by selecting the option under session manager that said Start new session on boot. I also changed by windows manager from compiz to kwin and had to modify my video driver as fix X server changed it bac to the default nv driver.

Thanks for the help tho

---

