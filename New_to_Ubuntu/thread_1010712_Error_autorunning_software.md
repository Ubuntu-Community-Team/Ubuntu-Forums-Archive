---
title: "Error autorunning software"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Combatkakapo on 2008-12-14
I am trying to install Counter Strike Source from the CD and whenever I put the disk in its giving me this error message "Cannot find the autorun program". Please help me

---

### Post by Michael.Godawski on 2008-12-14
hi Combatkakapo, 

you cannot run exe (Windows) applications in Linux; for windows games you need either the app Cadega or Wine. Try Wine first because it is free.

[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)

---

### Post by Combatkakapo on 2008-12-14
I have wine installed but it still give me the same error.

---

### Post by 3rdalbum on 2008-12-14
Run the installer from the CD manually. Gnome doesn't really link in with Wine very well and it doesn't look like it will automatically run Windows programs when they are in the "autorun" of the CD.

---

### Post by Michael.Godawski on 2008-12-14
You know the content of the cd better than I do..

Right click on the setup or autorun file and try to open it with wine. There should be an option, if not select open with other application and select wine.

---

### Post by Combatkakapo on 2008-12-14
ok, the autorun error is fixed and I got the disks to work, but when the first disc is done downloading, and i try to open the disc tray it gives me a new error saying "Cannot unmount vloume: An application is preventing the volume 'CSS_1' from being unmounted."

---

### Post by mc4man on 2008-12-14
There are 2 ways.
Some people use wine eject. When the first disk is done open a terminal and enter  wine eject
Sometimes it doesn't work or wine can't find the path to next disk so...

I prefer to give to wine the proper path in a way that doesn't lock the drive. 
For that you need to know what drive letter wine has assigned the drive (usually either D or E, open configure wine from applications menu -> wine or run winecfg in terminal. Ck. under drives tab. (if not listed click autodetect

Then you just need to browse the cd to find the name of the install exe.

Ex 
My drive is D and the exe on the cd is setup.exe
```

wine D:\setup.exe
```

When the first disk is done push the button on your drive, ect., actually do exactly what you'd do in windows.

---

### Post by Combatkakapo on 2008-12-14
Thank you all for the help, i finally got it to work :)

---

### Post by UniqueCrash5 on 2009-01-27
Hey folks,

 I'm having the exact same problem and it seems like it would be silly to create a new thread, sooo...

 Autorun is failing to work for multiple Windows based game disks for me.  I can cheerfully explore the CD and run the appropriate file and they run fine (Wine=awesome), but the thing is that they're kids' games and while my kid can click on a pop-up dialog, exploring the CD for the correct file is little beyond him (yet). :)

 As a result, I'd really like to get Autorun actually running properly with Wine.  

 The error I get (just as described by the original poster above) is "Error autorunning software.  Cannot find the autorun program."  The contents of the autorun.inf file is along the lines of:

```
[autorun]

open=BBCAuto.exe

icon=Bob's castle adventure.ico
```

  And yes, I can copy the disk contents to the hdd and it works fine, but I'd rather not have to...  It's very much a spare-parts pc and I don't have all that much room!  And it seems like it should be a simple fix...

---

