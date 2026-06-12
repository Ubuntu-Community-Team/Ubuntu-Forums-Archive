---
title: "Sharing a protected folder"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by Naddiseo on 2006-12-26
Hi, I reinstalled feisty on Sunday (dist-upgrade from dapper->edgy->feisty) and I had a shared folder before. I didn't wipe that harddrive because it was my backup drive, but now I've reinstalled it's protected (nobody:nogroup rw-r-r) and I can't sudo chmod or chown it... how do I get it shared again?

I get this error when trying to share it: "The configuration could not be loaded. You are not allowed to access the system configuration."

Any ideas?

---

### Post by Naddiseo on 2006-12-27
*bump*

Sorry for my impatience, but my dad has threatened to rip the HDD out of my computer and put it in his if I can't get the folder neworked...

*edit*
I think I've done it now. I set nobody's password and logged in as that user, then chowned the directory to my user, then chmod to 777 then just edited smb.conf and it worked... but I'm still getting the error about not being able to read the config file when I try to share via the nautilus right click menu.

---

