---
title: "Issues with firefox and gnome"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by arnicainthemembrane on 2009-09-11
Basically, Firefox has deleted / forgotten my (hundreds of) bookmarks, and when I try to log onto gmail, etc. nothing happens when I hit the "send" button.

Also, when I try to log out of gnome and shut down the computer, hitting the "running man" button causes the shortcut icons on my desktop to vanish, then I have to turn off the computer manually.

I downloaded Chromium and it crashes frequently, but this is probably an issue with Chromium itself.

I did remove the hard drive at one time, when the computer was powered down, to insert another hard drive and test out an Ubuntu 8.10 disk (which didn't work because the disc was cracked).

My present solution to the whole problem is to burn an Ubuntu 9 CD off the ubuntu site then boot up my computer with the disc in and do a fresh install.

So, finally, my question is, will I lose data if I do this? Should I get an external USB drive and put my home file on it, then do a fresh reboot (Ubuntu v.9 from disc), eliminating any issues presently on the computer? Or is there any harm in simply rebooting? Or are these common problems I can probably fix myself?

---

### Post by lovinglinux on 2009-09-11
I don't know if you have a problem that requires re-installing, but let's try a very simple thing first.

Close Firefox, then go to "Applications >> Accessories >> Terminal" to open a terminal window. Then paste this code into it and hit enter:

```
firefox -P
```

This will launch Firefox Profile Manager. Click the "Create Profile" button, then "Next", then replace "Defaul User" with "test" and click "Finish". This will create a new profile named "test" (you can use any other name if you want). Untick the option "Don't ask at startup", so the profile manager will popup every time, allowing you to choose a profile to start with. The "test" profile should be already selected, so click "Start Firefox". Now go to Gmail and try to login. If you have success, then it probably was corrupted profile causing the problem.

You can then try to pinpoint the problem in the profile or simply import the bookmarks backups to the new one. Firefox makes regular bookmark backups automatically. For instructions on how to do that, visit the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

About your icons missing, I have no idea, but someone will probably find a fix for you.

Nevertheless, if you want to re-install Ubuntu, I recommend learning about [separate home partitions](http://www.psychocats.net/ubuntu/separatehome). It will save you from a lot of trouble in the future.

---

### Post by arnicainthemembrane on 2009-09-11
thanks!!!!!!!!!!!!!!!!!!

---

