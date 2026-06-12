---
title: "Saving settings before reinstall"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by emeraldgirl08 on 2009-07-28
Things have come to a head for me and my latest installation of Jaunty. During an install the power went out during a huge update (around 200mb). 

Things have been strange with my Jaunty since then. 

Whenever I log into Jaunty about five minutes (sometimes less) the comp just abruptly restarts. Real inconvenient when you're doing something important!

So I've decided to reinstall it. I would like to save settings but kind of wonder if I save the Home folder- would that save the damaged updates???

How do I even start to save settings and transfer that over to my new install? Or do I just start over now that the weathers awesome this morning???

---

### Post by chrisinspace on 2009-07-28
Well the first thing you can do if you want to install all of the same software is open Synaptic, click on the 'File', and choose 'Save Markings As'.  This will back up all of the selections you have made in Synaptic so you don't have to go through after your re-install and manually check off of those packages again.  One note of caution: if one of those packages caused your current problem, it would be installed again in your rebuilt machine.

The other thing you can do is back up your Home directory.  That process is documented pretty well in these forums and throughout the web.

---

### Post by diablo75 on 2009-07-28
The tip in the above post about the save markings in Synaptic... Wow, I never knew about that cool shortcut.  So that'd be a good way to save the packages (software) you have installed for quick re-install later.  Though a question that I have about that is if it is smart enough to also preserve your third party repos too, so if you had the restricted packages marked, they could be reinstalled easily.

Otherwise, backup .hidden folders from home for programs that you know you need backup settings for (.mozilla for example has bookmarks, passwords for firefox, etc.)

---

### Post by chrisinspace on 2009-07-28
Yeah...I'm not sure about 3rd party repos, but I would think if you add them in first, then restore your markings, it would pick everything up.  I haven't tried it, though.

Good advice in the .hidden folders.  Note: to see them, you have to show hidden files and folders.

---

### Post by drs305 on 2009-07-28
> **diablo75 said:**
> Though a question that I have about that is if it is smart enough to also preserve your third party repos too, so if you had the restricted packages marked, they could be reinstalled easily.


The packages will only include those registered with APT (synaptic, dpkg, apt-get, aptitude, debs installed by gdebi which are now listed in synaptic, etc). If third party repositories are enabled in the new install and they were registered in APT, they should be installed. The list won't include .tar.gz installations, etc.

The same is true if you save the list with the "dpkg --get-selections" command.

---

