---
title: "Resolution problem - monitors no longer auto-detected?"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by Cosmogirl on 2010-01-01
We turned on our computer (Ubuntu 9.10 installed) this morning to find a black screen.  After a little messing around we got two resolutions available: 640 x 80 or 320 x 24.  Normally we should have 1024 x 768.  Our graphics card is an nVidia G73 (or GeForce 7300).  Going to System > Preferences > Display gives an error message: "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?". After clicking on "no", a new window comes up marked "Monitor unknown" among other things, & only allowing us the choice of the two resolutions mentioned above.  Clicking on the button "Detect monitor" in this window changes nothing.  The resolution was working fine yesterday, I can only conclude that maybe a file we installed via Update Manager yesterday has screwed things up.  Do we have to reconfigure Xorg or is there a simpler solution?  We'd appreciate your help.

---

### Post by Joeb454 on 2010-01-01
Thread Moved to Absolute Beginner Talk :)

---

### Post by Ferretti on 2010-01-01
Have you tried going to System > Administration > Hardware Drivers to see if the driver was lost?

---

### Post by ST3ALTHPSYCH0 on 2010-01-01
That error you got is b/c afteryou install the Nvidia drivers you need to use the Nvidia X config tool (System>administration>Nvida-somthing). Try that and see if it happens to give you any further options.

---

### Post by Cosmogirl on 2010-01-02
Thanks for your replies.  In fact the problem solved itself!  Turned on the computer again today and maximum resolution has been restored.  No idea what went wrong there!  Next time I have a problem I'll try rebooting before doing anything else...

---

