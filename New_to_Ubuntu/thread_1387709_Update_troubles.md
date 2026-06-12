---
title: "Update troubles"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by Alex De Duck on 2010-01-22
I had this little danger triangle up top, saying the system was outdated, so I ran over to administration and ran the update manager. Everything downloaded, but installing didn't work: 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

And the sudo dpkg --configure -a gave me this: 

dpkg: dissection error, in file '/var/lib/dpkg/updates/0000' near line 4 package 'xserver-xorg-input-vmmouse':
 EOF after field line `Installed-S'

(Note, this is a rough translation, it first said: dpkg: ontleedfout, in file '/var/lib/dpkg/updates/0000' near line 4 package 'xserver-xorg-input-vmmouse':
 EOF na veldnaam `Installed-S' because for some reason Ubuntu's half Dutch for me. I would prefer it to be all in English, but hey, I speak Dutch so there's no trouble there.)

Any ideas?

---

### Post by plucky on 2010-01-22
> **Alex De Duck said:**
> I had this little danger triangle up top, saying the system was outdated, so I ran over to administration and ran the update manager. Everything downloaded, but installing didn't work: 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

And the sudo dpkg --configure -a gave me this: 

dpkg: dissection error, in file '/var/lib/dpkg/updates/0000' near line 4 package 'xserver-xorg-input-vmmouse':
 EOF after field line `Installed-S'

(Note, this is a rough translation, it first said: dpkg: ontleedfout, in file '/var/lib/dpkg/updates/0000' near line 4 package 'xserver-xorg-input-vmmouse':
 EOF na veldnaam `Installed-S' because for some reason Ubuntu's half Dutch for me. I would prefer it to be all in English, but hey, I speak Dutch so there's no trouble there.)

Any ideas?

It seems you had a problem installing the xserver-xorg update.

From a terminal ```
cd /var/lib/dpkg/updates/
ls
``` ls will show you what files are there,you can remove all the files in that directory as it is temporary storage for the updater.

Then ```
sudo apt-get update
sudo apt-get upgrade
```


Good Luck

---

### Post by Alex De Duck on 2010-01-22
I get permission denied trying to delete these files... They're mosty 4 digit numbers going from 0000 to 0055 and tmp.i. And yes, I have administrative rights on the system.

---

### Post by plucky on 2010-01-22
> **Alex De Duck said:**
> I get permission denied trying to delete these files... They're mosty 4 digit numbers going from 0000 to 0055 and tmp.i. And yes, I have administrative rights on the system.

Use ```
sudo rm -i *
``` but make sure you are in the correct directory.The -i will allow interaction.

Good Luck

---

### Post by Alex De Duck on 2010-01-22
I think that did it, thanks!

---

