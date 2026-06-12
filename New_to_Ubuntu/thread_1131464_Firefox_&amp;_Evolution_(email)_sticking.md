---
title: "Firefox &amp; Evolution (email) sticking"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-04-20
I want to uninstall both Firefox and Evolution.

I don't want to lose my configs/add-ons/plugins in FF and none of my emails or contacts in Evol.

Both cannot properly quit on command. Sometimes, I have to use the "force quit button" to get the apps closed.

Anybody know a thing about this?

---

### Post by antikristian on 2009-04-20
I'm pretty sure reinstalling them is not going to help, In most cases the problem lies in your config directory for the apps in your home folder, since both firefox and thunderbird binaries lie in their own safe little /usr/bin haven without beeing touched, and are most likely identical to every hardy users and the repositories version.

I'm putting my money on your plugins:P

To resolve it I would: 
close both applications 
in a terminal, do a 
 killall firefox 
 killall thunderbird
open my home folder 
show hidden folders
rename the ".mozilla" folder to something like ".mozilla.bak"

Restart firefox and thunderbird, see if the problems persist (don't worry, your emails are not gone, only moved to the .mozilla.bak folder)
Two things might happen:

**Option 1**
If the problem vanished, then shut down both programs, and start copying the email and files from your .mozilla.bak folder to the new .mozilla folder. Do not move the files, it's nice to have a backup during this process. Also, we are trying to eliminate the problem, so do not copy all files at once, Try the extensions first, then some of the subfolders for firefox and so on. If the problems reappear, rinse, repeat, remember to exclude the folder or file that caused the problem.

**Option 2**
If there is still a problem, then do a reinstall of firefox and thunderbird in synaptic or aptitude, then just delete the new .mozilla folder and copy .mozilla.bak and rename the copy to .mozilla

---

