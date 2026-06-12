---
title: "launcher for marble blast gold demo?"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by thomz92 on 2009-10-24
i downloaded the .sh.bin file from the marble blast gold site. then i made it executable and ran "./MarbleBlastGoldDemo-1.4.1.sh.bin" (or something like that). Now to run it, i have to cd to the folder i installed it in and run "./marbleblastgolddemo". Is there any way to make a launcher for this in my applications -> games menu?

---

### Post by fooman on 2009-10-24
right-click on applications and choose "edit menus"

when the main menu pops up,  click once in the left column on "games",  then all the way over on the right,  click "new item"

for name,  type in "marble blast gold" (or whatever you want to call it)
to the right of "command",  click on "browse", navigate to the correct folder and click once on the file "marbleblastgolddemo"....then click "open".
if there is an icon for the game in that folder...drag and drop it right onto the standard icon that is in the create launcher box and you will have the correct icon for it as well.

click "ok",  then see if its in the menu.

hope that helps.

---

### Post by thomz92 on 2009-10-26
the marbleblastgolddemo file that is there doesn't work for some reason. I checked the properties of that file and it says it is a "shell script (application/x-shellscript)". But If i click on it, the little menu pops up asking me if i want to run it, run it in terminal, etc. When i push "run", nothing happens! The only way (that i can find) to open the game is to cd to the folder in the terminal and run "./marbleblastgolddemo". I have no idea why this works and just clicking on the file doesn't. Does anyone have an idea?

---

### Post by Bölvaður on 2009-10-26
is this the same thing as you guys are getting?

```
$ ./marble
Verifying archive integrity... All good.
Uncompressing Marble Blast Gold Demo............................
This installation doesn't support glibc-2.1 on Linux / unknown
(tried to run setup.gtk)

This installation doesn't support glibc-2.1 on Linux / unknown
(tried to run setup)



The setup program seems to have failed on unknown/glibc-2.1

Detecting libc...
Binary file /lib/libc.so.6 matches
Detected: os=Linux, arch=unknown, libc=glibc-2.1

```

---

### Post by thomz92 on 2009-10-26
> is this the same thing as you guys are getting?

no the installation process went fine... Im just wondering why the marbleblastgolddemo application isn't working but "./marbleblastgolddemo" does...and if i can't make it work how i would get a launcher to start it

---

