---
title: "Default... everything"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by J697 on 2011-01-23
I made a few mistakes when I first installed Ubuntu, then I installed it again. Well I have been on that second install for about a few months now. I have to much data to lose. So I cannot install it again. I have to go with this version that I have. I need to default the whole permission setup. I gave a bunch of chowns and chmods where they maybe shouldn't have been. As security means a big deal to me. I really want my computer to be 100% safe. How can I restore the default permissions for every file?

---

### Post by switch10 on 2011-01-23
Restore from the backup that you made?  

Short of that, I'm pretty sure there is no way to restore default permissions of files.  

It may be time for another backup/reinstall.

---

### Post by walt.smith1960 on 2011-01-23
If your data is in the standard places,  /home/whatever, it isn't that hard to backup your data and reinstall.  This is why those more knowledgable than I recommend a separate home partition--it's possible to delete and reinstall the O.S. without touching data or settings.

---

### Post by diablo75 on 2011-01-23
If I were you, I would backup the contents of your entire /home/* in a tar.gz and copy that to an external hard drive.  When you reinstall, all you'll have to do is copy all the data in that archive back into your new /home folder.  All your files, user preferences and application specific data (such as Firefox bookmarks and passwords, email caches in Evolution or Thunderbird, and pretty much any other app that stores user account specific data).  Programs like WINE and Virtualbox also store their little virtual machines in hidden folders within your home folder (Use CTRL-H to reveal these if you're curious).

When you go to install a new system, use manual partitioning to create a partition for /, another for /home and another for your swap.  That way, if you ever have to do this again, you just reinstall by overwriting the / partition (formatting first) and using the existing /home partition as is, being careful to make sure it will not be formatted during install.  Setup your new user account to have the same name as your old account and the two will match up.  The first time you login to your account after reinstall, your desktop wall paper, desktop icons, and home folder will be just as you left it.  You'll just have to reinstall software you had already installed, but that's not that difficult to do; just a little time consuming.

---

