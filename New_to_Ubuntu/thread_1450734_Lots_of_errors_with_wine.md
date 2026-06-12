---
title: "Lots of errors with wine"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by woodsonoversoul on 2010-04-09
Hi All,
    I'm messing around with wine for the first time trying to install Goggle SketchUp. I believe everything installs correctly, how ever I get the following errors when I try to run SketchUp:
```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGCore.dll") not found
err:module:import_dll Library libIGCore.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\SketchUp.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGCore.dll") not found
err:module:import_dll Library libIGCore.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGUtils.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGCore.dll") not found
err:module:import_dll Library libIGCore.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGMath.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Google\\Google SketchUp 7\\libIGMath.dll") not found
```

Plus lots more. What am I missing (beside what's listed up there) and how do I get it?

---

### Post by cogier on 2010-04-09
I am no expert here but the list you show only contains 2 missing DLL files. These are **MSVCR80.dll** and **libIGCore.dll**. They should be included with the software or you may need to get them from a copy of Windows (try Google). I suggest you put them in the folder **/home/Your Name/.wine/drive_c/windows/system32** and see if that works.

---

### Post by woodsonoversoul on 2010-04-09
Thanks, I'll try that. It sounds like I need to update my copy of wine or something...

Oh and also, there's about three pages of errors like the ones I posted above...

---

### Post by Sir Jasper on 2010-04-09
Hi,

Wine HQ reports Sketchup v 6 using Wine v 1.1.21 has a Gold rating.

Later versions of Sketchup and Wine have a Silver rating.

My regards

---

### Post by e4uforums on 2010-04-09
Have you looked at PlayOnLinux?  PlayOnLinux is a frontend to WINE which handles all the version, update, and configuration requirements for a bunch of different programs.  It looks like Google Sketchup has a supported install script:

[http://www.playonlinux.com/repository/?cat=2](http://www.playonlinux.com/repository/?cat=2)

It's pretty slick, I used it to install Photoshop CS4 and IE7 without any trouble or headache - and both worked nearly flawlessly (some minor graphic problems, but all functionality was there).

It worked well for me as I'm pretty new to Ubuntu.  Couldn't hurt to give it a shot.

---

