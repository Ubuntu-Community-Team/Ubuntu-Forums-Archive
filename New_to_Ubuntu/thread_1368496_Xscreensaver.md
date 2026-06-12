---
title: "Xscreensaver"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by jnmjr on 2009-12-30
Ok guys another small annoyance, I installed Xscreensaver from Synaptic, nice to have all those screensavers. First, time I opened the scsavers config window I got this message ,

Gnome-screensaver deamon running do you wish to stop it? OK
Xscreensaver deamon not running on display "0.0" Do you wish to start it? OK

All looked fine, so I deleted Gnome-screensaver so it wouldn't interfere with Xscrsaver, I rebooted to make sure all was well and here's the problem:
Xscrsaver doesn't start automatically, I get this message:
Xscreensaver deamon not running on display "0.0" Do you wish to start it? 
So I have to start it manually in order to get to work. How do I get it to start at start-up?

I googled it but most posts on this issue are very old. Any one have a solution?. THX.

---

### Post by 4Orbs on 2009-12-30
Go to the System > Preferences > Session And Startup menu, click on the startup apps tab at the top, add xscreensaver to the list of auto-start applications and it will start its daemon every bootup thereafter.

---

### Post by jnmjr on 2009-12-31
I see your point but which file, there're several "xscreensaver" in different locations. can you point me in the right direction. THX.

---

### Post by 4Orbs on 2009-12-31
No, you don't go to the screensaver settings. You need to open the session manager from the System menu (maybe it's labeled "Autostarted Applications" or "Startup Apps"... I don't have Gnome installed at the moment and don't recall the actual title of the menu header). Anyway you add the word xscreensaver among the list of auto-started applications. If you can't find it in the System > Preferences menu, maybe someone with Gnome currently installed will point you to the correct menu item.

---

### Post by jnmjr on 2009-12-31
THX 4Orbs, I understood what you meant but to add a filename to start-up you have to input a file path or command, my question was if you knew which one ,but I guess I wasn't clear in my previous post, what I did was search for the executable which I finally found in
usr/bin, it took a bit of time but it works fine. THX again for pointing me in the right direction.

---

