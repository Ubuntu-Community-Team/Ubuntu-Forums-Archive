---
title: "what files am i looking for??"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by andru183 on 2009-07-25
you know the way windows has exe files, well im trying to set up shortcuts to some programs to get them to run and i dont know what type of file im looking for, like nvidia x server setting, i want to put that in the menu to click and have it run but i dont even know what the command to run it is, all im asking is what is the ubuntu version of an exe?

---

### Post by Mark Phelps on 2009-07-25
> **andru183 said:**
> you know the way windows has exe files, well im trying to set up shortcuts to some programs to get them to run and i dont know what type of file im looking for, like nvidia x server setting, i want to put that in the menu to click and have it run but i dont even know what the command to run it is, all im asking is what is the ubuntu version of an exe?

The general way to do this is to right click on the Applications area on the top-left of the screen and edit the menus.  You can then add a selection to the submenu of your choice.  Those work much like shortcuts in MS Windows.  You use the edit menu panel to locate the program you want to run, fill out the panel, and then when you open the menus next time, you have a menu entry.

---

### Post by Whiffle on 2009-07-25
Well, the way linux works is that file extensions don't mean anything to the OS, all of the information about a file is stored within the file, or the OS can look at the file and figure it out.  

But to answer your question, the easiest way to find something is usually using the command line tab complete, or doing:

which <nameofprogram>

But in general, executables for programs are located in /usr/bin

---

### Post by andru183 on 2009-07-25
> **Mark Phelps said:**
> The general way to do this is to right click on the Applications area on the top-left of the screen and edit the menus.  You can then add a selection to the submenu of your choice.  Those work much like shortcuts in MS Windows.  You use the edit menu panel to locate the program you want to run, fill out the panel, and then when you open the menus next time, you have a menu entry.
its just i find a load of nvidia files and dont know which one will run it??

---

### Post by oldos2er on 2009-07-25
If you've installed the proprietary Nvidia drivers, you should have a menu entry at System, Administration, NVIDIA X server settings. If this doesn't exist, create a launcher with the command **/usr/bin/nvidia-settings**

---

