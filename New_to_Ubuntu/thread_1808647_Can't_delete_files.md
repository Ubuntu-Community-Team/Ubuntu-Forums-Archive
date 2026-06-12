---
title: "Can't delete files"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by lwalper on 2011-07-20
I'm in the file manager and seem to be unable to delete files / folders. Delete key is dead and the right click option to move to the trash is greyed out.

---

### Post by wolfen69 on 2011-07-20
Where in the file manager are you? Root? Home?

---

### Post by mokrates on 2011-07-20
do you have write permissions to the directory in question?

---

### Post by Primefalcon on 2011-07-20
> **wolfen69 said:**
> Where in the file manager are you? Root? Home?
the files are probably owned by root, if you are sue they're really safe to delete

hit alt+F2 and type:

```
gksudo nautilus /home/<yourUserName>
```

and then delete them  (be careful this opens a window with root (admin powers), which means you can delete pretty much anything, even important system files so be very very careful (which is why you'll be prompted for a password when doing this).

---

### Post by lwalper on 2011-07-20
Well, I installed CrossOver from the Software Center. The installation went without a hitch, but there are no icons anywhere to actually run the program. The only icon I can find is one to uninstall the application. Seems kinda strange to install an application with the only option available being to uninstall it??

So, I clicked "uninstall" - the appropriate warning box opened telling me that all the files CrossOver had installed would be deleted. OK?? Following the "uninstall" I went to Nautilus to see if the files has actually been deleted and they had not been.

So, I'm in File System/opt/cxoffice/doc/ trying to delete some of those persistent files.

D I have write permissions? I suppose -- I'm the only one with a user account and haven't changed anything from the original installation.

---

### Post by Primefalcon on 2011-07-20
> **lwalper said:**
> Well, I installed CrossOver from the Software Center. The installation went without a hitch, but there are no icons anywhere to actually run the program. The only icon I can find is one to uninstall the application. Seems kinda strange to install an application with the only option available being to uninstall it??

So, I clicked "uninstall" - the appropriate warning box opened telling me that all the files CrossOver had installed would be deleted. OK?? Following the "uninstall" I went to Nautilus to see if the files has actually been deleted and they had not been.

So, I'm in File System/opt/cxoffice/doc/ trying to delete some of those persistent files.

D I have write permissions? I suppose -- I'm the only one with a user account and haven't changed anything from the original installation.
I wouldn't do that.... try doing an apt-cache search --installed crossover and then do a sudo apt-get autoremove --purge <whatever> based on that

---

### Post by halitech on 2011-07-20
> **lwalper said:**
> 
So, I'm in File System/opt/cxoffice/doc/ trying to delete some of those persistent files.

D I have write permissions? I suppose -- I'm the only one with a user account and haven't changed anything from the original installation.

by default, the only place you have read/write/delete permissions is inside your home directory. Everything else is owned by Root so those files would have do be deleted by root. 

I would do as Primefalcon suggested first before just deleting files/folders

---

### Post by mokrates on 2011-07-20
So you don't.
Installed files under /opt usually are owned by 'root' and you are some 'user'. As probably most of CrossOver is deinstalled, and the remaining stuff probably wont use up much space and don't harm your installation,
AND since you don't know about root or permissions, you should probably just leave that couple o' files alone.

CrossOver itself is a Wine fork which doesn't have to install a 'clickable application' as it can be viewed as kind of a 'subsystem' which enables you to run Windows programs. So as CrossOver was installed, you should have tried to run an Installer of some Windows program

---

### Post by lwalper on 2011-07-20
OK, so, in a terminal I enter
```
leslie@leslie-laptop:/$ apt-cache search --installed crossover
```
which returns
```
mda-lv2 - Paul Kellett's MDA plugins ported to LV2
phasex - Phase Harmonic Advanced Synthesis EXperiment
swh-lv2 - Steve Harris's SWH plugins ported to LV2
crossover-standard - Run Windows applications like MS Office
```
So I run
```
leslie@leslie-laptop:/$ sudo apt-get autoremove --purge mda-lv2
```
which returns
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mda-lv2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 191 not upgraded.
```
Not removed? Has it already been deleted? I still see the files in Nautilus.

---

### Post by halitech on 2011-07-20
> **lwalper said:**
> OK, so, in a terminal I
```
leslie@leslie-laptop:/$ apt-cache search --installed crossover
```
which returns
```
mda-lv2 - Paul Kellett's MDA plugins ported to LV2
phasex - Phase Harmonic Advanced Synthesis EXperiment
swh-lv2 - Steve Harris's SWH plugins ported to LV2
crossover-standard - Run Windows applications like MS Office
S I run
[code]leslie@leslie-laptop:/$ sudo apt-get autoremove --purge mda-lv2
```
which returns[/code]
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mda-lv2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 191 not upgraded.
```
Not removed? Has it already been deleted? I still see the files in Nautilus.

try this

```
sudo apt-get autoremove --purge phasex swh-lv2 crossover-standard
```
that should remove everything

then do
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by lwalper on 2011-07-20
OK. That's in the process -- 166Mb to download.

---

### Post by lwalper on 2011-07-20
Looks like that cleaned it all out. Thanks a lot!

---

