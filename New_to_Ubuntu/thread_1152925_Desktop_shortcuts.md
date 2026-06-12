---
title: "Desktop shortcuts"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by thelegionsplayer on 2009-05-08
How can i create desktop shortcuts to apps that run on windows?(like to opera.exe in drive D:  etc)

---

### Post by suitedaces on 2009-05-08
Edit, misread

---

### Post by achase79 on 2009-05-08
If you are going to run windows programs through wine, you should install the program in wine. Registry entries are used differently in wine than in windows.

---

### Post by thelegionsplayer on 2009-05-08
oh i just use open with :wine from right click drop down menu
and how do u "install" the programs in wine?
and is there any windows registry equivalent for wine/ubuntu

---

### Post by achase79 on 2009-05-08
Installing in wine usually puts a launcher on the desktop and always in the menu, so if it doesn't give you a launcher on the desktop you can drag it out of the menu to the desktop.

---

### Post by achase79 on 2009-05-08
Ubuntu itself uses gconf but wine has its own registry in the ~/.wine directory.  The registry editor for wine is just like the one for windows... you just type "wine regedit".  To install in wine just get the installation program and right click and select to open with wine.  This should run the installer and install it in wine.  Some programs are more compatible with wine than others.  If you need specific program information go to [appdb.winehq.org]("http://appdb.winehq.org")

---

### Post by achase79 on 2009-05-08
Any particular reason you want to run Opera for windows rather than the native linux version?

---

### Post by aeiah on 2009-05-08
once you've set up your windows program to run via wine (and it does seem odd that you'd want to do this with opera since it has a native linux version) then you can start it from the command line like:

> 
wine ~/.wine/drive_c/installpath/program.exe


once you've got that tested, you can create a launcher that'll do it for you.

right click on the desktop and use the menu to create a launcher. go into its properties and in the target field enter the command that you know works in the terminal. you can also enter tooltip info and select an icon from there too.

you can do the same thing for directories. i have my film and incoming folders linked from launchers on the desktop. for folders i think you select 'file' rather than 'application' or whatever in the launcher's properties box.


you can also use that command line for use on your ubuntu menu via creating a new menu item, if like me you want your games that run under wine to be in your games section of the menu and not the wine section.

---

### Post by thelegionsplayer on 2009-05-08
er no i dont want opera..was just an example
so if install programs in wine c drive where does it get stored?iv installed ubuntu within windows  in F; drive.so the files will be in F; drive?

---

### Post by aeiah on 2009-05-08
> **thelegionsplayer said:**
> er no i dont want opera..was just an example
so if install programs in wine c drive where does it get stored?iv installed ubuntu within windows  in F; drive.so the files will be in F; drive?

linux doesnt use drive letters. partitions and hard drives are mapped to directory locations. the example i gave was ~/.wine/drive_c/... ~/ is shorthand for home, so the absolute path to your home is /home/username/

all programs store their config files and user files in a hidden folder in your home directory. in linux, folders are hidden if they begin with a dot. to show hidden folders in nautilus you can press ctrl+h, and again to hide them again.

wine is an emulation environment for windows, and as such, it emulates drive letters too.. anything within the ~/.wine/drive_c/ folder is seen by wine as being in the C: drive, even though under linux no such drive exists.

just dropping things in the drive_c folder wont make them run with wine, and in fact windows software doesnt need to be in drive_c, its just the default location that wine uses.

i suggest finding a program you may want to use that is known to work well in wine and following a tutorial on how to install it, and then you may get a clearer idea of how wine structures things. a lot of people like using utorrent in wine and it works very well apparently, although i prefer deluge which is native to linux.

incidentally, if you should be able to find the partitions that you had in windows (with drive letters) in ubuntu in the /media/ folder, if they have been mounted already and are accessible.

ps: just in case you weren't clear. wine wont run the applications that you have installed under windows (or not without things getting really complicated). the best approach is to re-install them with wine. also bear in mind that wine cant make every windows program run smoothly and a lot wont run at all, but thankfully linux has alternatives to just about anything you'd want to run on windows, except for games and certain things like autocad. check winehq.org to see what programs run flawlessly, which have a few bugs, and which are rubbish.

---

### Post by thelegionsplayer on 2009-05-08
well wat i asked was: i hav installed ubuntu _ within windows_   in the F: drive so everything connected to ubuntu gets stored in F: drive right? so if i install a prog, say hitman 2, using wine ..the disk space onF; drive wud get used right?

well my hdd is of 80gb so disk space is a luxury that i dont have for the time being..wat shud i do to make programs accesible both in windows and ubuntu/wine?

---

### Post by jacksinn on 2009-05-08
You, unfortunately, aren't going to be able to install Hitman (or any other program) once in Ubuntu and run it in Windows or vice-versa. You'd have to install it in both locations which, like you said, isn't a luxury and 80gb hard drive can afford. Now, if you want to use the same conf files or any other files and you are using a WUBI install you can access those items in the
/host directory which then is basically like looking at your C:\ drive in Windows.
If you aren't using a WUBI install, you can still view those files (typically) as a separate mounted volume.

