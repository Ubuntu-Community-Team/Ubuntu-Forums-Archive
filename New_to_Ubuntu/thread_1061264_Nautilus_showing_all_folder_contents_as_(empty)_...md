---
title: "Nautilus showing all folder contents as (empty) ... but files are there!"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by andyburlow on 2009-02-05
I would like to get to the bottom of a really frustrating issue with Nautilus in that I cannot view the contents of any folder. I can view all folders and I can check the folder has contents through terminal but nothing I do with the setup of Nautilus can make it display the contents of the folders.
I can rtclk on a folder and see the folders properties and size of contents etc.

Im thinking back to when I installed Ubuntu and I dont think I have ever seen any files (through Nautilus). Other apps can list files with no problems.

I have searched and searched for answers (here and the web) but no similar problems - so it must be some odd setup/permissions issue I turned on.

Any advice gratefully recd.

---

### Post by handydan918 on 2009-02-05
That does seem al ittle weird. 
I'm not a gnome user, so you might want to wait for better advice, but I'd try ```
dpkg-reconfigure nautilus
```

---

### Post by Kellemora on 2009-02-05
Hi Andy

I just want to clarify something here first.
When you say through Nautilus, are you referring to Places/Computer/Filesystem OR Applications/Accessories/File Browser OR Terminal then typing the word Nautilus to bring up the file browser?????

All three should bring up the SAME file browser window, unless something is broken somewhere.

You could check List Columns to make sure ALL of the viewing features are not turned off, it's under Edit Preferences.

Also, there is one BUG I recently found in the 64 bit version of Ubuntu.  It refuses to display files that use illegal characters in file names.  Which accounted for like 150,000 of our missing files from when certain characters were allowed.  All 150,000 that won't appear under the 64 bit version, appear just fine under the 32 bit version.  Can be opened, edited and rewritten, even copied to a new folder USING the existing illegal characters in the file name!

Makes me WONDER why a character is considered illegal if you can use it, can save files with it from a program, but not directly, but you can ONLY view them in the 32 bit version, not the 64 bit version.  Nearly all of our question answer files, the question portions were saved using a question mark in the filename.  Been doing it that way since Windows 3.0, through XP and in Ubuntu, until we got a new 64 bit computer the other day.  Now suddenly we can't see ANY question files from the Server.

So that's something else to check too, that you are using Filenames Legal for use in Ubuntu!

TTUL
Gary

---

### Post by andyburlow on 2009-02-06
**Sorted!**
Thanks Gary for getting me to look in Edit / Preferences

Lurking at the bottom I noticed the option - Tree View Defaults and there was the option to 'Show only folders' with a big tick in it!
 
Looks like I need to spend some time having a clean up - loads of files have appeared!

Thanks for your help.

---

### Post by Kellemora on 2009-02-06
Hi Andy

Actually that SHOULD BE CHECKED to prevent files from appearing in your directory tree on the LEFT PANEL/Frame.

However, I too have noticed that if you CLOSE the Left Panel that sometimes the Main Screen takes on the characteristics of the TREE and the files don't show!

Nautilus does have a few bugs in it yet!

TTUL
Gary

---

