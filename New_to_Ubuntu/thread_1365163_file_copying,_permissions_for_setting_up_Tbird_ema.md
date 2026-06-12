---
title: "file copying, permissions for setting up Tbird email"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by chuck4200 on 2009-12-26
I'm lost and need some quick help to set up my email accounts in this maze of trying to copy/port over my emails files, bookmarks, etc to setup Tbird 3.0.  I have the s/w installed, profile and one email account.  Formerly XP, Seamonkey, Firefox and Tbird veteran.  Have not had a lot of time to get Linux up and running - leaving 5:00 AM for week long trip to NYC.

My data files are on a separate partition FAT32 Laptop D drive.  No problem accessing this drive.  I want to copy these over and setup about a dozen email accounts.  Creating/recreating the account is not the problem, getting the older files and newsgroups is.  With Windows it's just a cut and paste routine.  This is turning into a nightmare for me being new to Linux.

I've tried a file synch program Conduit Syncronizer, but I can not see or access the profile directory to copy the files under /home/chuck.  The profile is set up under 
/home/chuck/.thunderbird/.....

Used this trick little Filesynch program in Windows for years to copy, back up, etc., but can not find a similar app in Linux, at least not yet.  How do I give permission to myself, the Admin, to manipulate these data files??

Thanks  :confused:

---

### Post by patchwork on 2009-12-26
First thing to try would be to temporarily change to root using the sudo command (assuming you're copying files through command line) i.e sudo cp /<old location> /<new location>

You may need to change ownership of the files,  This can be done quickly using the chown command:  sudo chown chuck /home/chuck/.thunderbird/<filename>

---

### Post by chuck4200 on 2009-12-26
I'm not savy enough for the command line to copy files, as they need to be placed in various directories that will be created with the new email account.  Command line would take forever.  Need to drag and drop in the file browser.

I don't understand why I do not already have r/w ownership of these data files in my /home directory though?

Using sudow chown ?  Would I have to do this for each file, or can I own the entire directory?  I have a couple hundred files to copy and paste, totaling about 400MB.  Thus the need to do this via GUI.

---

### Post by patchwork on 2009-12-26
From Desktop:

Places--Computer--chuck---Edit--Preferences--check the box "show hidden and back-up files"

This will allow you to view the files in the gui.  You still may need to change ownership, however.  Try it and see.

---

### Post by patchwork on 2009-12-26
I'm pretty new myself, but I believe you can change the ownership of the entire directory by using a wildcard, i.e sudo chown chuck /home/chuck/.thunderbird/*

Only try this if you are not able to copy your files in the gui for ownership reasons

---

### Post by chuck4200 on 2009-12-27
Patchwork,

Thanks - geesh - such a simple answer.  Been reading, searching and net searching for that simple answer for days.

Thanks

---

