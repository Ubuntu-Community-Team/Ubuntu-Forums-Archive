---
title: "WINE and exe files"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by 3948ctyj on 2010-03-05
I downloaded a cd from a Cellular Broadband provider but it was for Windows,  exe stuff.
If I had WINE would it have installed ok???? They dont have a Linux cd.

---

### Post by seymur on 2010-03-05
What kind of CD is that? You can just install Wine and see if it will work.

---

### Post by Fläsh on 2010-03-05
Simply insert the CD into your CD-ROM/DVD/CD-ROM Drive. Ubuntu should detect the CD and automaticly mount it and the cd will appear on your desktop open the icon and the file broswer will open bringing you to your files simply drag your mouse over them to select them they should highlight in blue like windows.

After you do that drag the files onto your ubuntu desktop. Then you make a folder called 'Folder' drag the items into that folder than open the folder you created and moved the objects to. You may now eject the disk by right-clicking your cd-icon on your desktop click eject and your cd-rom should pop open take the disk out. 

Now open your terminal by going to Programs->Accessories->Terminal to open a terminal window. Now wait for it to load up and type cd drag your 'Folder' into the terminal then tap enter you should now be in your folder directory now type 

```
wine program_exe_name_etc.exe
```Follow the on-screen directions it should install correctly then go to Applications->Wine->Program Files-><Your program name>->Application name 
to launch the application.

EDIT:

P.S 'If you have time open Mozilla Firefox and type [http://appdb.winehq.org/](http://appdb.winehq.org/) search your application see if you can find it to check if wine can run it (it may not be there though)'

---

### Post by Agent ME on 2010-03-06
> **Fläsh said:**
> Simply insert the CD into your CD-ROM/DVD/CD-ROM Drive. Ubuntu should detect the CD and automaticly mount it and the cd will appear on your desktop open the icon and the file broswer will open bringing you to your files simply drag your mouse over them to select them they should highlight in blue like windows.

After you do that drag the files onto your ubuntu desktop. Then you make a folder called 'Folder' drag the items into that folder than open the folder you created and moved the objects to. You may now eject the disk by right-clicking your cd-icon on your desktop click eject and your cd-rom should pop open take the disk out. 

Now open your terminal by going to Programs->Accessories->Terminal to open a terminal window. Now wait for it to load up and type cd drag your 'Folder' into the terminal then tap enter you should now be in your folder directory now type 

```
wine program_exe_name_etc.exe
```Follow the on-screen directions it should install correctly then go to Applications->Wine->Program Files-><Your program name>->Application name 
to launch the application.

There's no need to do all of that: You can run the program straight off of the disk by just double clicking the .exe file. There's not much benefit running it from your desktop, and running it in a terminal does little better (it does give a slight explanation if a program possibly doesn't start up).


However, if the program is for installing drivers or setting up a network connection, which is what it sounds like, the program definitely is not going to work in Wine. What are you trying to set up exactly? Maybe there is a linux solution that doesn't involve the windows cd.

---

### Post by Fläsh on 2010-03-06
Well you have your methods i have mine ! I'm Generally used to installing games with wine so i insert the disc and extract the files. Follow AgentME he has more experience with ubuntu then me.

---

### Post by 3rdalbum on 2010-03-06
No, this will not work in Wine. Just set up your mobile broadband connection in Network Manager.

---

