---
title: "Synaptic and apt-get not working (Hardy 8.04.2)"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by usnica on 2009-02-28
Today synaptic package manager and apt-get stopped working.  They will not install or remove any packages.  I tried installing blubuntu-look using apt-get to display the error messages and get this:

Fetched 2532kB in 26s (94.5kB/s)                                                                                                            
(Reading database ... 
dpkg: serious warning: files list file for package `x11-xkb-utils' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/blubuntu-gdm-theme_0.2-0ubuntu3_all.deb (--unpack):
 files list file for package `xscreensaver-data' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/blubuntu-gdm-theme_0.2-0ubuntu3_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]

No matter what I try to install or remove I get the 'x11-xkb-utils' and 'xscreensaver-data' messages.

I'm using Hardy 8.04.2 and this is the first problem since installation (8.04.02 installed clean from CD - checksums are OK). Any help is greatly appreciated.

---

### Post by swoll1980 on 2009-02-28
```
sudo apt-get --purge remove x11-xkb-utils
```
```
sudo apt-get --purge remove xscreensaver-data
```

See if that does the trick

---

### Post by Michael.Godawski on 2009-02-28
hi,

some related thoughts:


[LIST]
[*][http://ubuntuforums.org/showthread.php?t=591910](http://ubuntuforums.org/showthread.php?t=591910)
[*][https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189)
[/LIST]
perhaps you get some inspiration how to solve the issue :)

---

### Post by ScarySquirrel on 2009-02-28
Somewhere in the Synaptic Help Files it tells you how to clean up old dead programs, which may help.

---

### Post by usnica on 2009-02-28
Thanks to everyone for the help.  I tried removing xscreensaver-data.list and x11-kbd-utils.list without success... more dpkg errors.  I ended up booting into a live system, copying the two .list files from the live system onto a jump drive, rebooting into the installed system and replacing the bad files with those from the jump drive.  Then it had the same error on a different file; one of the theme files.

I let the system reboot a few times so fsck would run and ended up with pages of inode and other errors.  Looks like a corrupted file system - hope it's not the hardware (only four months old).  All was well with 8.04.1 - I will likely reinstall it and see what happens.

---

