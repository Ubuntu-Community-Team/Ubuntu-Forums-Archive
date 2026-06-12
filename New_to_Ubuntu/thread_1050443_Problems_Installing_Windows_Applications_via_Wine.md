---
title: "Problems Installing Windows Applications via Wine"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Steveor on 2009-01-25
I've recently installed the latest versions of Ubuntu (8.10 I believe) and Wine 1.0.1 and am trying to install Garmin's MapSource Topo V 2.0, topographical maps for installation into GPS receivers (a three disc process).   I can't recall all the problems but I eventually blundered  through and got it installed so it would run properly.  Then I attempted to install MapSource MetroGuide Europe V 5 which contains European street maps (a two disc process).  I kept having problems when I had to insert the second disc; CD ROM drive would not allow me to open it.  The I learned the "wine eject" command in the terminal and was able to put in the second disc.  Then the install program kept prompting me to put in the disc despite it being present in the "Places" drop down menu.  After several times of restarting the install I was eventually able to finish the process.  I don't know what I did differently if anything.  Once both programs are installed they should run concurrently.  Unfortunately I was never able to reopen the program.  When I do all I get is the opening screen and then nothing.  It just stays there.  The system manager reads the program takes 90+% of the CPU but nothing happens.  

After reading about a dozen other threads, I've loaded a bunch of other suggested programs (I don't know what they are for) but have not solved this issue.  Any assistance or suggestions would be greatly appreciated.

P.s. I've also had problems with VirtualBox but that is for a different thread.

---

### Post by lavinog on 2009-02-15
wine still has issues with alot of programs.
you may want to manually start the program from a terminal to see the error messages
```
wine programname 
```
you should be in the program's folder first:
```
cd ~/.wine/drive_c/Program\ Files/programfolder
```

There is a bug in wine that prevents apps that use directX and menubars simultaneously to work properly (like cad programs)

---

### Post by Kareeser on 2009-02-16
Steveor, because of the nature of Windows programs, and the inherent coding differences present in the WINE library layer, some programs are bound not to work properly.

Also, WINE's development base is small (but dedicated), and it only recently came out of its beta stages.

For now, your best bet would be to check the AppDB ([http://appdb.winehq.org](http://appdb.winehq.org)) to see if your program is supported, and if there are any workaround that need to be applied pre or post-installation.

---

### Post by davidsrsb on 2009-02-16
There are more recent versions of wine from wthe winehq site. They are on a two week release cycle.

Garmin mapsource worked at one point in wine, but the two most recent releases (for Vista compatibility) do not work  without some messing about with native MS libraries

---

### Post by petersfreeman on 2010-03-11
I am attempting to get MapSource version 6.15.x working under Wine.  An earlier version worked however I needed to install the latest version to be compatible with the one I have installed in my Vista partition.  MapSource is the last application I need to run under Windows, then I can use Ubuntu for everything.

The MapSource install worked fine under Wine, but when I try to run the installed application, a blank small window opens momentarily, probably the initial MapSource image, then it just quits.  I have installed WineTricks.

Here are the messages I get when I run MapSource from a console:

[FONT="Courier New"]
wine: Call from 0x7b845540 to unimplemented function gdiplus.dll.GdipCreateFontFamilyFromName, aborting
wine: Unimplemented function gdiplus.dll.GdipCreateFontFamilyFromName called at address 0x7b845540 (thread 0009), starting debugger...
Unhandled exception: unimplemented function gdiplus.dll.GdipCreateFontFamilyFromName called in 32-bit code (0x7b845592).
[/FONT]

I don't know how to proceed from here.  Could you help me please.

Thank you,

Peter

---

