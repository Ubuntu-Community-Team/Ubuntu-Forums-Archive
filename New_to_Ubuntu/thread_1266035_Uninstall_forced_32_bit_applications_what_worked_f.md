---
title: "Uninstall forced 32 bit applications: what worked for me"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by Mander on 2009-09-14
I thought I'd document this rather convoluted way of uninstalling a 32 bit package on a 64 bit system in case it helps someone else.  I'm pretty much a newbie so I may have done something wrong, but this seems to have done the trick.

Background:  I was having trouble with OpenOffice 3.1 so I thought I'd try installing 2.4 to see if it helped.  When I went looking to download a copy of the older version, the only one I could find was 32 bit (I found the 64 bit version after the fact).  So, I installed it using the 

```
dpkg -i --force-architecture *.deb
``` 

command in the appropriate folder.  This mostly worked but OpenOffice couldn't find the JRE so the database program would not run.  I tried various things but in the end decided to uninstall.

In trying to uninstall it I found that simply running dpkg -r openoffice*.deb, and various permutations of that command, didn't work.  dpkg complained about needing the actual package name, not the name of the .deb file.  

It also seemed to be confused about the OpenOffice installation on my Windows partition.  Running dpkg -l | grep openoffice* gave a list including the Windows versions.  I also didn't want to have to go through every single folder and run the dpkg commands over and over.

In the end I did the following:

1. made sure I was in my own /home folder. Previously, I was somehow running these commands from my separate data partition. I don't know if this made a difference but I no longer saw the .cab files after I did this (perhaps a big "duh"?).

2. generated a list of the OpenOffice files that dpkg knew about:

```
dpkg -l | grep openoffice* > /home/mander/openlist.txt
```

This generated a text file that looked a little bit like this:

```
ii  openoffice.org-base 2.4.3-21  Base module for OpenOffice.org 2.4
ii  openoffice.org-calc 2.4.3-21  Calc module for OpenOffice.org 2.4

```

and so on.  

3. In order to turn this into a list on one line, I imported it into Gnumeric as a tab-delimited file, which separates the text lines into columns.  I then copied the column with the package names back into a text file and joined all the lines (ctrl+j in gedit).

4. For good measure I created the whole command in gedit, copied it, and pasted it into the command line using middle click.  This is the final command I used:

```
sudo dpkg -r -B openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-core01 openoffice.org-core02 openoffice.org-core03 openoffice.org-core03u openoffice.org-core04 openoffice.org-core04u openoffice.org-core05 openoffice.org-core05u openoffice.org-core06 openoffice.org-core07 openoffice.org-core08 openoffice.org-core09 openoffice.org-core10 openoffice.org-debian-menus openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome-integration openoffice.org-graphicfilter openoffice.org-headless openoffice.org-hyphenation openoffice.org-hyphenation-en-us openoffice.org-impress
```

This might have uninstalled some of the bits of the Windows installation of OpenOffice, but since I know how to fix that I am not as worried.

This seems to have worked, in that OpenOffice now seems to be gone.  Now the next step is trying to install the older version again, which is an entirely different kettle of fish.

ETA:
Well, it didn't quite work, in fact.  After spending several hours trying various things with dpkg, aptitude, synaptic, etc. I finally tried 

```
dpkg --purge

dpkg --remove --force-remove-reinstreq

and 

dpkg --purge
```

again, with the above list of files, and it finally seemed to get rid of them all and I was able to re-install OpenOffice from the usual Jaunty repository.

---

### Post by lukjad on 2009-10-11
Nice tutorial. Let us hope it will be moved to that section. :)

---

