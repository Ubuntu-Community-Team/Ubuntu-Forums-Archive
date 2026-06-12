---
title: "HELP! Screen rotation disaster, need this computer working again!"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by kanati on 2009-03-21
I already posted this in the General Help thread, but that doesn't seem to be working, so here it is again.

I rotated my screen to the left using the Screen Resolution dialog.  The system froze and I used CTRL-ALT-BACKSPACE to get back to the login screen.  Now when I log in none of the UI elements load, all I get is my desktop background (still rotated).  I'm looking at my xorg.conf file from the failsafe terminal, but I can't find any option for screen rotation. How do I get the screen to rotate back to normal through the terminal?

Thanks!

---

### Post by The Cog on 2009-03-21
Yes, that rotate option is a real train-wreck. I don't understand why they leave such a nasty booby-trap in there. The setting will be stored somewhere in either ~/.gnome or ~/gnome2 I don't know which. You could rename these from the failsafe terminal and the reboot. Gnome will create new copies with default settings. Then you can seta bout figuring where the offending setting is and restoring all the other app settngs from the renamed directories. Or just live with having to configure all your gnome preferences again.

---

### Post by kanati on 2009-03-23
Thanks for the reply.

I managed to solve this one... somehow.  I put an option into my xorg.conf to rotate the screen counterclockwise (based on the kindergarten logic that two wrongs make a right).  I then restarted the system with an external monitor plugged in, and now all is well.  Any idea which of those two solved the problem?

Thanks again,

---

