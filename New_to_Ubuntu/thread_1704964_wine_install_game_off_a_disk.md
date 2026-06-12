---
title: "wine install game off a disk"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by mushroom08 on 2011-03-11
ok i just got wine to try and play one of my games ive configured it with terminal but 

Open the terminal, and cd into the directory where the .EXE is located.
Type wine the-name-of-the-application.extension (e.g. wine realplayer.exe).

ok ive tried my damnedest but i cant figure out how to use the cd command or even figure out what my cd/dvd drives directory would be (im trying to install off a disk) i just dont know much about the terminal yet help plz

---

### Post by ~Plue on 2011-03-11
an easier way would be to right click the exe > open with custom application >> "*wine*" - without quotes of course  (note that its not 'wine program loader' which is the default)

but in case you want to open through terminal;
*ls /media* would show the name of the mount point (eg diablo 2 installation disk)
then run 
```

wine /media/diab*[press tab to auto complete]*/install.exe
```

---

### Post by mushroom08 on 2011-03-11
ok i used the terminal line it started then i got "unable to locate necessary files. please run setup from the CD-ROM disc"???

---

### Post by ~Plue on 2011-03-11
what application are you trying to run? see the application rating and test results at the wine appdb to check if you could actually run it smoothly. if any thing extra needs to be done, it'll most probably will be in the 'HOW TO' or 'Troubleshooting' section of that app

>> [http://appdb.winehq.org/index.php](http://appdb.winehq.org/index.php)

---

### Post by mushroom08 on 2011-03-11
its an older game dune 2000

---

### Post by ~Plue on 2011-03-11
the appdb entry doesn't seem to help much...i can give a brief explanation of the comments though
 
either run the setup from within the folder
[I]cd /media/<path>
wine setup.exe
[/I]
OR, open *winecfg (application menu>wine>configure wine) *, add a new drive pointing to the mount point of the cd (/media/<*path>*). under advanced settings, set the type to cd-rom.
then, run
*ln -s /dev/<cdrom_device> ~/.wine/dosdevices/<drive_letter>\:\:*

/to find the cdrom_device, see if its listed in system menu>administration>disk utility
or* mount | grep '/media/<**path**>'*

---

### Post by mushroom08 on 2011-03-11
im still having trouble i can get it to start but then i get the damn error message

---

### Post by grahammechanical on 2011-03-11
The way that I install programs off of a disc is to type in a terminal winefile. It loads up a Windows explorer type file manager. I browse to the CD drive (usually drive D: and find the relevant setup.exe or install.exe whatever the program uses to install.

Regards.

---

### Post by mushroom08 on 2011-03-12
i got the same error message

would it just be easier to rip the disk onto my drive and just run it from there and how would i do that?

---

### Post by Mark Phelps on 2011-03-13
The link below is to the WineHQ that has info for Dune 2000:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1670]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1670")

The Bronze rating is the lowest rating an app/game can get -- other than Garbage. So, don't be surprised if stuff does not work.

---

### Post by mushroom08 on 2011-03-13
but still said it will install i looked at that before i got wine

---

