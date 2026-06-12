---
title: "Firefox will not run in my user profile after installing lucid"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by nightshade209 on 2010-05-15
I installed Lucid yesterday. I had copied the entire home folder (including all the hidden configuration folders) onto an external hard disk. And did a fresh install of lucid. After the installation, i copied the backed-up home folder onto my disk, choosing to merge folders whenever there were identically named folders. Now, Firefox refuses to start in my user profile, but works perfectly well in the other three profiles on the PC. Whenever i try to launch firefox, it displays a dialog saying "Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system." Rebooting did not help. Please tell me how to get rid of this problem.

---

### Post by mbzn on 2010-05-15
try "sudo killall firefox"

---

### Post by nightshade209 on 2010-05-15
"killall firefox" does not help.It says "firefox: process not found". Also, firefox does not show up in either System Monitor or top.

---

### Post by BandD on 2010-05-15
try this:

back up your ~/.mozilla folder.  Open nautilus, go to your home folder, hit ctrl+h (to view hidden files) and right click on .mozilla and selected "rename".  Rename the folder to .backup-mozilla.  

Then try to start firefox.

See if that works (you shouldn't have your bookmarks or anyhting like that when it starts, it'll be a "virgin" firefox)

---

### Post by marshmallow1304 on 2010-05-15
Maybe Firefox was running when you copied the profile to the backup disk?

[http://www.mattcutts.com/blog/how-to-fix-firefox-is-already-running-error/](http://www.mattcutts.com/blog/how-to-fix-firefox-is-already-running-error/)

Basically, delete ~/.mozilla/firefox/<profile>/lock and ~/.mozilla/firefox/<profile>/.parentlock

---

### Post by BandD on 2010-05-15
try marshmallow1304's post first.  It gets at the same thing I was trying to do, but I didn't know what files track firefox's last session.  The "virgin" firefox that I proposed would have been more a "proof of concept" and would then require quite a bit of work to get the bookmarks and what not transfered over.  

If marshmallow1304's fix works, then life is good.  If it doesn't try what I suggested and let us know if that works.

---

### Post by nightshade209 on 2010-05-15
I tried marshmallow1304's suggestion, but although i deleted the .parentlock file, i could not find one called lock, and the problem persisted. However, in the link marshmallow1304 has given, there is another link to create a new firefox profile. I followed those instructions and firefox is working well with the new profile. So problem solved, thanks!:)

---

### Post by lovinglinux on 2010-05-15
> **BandD said:**
> The "virgin" firefox that I proposed would have been more a "proof of concept" and would then require quite a bit of work to get the bookmarks and what not transfered over. 

Yes, that's why I recommend that only as last resort, but a lot of people in these forums recommend that as the first thing when an user has a problem with Firefox. I really don't like this, since is not the best solution for the user.

My approach is to first create a new profile with the profile manager, then test and try to pinpoint the culprit. If nothing works, then rename the profile folder. See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

> **nightshade209 said:**
> I tried marshmallow1304's suggestion, but although i deleted the .parentlock file, i could not find one called lock, and the problem persisted. However, in the link marshmallow1304 has given, there is another link to create a new firefox profile. I followed those instructions and firefox is working well with the new profile. So problem solved, thanks!:)

You can move most of files from the old profile into the new one. If you want to do that, in order to restore passwords, extensions, settings and so on, then check each file function [here](http://kb.mozillazine.org/Profile_folder_-_Firefox#Files).

---

