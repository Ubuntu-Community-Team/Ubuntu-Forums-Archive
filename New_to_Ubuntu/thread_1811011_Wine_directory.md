---
title: "Wine directory"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by Dead root on 2011-07-24
Hello,

I installed Wine to be able to use WINSCP. Now I installed WinSCP and everything is working fine.

**However the guide says "Theoretically, your program should be available in Applications >  Wine > Programs. For some reason, in this case, it wasn't, so you can  go to *Applications* > *Wine* > **[I]**Browse C: Drive"**

I am using the Unity desktop so when I click on applications it just shows them. How can i go to the wine directory? 

Because I can't see the applications folder or anything so i am Kinda confused.

Thank you
[/I]

---

### Post by JC Cheloven on 2011-07-24
To answer your exact question: the "c" windows-like fake disk is in the folder
~/.wine/dosdevices/c:/
where ~ is the path to your home folder, and .wine is a hidden folder (starting by "."), which is visible in nautilus hitting ctrl-h.
Inside you'll find the usual "Program Files" folder. Inside different folders, one for each app you installed. Most likely there will be a folder named WinSCP, which will contain some .exe file. You can open this one with wine (either by a command in terminal or right clicking and choosing to open with wine). This is a valid workaround if everything else fails.

Anyway, there should be a menu item already. From the unity interface click "applications" and start to type "wine". An icon for wine should appear soon. Pick that and see if there is what you would expect.

---

