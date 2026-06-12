---
title: "Don't understand TableEdit install instructions"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by desert dweller on 2011-04-21
I want to install a guitar tab program called TableEdit. There isn't a Linux version. So it has to run under Wine. The instructions for installing include this:

Installs and runs pretty much perfectly. Still need the specially compiled tef260.ttf font. Still need to do the comctl32.dll override, plus now need to rename the /drive_C/windows/winsx folder to eliminate it in order to get the override to load (or program won't start.)

I don't know what this means or how to do it. What do I need to do to accomplish these tasks?

I'm running Ubuntu 10.10

---

### Post by Mark Phelps on 2011-04-21
> **desert dweller said:**
> Still need the specially compiled tef260.ttf font.
Which means ... you will have to locate and download this file.  Then, you will have to add this font to the set Windows understands.  Don't know how to do that -- you should ask on the Wine subforum.

>  Still need to do the comctl32.dll override,
Which means ...  you will have to locate and download this file, and replace the current file with this one.

>  plus now need to rename the /drive_C/windows/winsx folder to eliminate it in order to get the override to load (or program won't start.)
Which means ... you will have to use the command line or a file manager to rename the folder.  Note: This is generally a BAD idea as Windows needs to have that folder available to do Windows Updates, but since you don't actually DO those updates in Linux with Wine, it's probably OK.

---

### Post by desert dweller on 2011-04-21
Thanks for the help! That makes everything a lot more understandable.

---