---

### Post by thelegionsplayer on 2009-05-08
wen i unistall the programs in wine the menu entry (applications>wine>programs) for the corresponding  program is not removed 
for eg i installed hitman 2 and uninstalled it, but still in applications>wine>programs eidos interactive and hitman 2,uninstall hitman etc are still present
is there any way to manually remove these entries?

---

### Post by aeiah on 2009-05-08
> **thelegionsplayer said:**
> well wat i asked was: i hav installed ubuntu _ within windows_   in the F: drive so everything connected to ubuntu gets stored in F: drive right? so if i install a prog, say hitman 2, using wine ..the disk space onF; drive wud get used right?

well my hdd is of 80gb so disk space is a luxury that i dont have for the time being..wat shud i do to make programs accesible both in windows and ubuntu/wine?


bang your head against the wall? :P

(and no, that wasn't what you originally asked, you asked about desktop shortcuts)

if you can get your hands on a portable version of the application you need (and doing so for hitman would be illegal and i cant condone that on this forum) then you could place it on a partition that both windows and ubuntu has access to and both wine and windows could run it without installing it. if a portable version isn't available then it gets tricky. what happens when you install something in windows? it saves savegames in My Documents, and it saves stuff in the registry. you'd have to mirror this in wine which is possible, but pretty tricky.

fortunatley it seems hitman 2 can run well in ubuntu as shown here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1848&iTestingId=39348](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1848&iTestingId=39348)

but unless you can find a portable version you may find you're stuck having to install it in two different locations.

---

### Post by aeiah on 2009-05-08
> **thelegionsplayer said:**
> wen i unistall the programs in wine the menu entry (applications>wine>programs) for the corresponding  program is not removed 
for eg i installed hitman 2 and uninstalled it, but still in applications>wine>programs eidos interactive and hitman 2,uninstall hitman etc are still present
is there any way to manually remove these entries?

try editing your menu (right click> edit menus)

or perhaps there's something in wine. i dunno, i have the wine menu hidden all the time and put my games in the game section as i described earlier in this thread.

---

### Post by thelegionsplayer on 2009-05-08
> **jacksinn said:**
> You, unfortunately, aren't going to be able to install Hitman (or any other program) once in Ubuntu and run it in Windows or vice-versa. You'd have to install it in both locations which, like you said, isn't a luxury and 80gb hard drive can afford. Now, if you want to use the same conf files or any other files and you are using a WUBI install you can access those items in the
/host directory which then is basically like looking at your C:\ drive in Windows.
If you aren't using a WUBI install, you can still view those files (typically) as a separate mounted volume.
didnt get u^^.

iv instaleed ubuntu within windows i;e in a disk partition created by windows.the name of which is F:   ..i kno that i can access C :  D: and E: drive 
and yes the install thingy's name was wubi

---

### Post by thelegionsplayer on 2009-05-08
> **aeiah said:**
> bang your head against the wall? :P

(and no, that wasn't what you originally asked, you asked about desktop shortcuts)

if you can get your hands on a portable version of the application you need (and doing so for hitman would be illegal and i cant condone that on this forum) then you could place it on a partition that both windows and ubuntu has access to and both wine and windows could run it without installing it. if a portable version isn't available then it gets tricky. what happens when you install something in windows? it saves savegames in My Documents, and it saves stuff in the registry. you'd have to mirror this in wine which is possible, but pretty tricky.

fortunatley it seems hitman 2 can run well in ubuntu as shown here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1848&iTestingId=39348](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1848&iTestingId=39348)

but unless you can find a portable version you may find you're stuck having to install it in two different locations.
er wat is it that u mean by a portable version? a cracked one?:lolflag:well lets just say i hav the installation files..well D drive is visible both in windows and buntu so i should do ..Wat?install it wen im running windows or install it wen im running ubuntu/wine
sorry for all the questions.just installed ubuntu yesterdayO_O
and yeah i feel like bangin my head against the wall

---

### Post by thelegionsplayer on 2009-05-08
> **aeiah said:**
> try editing your menu (right click> edit menus)

or perhaps there's something in wine. i dunno, i have the wine menu hidden all the time and put my games in the game section as i described earlier in this thread.
  right click where?cant right click on applications drop down menu and cant configure that part (i.e applications>wine>programs part of the menu)from system>preferences>main menu

---

### Post by achase79 on 2009-05-08
you want the alacarte menu editor

---

### Post by Niniel on 2009-05-08
Yes, System/Preferences/Main Menu opens the menu editor. You can drag and drop in there. 
Portable software is software that is configured so that it can be run from a USB-stick for instance and not alter the system the stick is plugged into (leaves no files behind, doesn't add anything to the Windows registry [may create temp folders/files on the computer, however]). Mostly for Windows as far as I know. A good site is [www.portableapps.com]("http://www.portableapps.com").

---

