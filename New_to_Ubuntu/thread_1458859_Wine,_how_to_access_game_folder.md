---
title: "Wine, how to access game folder?"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by hellowlol on 2010-04-20
Hello all, just got ubuntu and loving it so far.

I installed dawn of war soulstorm but now i need to access the folder to change something, i know its under apps > wine > programs > thq

but theres no way to access that folder, ive tried 'browse C:/' but when you go to program files theres no THQ or anything like that. 

please help :[


ps: i do not dual boot XP , and i can't even if i wanted atm.

---

### Post by scottiw2000 on 2010-04-20
It could be that the game is installed in its own folder, outside of Program Files but still in the fake c: drive. You can navigate to the wine filesystem by 
- opening a Nautilus window to your home folder
- pressing ctrl-h to reveal hidden folders
- opening the .wine folder (notice the . at the beginning of the name -- this marks it as a hidden folder)

In the .wine folder is a folder called drive_c and all of your installed files should be in there somewhere.

If you don't find them that way, another option is to search your filesystem. A fast way is to open a terminal and type **locate** followed by the filename or folder name you are looking for. If you don't know the whole filename you can put a * at the beginning or end as a "wildcard." That search is really fast and should show you right away whether the files are somewhere else.

---

### Post by arnab_das on 2010-04-20
> **hellowlol said:**
> Hello all, just got ubuntu and loving it so far.

I installed dawn of war soulstorm but now i need to access the folder to change something, i know its under apps > wine > programs > thq

but theres no way to access that folder, ive tried 'browse C:/' but when you go to program files theres no THQ or anything like that. 

please help :[


ps: i do not dual boot XP , and i can't even if i wanted atm.

make sure first of all that the application you're talking about is installed. you can do that by checking the Wine menus.

if the program is listed there, then it should also be in the C:\

i think there might be an issue with the installation. just reinstall the application again. also note, some applications need not be installed under C:\program files it may have a completely different folder. so do some searching. also, the application name may be different. so, try all options.

---

### Post by hellowlol on 2010-04-20
[IMG]http://i41.tinypic.com/zn8lg4.png[/IMG]

Thank you for the responses , if i go to the .wine folder i get the exact same thing if i would go to aps>wine>browse c

pic related.

I have more stuff installed with wine like macromedia flash and they work fine, but these too i cannot locate at program files [ even with show hidden files ]

---

### Post by hellowlol on 2010-04-20
nvrmind :D i found it..

it was located here

/home/ruut/.wine/drive_c/users/ruut/My Documents/.PlayOnLinux/wineprefix/DawnOfWar_Soulstorm/drive_c/Program Files/THQ/Dawn of War - Soulstorm

appreciate the help guys!

---

