---
title: "deleting config files and unused packages"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by thomz92 on 2009-03-13
hi! is it safe to delete unneeded packages or config files through synaptic? or has anyone had problems when doing so?

---

### Post by aesis05401 on 2009-03-13
'Safe' depends entirely on how you are identifying files as disposable.  

Try 'man apt-get' and check out clean, autoclean, autoremove, purge etc..  

Will these accomplish your task?  If so, clean, autoclean and autoremove are pretty safe in my experience.  If you are manually picking files to remove it might be smarter to know what each one is before blowing them away.

---

### Post by thomz92 on 2009-03-13
"'Safe' depends entirely on how you are identifying files as disposable."

srry, i dont understand what you mean by this. I'm asking if the packages really are unneeded if synaptic says they are. Like, i wont accidentally delete add-ons or packages that i need or something.

---

### Post by RedSingularity on 2009-03-13
When you choose "completely remove" an application synaptic will remove that app and all the files needed to run that particular app.  It wont delete files that are used by any other software.

---

### Post by cairnzi on 2009-03-13
sudo apt-get autoclean
sudo apt-get autoremove
sudo deborphan | xargs sudo apt-get -y remove --purge


these are all safe commands to use to clear all un-needed files, you can also use "localepurge" but be carefull when setting it up.

---

### Post by aesis05401 on 2009-03-13
A little more info might help figure out how to completely answer your question.  Of course, maybe I am just not understanding what you are asking.  

First off, forgive me if you know all this, but most of the things listed by Synaptic aren't actually on your computer, they are packages available from the repositories listed in /etc/apt/sources.list.  You can type 'less /etc/apt/sources.list' from a terminal to see a list of repositories you are currently polling. 

So any package you see in Synaptic that does not give you the 'Mark for removal' or 'Mark for complete removal' option when you click it is not actually on your machine.  

You will find pieces of things that can safely be removed in the Status/Not Installed (residual config) and Not Installed sections of Synaptic.  Not Installed (residual config) is a list of config files that remain after the packages that required them were removed and they should be removable without problem unless you are hoping to reinstall the package with your original config files.  

The Not Installed section will list all sorts of programs that you are not running, most of which were never even downloaded to your machine.  I recently downloaded, installed, then uninstalled 3dchess, and I see that clicking 3dchess in the Not Installed section gives me the option to completely remove the packages because they are still sitting on my machine.  This would be the equivalent of running 'sudo apt-get remove 3dchess" from a command line.  All the entries on either side of 3dchess, though, were not on my machine to begin with, so there is nothing to remove.  

Anything marked as installed should probably be left installed even if the properties screen in Synaptic lists the package as 'optional.'  Plenty of optional packages are used to deliver bells and whistles of various sorts.

Long story short, anything that Synaptic is listing as both Not Installed*, and gives the option for 'Mark for Complete Removal' should be safe to remove.

---

### Post by thomz92 on 2009-03-14
ok! i'll try those ideas. thanks for the help!

---

