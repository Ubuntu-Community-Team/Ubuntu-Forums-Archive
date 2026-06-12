---
title: "Problem with resolution"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by davidstri on 2009-06-10
For some reason when I log into my account and try to change the
screen resolution through system > preferences > display, I only get
four options for the resolution, ranging from 320x240 to 800x600 and
two options for refresh rate, ranging from 56 Hz to 60 Hz , but when I
switch to a different user, the screen shrinks and when I go to system
> preferences > display,I see that I get thirty options for the
resolution, ranging from 320x175 to 1600x1200, and five options for
the refresh rate, ranging from 85 Hz to 60 Hz.  So the resolution
switched from 800x600 to 1600x1200 and refresh rate from 56 Hz to 85
Hz.  How do I set the default resolution and refresh rate so the
resolution stays at a good resolution and doesn't change when I 
switch users?

---

### Post by Het Irv on 2009-06-10
the permissions are the same for both users? Is there anything different between the two other than the username?

---

### Post by davidstri on 2009-06-10
My permission are(y for checked and n for un-checked)
[y] Access external storage device automatically
[y] Administer the system
[n] Capture video from TV or Webcams, and use 3d acceleration
[y]Configure printers
[n]Connect to Internet using modem
[n]Connect to wireless and ethernet networks(wich is weird because I'm 
   using an ethernet connection to write this reply)   
[y] Moniter system logs
[n] Mount user-space filesystems(FUSE)
[n] Send and receive faxes
[y] Share files with local network
[n] Use audio devices
[y] Use CD-ROM drives
[y] User modems
[n] User tape drives

and all of the permissions for the other user are unchecked.
I saw this in System > User and Groups > Properties

BTW, If I log into the other user first and then log into my user, the same thing happens to my resolution, the resolution is raised to 1600x1200.

---

### Post by Chris Edgell on 2009-06-10
I have been adjusting my resolution for MONTHS by Ctrl+ and Ctrl-

I'm not offering this as a solution but it does work.

---

### Post by davidstri on 2009-06-10
Cool, thanks for the tip, but Ctrl+ and - just changes the font and what's inside of the internet window, but I want to change the internet window and everything else, including stuff opened outside of the internet, but thanks again for the tip.

---

### Post by davidstri on 2009-12-21
I found out what was causing the blown up resolution. After reinstalling Ubuntu onto my computer a couple times trying to discover what was wrong (see here > [http://ubuntuforums.org/showthread.php?t=1338591](http://ubuntuforums.org/showthread.php?t=1338591)), I found out when I changed the resolution from the display settings, after a reboot, the resolution would blow up . In karmic koala, it doesn't even let you log-in after changing the resolution. The problem must be with my monitor and not with Ubuntu. Problem semi-solved, there is no solution, hehe.

---

