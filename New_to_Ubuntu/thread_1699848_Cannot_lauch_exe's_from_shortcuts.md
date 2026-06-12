---
title: "Cannot lauch exe's from shortcuts"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by devilwarier9 on 2011-03-04
My computer is currently dual booting windows and ubuntu and a lot of my programs and data are stored on my windows partition, so instead of reinstalling them I just launch their exe's from my /media/Windows folder.  Most of my common programs I put links to in the Ubuntu "start" menu and they normally work, but as of upgrading to 10.10 yesterday (I know I'm late to the party) if I try to open anything, for example firstclass, it says 
"Failed to execute child process "/media/Windows/Program Files (x86)/FirstClass/fcc32.exe" (Permission denied)"
 but when I go into the folder and manually open the exe, not with a shortcut, it works.  This is happening for EVERY windows program I have a shortcut to.  Any suggestions?

---

### Post by Hippytaff on 2011-03-04
Hi and welcome
 
Are you using the .EXEs with wine?
 
anyway, you need to make files executable, but the windows filesystems (FAT NFTS etc) don't listen to Linux permissions. Therefore, you probably need to move the exes to somewhere on your linux partition in order to be able to do it. Once done, either right click on the file, go to the permissions tab and click the box next to Make Executable, or open a terminal and cd to the folder containing the exe eg ```
 cd /Downloads
``` and use [chmod]("https://help.ubuntu.com/community/FilePermissions#Changing%20Permissions") to [COLOR=black]**ch**[/COLOR]ange the **mod**e or permissions.```
sudo chmod +x filename.exe
```

---

### Post by devilwarier9 on 2011-03-04
Yes, I am using wine to open them, and they are set to executable.  The shortcuts all worked perfect in 10.04, and its not a problem that they are not executable, its that apparently the Gnome Menu Bar doesn't have permissions to the exe's.

---

### Post by devilwarier9 on 2011-03-04
can anyone give any suggestions? Theyre set to executable and run when you manually open them, but not from any shortcut

---

