---
title: "Reformating to Jaunty and Firefox Migration"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by TadeoDiaz on 2009-05-12
So I am getting ready to reformat my laptop to Jaunty (running intrepid right now) but I want to be able to keep my firefox settings (saved passwords, preferences, etc). Can I just backup the .mozilla and then replace the folder in the new installation with the old one?

Or even better, is there a way to export all your settings to a file that can then be applied to the new installation? 

Thanks in advanced for the help

---

### Post by cariboo on 2009-05-13
I usually backup all the files and directories in my home directory, even though I have a seperate home partition before doing a clean install.

---

### Post by lavinog on 2009-05-13
Clear your cache before backing up though...no point in backing up cache data.
Also be careful of backing up your home folder...I ran into a recursive issue using rsync because of the gvfs mounted my backup drive to the desktop. Make sure you use a one filesystem option so it doesn't backup your backup.
This is accomplished with the -x switch for rsync or cp.

---

### Post by lovinglinux on 2009-05-13
> **TadeoDiaz said:**
> Can I just backup the .mozilla and then replace the folder in the new installation with the old one?

Yes.

> **TadeoDiaz said:**
> Or even better, is there a way to export all your settings to a file that can then be applied to the new installation?

Yes. Use [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) extension to create a complete backup then restore it into the new installation.

---

### Post by presence1960 on 2009-05-13
> **TadeoDiaz said:**
> So I am getting ready to reformat my laptop to Jaunty (running intrepid right now) but I want to be able to keep my firefox settings (saved passwords, preferences, etc). Can I just backup the .mozilla and then replace the folder in the new installation with the old one?

Or even better, is there a way to export all your settings to a file that can then be applied to the new installation? 

Thanks in advanced for the help

Backup your profile folder for Firefox located at /home/.mozilla/firefox (see screenshot). After install of Ubuntu place this back in same location. Then in terminal run ```
firefox -profilemanager
``` This will open profilemanager. Click Create or Add to make a new profile. Follow the prompts and choose the profile folder you just put back in the /home/.mozilla/firefox directory. After adding this it is safe to delete the other profile created by Firefox during the install by using profilemanager. **But do not delete it prior to adding your profile that you want!** When you are done and start FF all your settings will be as they were prior (bookmarks, password manager, extensions & themes, etc). I have been using the same profile folder for years now.

P.S. you can use the same process for thunderbird if you use it. Profile folder is located at /home/.mozilla-thunderbird.

---

