---
title: "need help saving scripts"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by bizzy31 on 2009-12-08
I need to "save this code into a text editor and save it in ~/bin."  I have no idea where this ~/bin folder is, and whenever I try to save the below script into the regular bin folder, it says I do not have permission to do this.  I also need to mark the script as executable with this command: chmod +x ~/bin/d2*.  

I'm following a guide to running multiple windows of diablo 2 but I am completely lost with linux.  Any help would be appreciated!
#!/bin/sh
export WINEPREFIX=$HOME/.wine-d2a
winecfg
wine "/mnt/drive_l/Programme/d2a/Diablo II.exe" -skipbnet -w

---

### Post by Some Penguin on 2009-12-08
If you don't have a ~/bin directory (note:  ~ stands in for your home directory -- it's interpreted that way by most shells), the direct solution is to make one.

mkdir ~/bin

---

### Post by bizzy31 on 2009-12-08
ok so I made the folder and saved the scripts to it.  How would I mark them as executable with this command: chmod +x ~/bin/d2*.  where would I add that line?

#!/bin/sh
export WINEPREFIX=$HOME/.wine-d2a
winecfg
wine "/mnt/drive_l/Programme/d2a/Diablo II.exe" -skipbnet -w

---

### Post by vanhelsing2009 on 2009-12-10
[SIZE=3]well if u need t make it excutable by manualy way
right click on ur file  then choose permissions and make it excutable

[/SIZE]

---

