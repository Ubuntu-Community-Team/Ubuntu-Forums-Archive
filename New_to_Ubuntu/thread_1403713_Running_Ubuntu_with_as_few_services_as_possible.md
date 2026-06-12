---
title: "Running Ubuntu with as few services as possible"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by alterKrieg on 2010-02-10
The goal here is to use a repurposed laptop as a viewer or console of sorts using rdesktop.  To do this I need the fewest number of resources running as possible because available RAM on this machine is pretty low.  

I've had success by logging in through the failsafe terminal to launch rdesktop and so I'm wondering if there is a way to define a separate user who will launch into something as lean as the failsafe terminal when launched, and then automatically run a number of commands to start vncserver and a specified rdesktop connection.

I'd prefer to setup a different user account to do so, because then I can maintain all the settings on my main user login.  This way, if there are major changes I need to make, or if I just want to play around more with linux, I can do so with the main login while the secondary one is the viewer.

I'm not sure the best way to set this up.  Or really, even where to begin.

Any ideas?

---

### Post by AntonioPT on 2010-02-10
You shouldn't do this with a "regular" install of Ubuntu. You should get an alternate CD and install a command-line system from there. Then just install the packages you need. If you need any help in what packages to install, etc... just PM me.

---

