---
title: "ubuntu will not open exe files"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2010-06-13
everytime i try to install a program or even try to get a software program installed   that has a exe file i get this error that states 

("The file '/media/SetupAssistantCD/SetupAssistant.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.")   

i kno its from a trusted source  just like the other software i got ahold of  and im just wondering  how do i get past this?

---

### Post by lisati on 2010-06-13
First of all, an "exe" file is an MS-DOS or Windows program file, and won't run on Ubuntu without help. "[Wine]("https://help.ubuntu.com/community/Wine")" is a common way of running *some* Windows software.

If you already have Wine installed, you *might* need to mark the file as "executable". You can do this from the command line with something like this: ```
sudo chmod +x program-file-name
```

---

### Post by Cthulhu_Dreams on 2010-06-13
Right click on the file -> click Properties -> Click Permissions -> Check "Allow executing this file as program"

---

### Post by marshmallow1304 on 2010-06-13
You may encounter issues with the above advice (which is otherwise valid) if you are trying to execute this file from a CD-ROM.  Since the CD-ROM is read-only, you will not be able to change the permissions.  To get around this, run the executable directly with wine (after it's installed, of course).

```
wine /media/SetupAssistantCD/SetupAssistant.exe
```

---

### Post by Mark Phelps on 2010-06-13
Also, you should be aware the Wine will not run every MS Windows app, far from it!

Before you try installing the app, you should go to the WineHQ site below and do a search on the app name and version:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

The resulting rating will give you a good idea of how well the app will actually work in Wine.

---

### Post by seradaluna on 2011-02-11
> **marshmallow1304 said:**
> You may encounter issues with the above advice (which is otherwise valid) if you are trying to execute this file from a CD-ROM.  Since the CD-ROM is read-only, you will not be able to change the permissions.  To get around this, run the executable directly with wine (after it's installed, of course).

```
wine /media/SetupAssistantCD/SetupAssistant.exe
```

I tried that and it said it could not find it

---

