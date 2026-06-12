---
title: "Saving programs to start upon new sessions"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by lckeeper1 on 2008-12-30
Hey all,

I've just installed the FutureLooks theme pack, complete with emerald and avant window navigator. I'm really enjoying the look and toying with it.

One problem that I'm running in to, however, is that everytime I go to the session manager to put both emerald and AVN in so they start during log-in, the commands are not saved.

Once I exit the session manager, it just comes up with the same programs, sans the ones I just put in.

I was just wondering if I'm missing something very basic here. Thanks a ton!

---

### Post by gettinoriginal on 2008-12-30
Try session manager options, automatically remember running applications

---

### Post by lckeeper1 on 2008-12-30
Thanks for the reply, but that doesn't work.

For some reason the session manager doesn't seem to pick up that both emerald and AVN are running. Also, the session manager doesn't seem to have all the options in the help file that it says it would.

I took screenshots of both. The system monitor clearly shows both emerald and AVN, but not the session manager.


Thanks for the help!

---

### Post by lckeeper1 on 2008-12-31
Bump.

Upgraded to 8.10, but still no luck.

Session manager does not remember what programs I put in at the start up menu after I hit the close button and goes back to the same ones, even if I remove it.

---

### Post by drs305 on 2008-12-31
If the apps you are trying to autostart appear in your Main Menu/Applications:

Once you have 'saved' your new apps in Sessions, you might try checking your startup folder to see if the apps appear in the list there. The settings are stored in ~/.config/autostart

If they don't appear, you could open nautilus to the ~/.config folder, and then open Applications,... to show the desired app. You can drag it's icon over to the ~/.config/autostart folder and create an entry there. Once you have done that, it should also show on the Sessions list. Watch the ~/.config/autostart folder as you close Sessions to see if the listing 'sticks'.  

If for some reason the apps appear in your menus but you aren't allowed to drag them to the autostart folder you may have a permission problem.

---

### Post by lckeeper1 on 2009-01-03
Thanks! This worked very well!

---

