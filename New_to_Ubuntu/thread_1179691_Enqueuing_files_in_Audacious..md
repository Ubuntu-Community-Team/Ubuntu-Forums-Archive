---
title: "Enqueuing files in Audacious."
date: 2009-06-05
forum: New to Ubuntu
---

### Post by melrokz on 2009-06-05
How to enqueue files in audacious from nautilus? (similar to the winamp feature enqueue) This would be very useful.

---

### Post by mc4man on 2009-06-05
The simplest way would be to use nautilus actions (r. click on a file, folder or m3u.
There are 3 decent actions in audacious, all can be used on files and folders.

you could also create a userapp.desktop with a Exec= following the same idea as the nautilus actions. (same command without the %M ) For example a .desktop named 'Enqueue in aud' with an Exec= of audacious -e

Nautilus actions are a tiny bit easier to set up than userapp.desktops

nautilus actions for audacious and amarok

[http://ubuntuforums.org/showthread.php?p=5287915#post5287915](http://ubuntuforums.org/showthread.php?p=5287915#post5287915)
(aud in posts prev. to linked

Note: for some reason back then I was putting part of the command in the 'parameters', they can go into the command line as well, maybe better there. (see this screen for difference in "queue in aud"

For conditions use "both"

Nautilus actions require you to restart x (Ctrl+Alt+backspace) to set


Edit The 3 most useful commands for aud (descriptions in screen shot tooltips in linked thread

Load to Audacious 
  
audacious -e -p   

New in Audacious  
 
audacious -E -p

Enqueue in Audacious  

audacious -e

---

