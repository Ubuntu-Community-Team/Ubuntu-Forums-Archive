---
title: "Which directories should I backup to save all my settings?"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by KWhistle on 2009-06-29
I've tried a backup utility that only backed up the home directory, and that didn't save any of the program settings.  How do I back up all of those, e.g. Firefox, Firefox plug-ins, desktop settings, openoffice settings, etc.?   Are there certain directories that contain these, or are they all over the place, and there is no way to back them up in case I need a reinstall?

---

### Post by Paqman on 2009-06-29
All that stuff is in /home/username. Specifically it's in a bunch of hidden folders (such as .mozilla and .gconf), you can hit CTRL-H to see them in your file manager.

---

### Post by KWhistle on 2009-06-29
Thanks... Just checked, and looks like the backup utility that I used didn't work properly.  

Got one more question, though:  Is there a way to back up all the programs except for the OS itself, so that I wouldn't have to re-download and re-install all of them if I need to reformat?

---

### Post by mikechant on 2009-06-29
> Is there a way to back up all the programs except for the OS itself, so that I wouldn't have to re-download and re-install all of them if I need to reformat? 

'aptoncd' can create a backup repository from your system so you don't have to re-download - but you do have to reinstall.
See [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Or you could just back up the entire OS and installed apps - e.g. by making a partition image of the root partition by running 'partimage' or a similar utility from a Live CD. This would be the quickest way to restore if you had to reformat.

---

### Post by Paqman on 2009-06-29
> **KWhistle said:**
> Thanks... Just checked, and looks like the backup utility that I used didn't work properly.  

Got one more question, though:  Is there a way to back up all the programs except for the OS itself, so that I wouldn't have to re-download and re-install all of them if I need to reformat?

If you backed up the contents of your home, and the package manager's cache at /etc/apt/cache then you could reinstall everything without downloading again. Since you'd kept all your settings you wouldn't need to do any setup at all once they were reinstalled. You could make it even easier on yourself by [reinstalling everything in one step]("http://ubuntuforums.org/showthread.php?t=261366").

---

### Post by philinux on 2009-06-29
> **KWhistle said:**
> Thanks... Just checked, and looks like the backup utility that I used didn't work properly.  

Got one more question, though:  Is there a way to back up all the programs except for the OS itself, so that I wouldn't have to re-download and re-install all of them if I need to reformat?

Open synaptic. File>Save markings as> Choose a file name and location. Ensure tick box Save Full state is ticked. To restore use Read markings.

---

### Post by KWhistle on 2009-07-01
Thanks for all the advice!  Will try backing up home and etc, hopefully no more data/settings losses.

---

