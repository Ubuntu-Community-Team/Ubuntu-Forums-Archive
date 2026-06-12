---
title: "Wine, I just don't get it..."
date: 2010-11-19
forum: New to Ubuntu
---

### Post by jrenaldy on 2010-11-19
Ok, I almost hate to post this since I'm sure this is such a rookie issue.  For the life of me, I can't seem to figure out Wine.  I've installed it on my Ubuntu (10.10) laptop via the software tab and the GUI interface is working (?) perfectly.  Question is, what now?  I've tried to download a handful of Windows applications and keep getting error messages about .exe files not working.  Believe me, I've really tried to reseach this matter and I seem to get contradictory information.  I'd really appreciate any insight.  Oh and by the way, if this has anything to do with a root/su password, then I give up!

---

### Post by tacantara on 2010-11-19
I've used Wine before (although I prefer just running Windows XP in a virtual machine).  I find it is easiest to open .exe files by right-clicking them, and selecting Wine Compatibility Layer from the right-click menu.  Have you tried that approach yet?

---

### Post by Old Marcus on 2010-11-19
Have you tried right clicking on them and selecting Wine? For some reason the archive manager is listed as the default program to open them with, which is stupid.

---

### Post by yeats on 2010-11-19
>  I've tried to download a handful of Windows applications and keep getting error messages about .exe files not working.

What errors are you getting?  Ubuntu will probably try to open the files with Archive Manager.  Try downloading the .exe file, right clicking, and selecting to open with wine.  You can change your system preferences to open .exe files with wine (System -> Preferences -> Preferred Applications).

---

### Post by Zookalicious on 2010-11-19
> **jrenaldy said:**
> Ok,   Oh and by the way, if this has anything to do with a root/su password, then I give up!

Now, now, thats not the right approach at all :D the terminal is your friend and it is very easy to copy and paste commands that a helpful forum member gives you! (As long as you find out what they do before running them).

In order to run an .exe with wine (assuming wine is already installed), right-click on the .exe file in your downloads folder and select "Open with Wine Windows Program Loader". 

However, since WINE is not a windows emulator, not every application will work perfectly (or work at all) under WINE. I strongly advise you to check out this site [http://appdb.winehq.org/](http://appdb.winehq.org/)
and search to see if the programs you are trying to run have been tested successfully in Wine!

Feel free to contact me if you have any other questions, I maintain a couple apps in the Wine database so hopefully I can help out :)

---

### Post by jrenaldy on 2010-11-19
Thank you all!  I have tried the 'right-click' method and it doesn't give me an option for Wine.  And the whole terminal thing; yeah, not so good at that either.

---

### Post by Old Marcus on 2010-11-19
Right click, select 'open with other application' and look for wine there. If no luck, try reinstalling wine.

---

