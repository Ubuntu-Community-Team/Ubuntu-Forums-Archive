---
title: "[SOLVED] Package BackUp List"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by LeChacal on 2009-01-02
I am looking for a fast easy way to compile a list of all the packages that I personally have installed on my system without also having the packages that are part of the base install. I would like this so I can reinstall faster when I upgrade/change HDD around. I have looked around and haven't found a fast and efficient way of doing this. Thanks

---

### Post by adult swim on 2009-01-02
although this probably includes base install packages, if you tried this link below, when it came to a package that was already there, nothing would be done.
[http://www.savvyadmin.com/backup-and-restore-package-lists-in-ubuntu/](http://www.savvyadmin.com/backup-and-restore-package-lists-in-ubuntu/)

---

### Post by LeChacal on 2009-01-02
Well this wasn't exactly what I was looking for but the link gave me an idea. Can run:

```
sudo dpkg --get-selections > packages.txt
```

on my currents system then run it again on a clean install and then just run a filter between the two output files. I will still have to do some hand work because right now I am looking at going from 8.04 32bit to 8.10 64bit. 

I have a couple of days before my new hardware comes and I do my installs, so if anyone has a better idea please and thank you.

---

### Post by handydan918 on 2009-01-02
No need to diff the two. The package manager will simply bypass any request for a package that is already installed.

---

### Post by 2hot6ft2 on 2009-01-02
I think this is what you're looking for.
> **handydan918 said:**
> Okay, this should be in the wiki, or something. It's so simple, yet so powerful.


```
sudo dpkg --get-selections
```


```
sudo dpkg --get-selections > softwarelist
```
At this point in the proceedings, you hose your system and reinstall, and then...

```
dpkg --set-selections < softwarelist
```


```
apt-get dselect-upgrade
```

Enjoy.

EDIT: To Quote source

---

### Post by LeChacal on 2009-01-02
OK thank you handydan918 and 2hot6ft2 that looks like it will work and makes since. I didn't think/know that the package manager would just skip over the already installed packages, thought it would cause problems. But I have tried to manually install the same package twice and it wouldn't let me so.

---

### Post by sofasurfer on 2009-01-02
I use this proceedure frequently since I'm always glitching my system and clutering it up with crap. I concider using this method to reinstall, to be faster and easier that trying to find repair methods. Here is my documentation telling me how to perform the proceedure...

Taken from [http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)

Package list should have been created and saved to file and stored to backup disk by using this command...

dpkg --get-selections | grep -v deinstall > /media/disk/backup/installed-package-lists/NAME OF PACKAGE LIST

This creates the list and saves it to my backup disk.
To use this list to recreate the Linux system follow these steps...
1) Reinstall base system
2) Copy nessessary files from backup - entire network directory copied back to /etc/, sources.list copied back to etc/apt/, etc.
(In this step, sources.lst is the ONLY file I need to copy back into the system).
3) Open network config window and enter encryption key. You now have internet access.
4) sudo apt-get update
5) sudo apt-get dist-upgrade
6) dpkg â€“set-selections < /media/disk/backup/Documents/linux/installed-package-list (In the command "dpkg â€“set-selections" the wierd characters between 'dpkg' and 'set' should be "--". For some reason my text editor can not recognize "--" and creates the weird characters instead)
7) sudo apt-get install dselect
8) sudo dselect
9) when prompted, choose to install packages

Hope this helps you as much as it has helped me.

---

