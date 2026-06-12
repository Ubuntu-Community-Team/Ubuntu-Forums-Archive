---
title: "How do i ge in my windows hdd through ubuntu (read)"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by edwardpatch1 on 2011-08-19
how do i open my windows 7 hdd with ubuntu so i can get a .exe from it plz help :)

---

### Post by Bachstelze on 2011-08-19
Is it not avaliable from the Places menu?

---

### Post by edwardpatch1 on 2011-08-19
wheres that im new to ubuntu

---

### Post by Basher101 on 2011-08-19
What ubuntu do you use? if its 11.04 it should be in the upper left corner if you use Unity. Otherwise if you use gnome 2.3 its on the top next to the bar that says applications

---

### Post by edwardpatch1 on 2011-08-19
um its 10.04 but its a diff design a bit the task bar is on side

---

### Post by Enigmapond on 2011-08-19
Well wherever it is...go to your main menu/places and see if it list there...it should be.

---

### Post by edwardpatch1 on 2011-08-19
8i really dont understand but there is a easy why a app for windows or linux called team viewer u can control
my pc and u can show me because its not available in places

---

### Post by Enigmapond on 2011-08-19
This is very easy.....Go to your Main Menu and click on "Places" and you will see your HDD listed.

---

### Post by edwardpatch1 on 2011-08-19
not in there

---

### Post by ajgreeny on 2011-08-19
Open up nautilus, the file manager, and in the left hand pane you should be able to see Places, and in there find your windows hard disk.

If not open a terminal (Applications->Accessories->Terminal)  and in that type ```
sudo fdisk -l
```(lower case L, not figure 1 at the end) and report the output back here, just to check that you do have a windows partition or disk.

---

### Post by gandaran on 2011-08-19
> **edwardpatch1 said:**
> how do i open my windows 7 hdd with ubuntu so i can get a .exe from it plz help :)
how did you install ubuntu? separate partition or inside windows (wubi)? If inside windows look for the windows files in system files /host.

---

### Post by edwardpatch1 on 2011-08-20
inside windows

---

### Post by edwardpatch1 on 2011-08-20
you have to install filemanager tho

---

### Post by edwardpatch1 on 2011-08-20
No there is no command on that terminal

---

### Post by edwardpatch1 on 2011-08-20
> **gandaran said:**
> how did you install ubuntu? separate partition or inside windows (wubi)? If inside windows look for the windows files in system files /host.
Theres a HOSTNAME.exe file in windows folder

---

### Post by gandaran on 2011-08-20
> **edwardpatch1 said:**
> Theres a HOSTNAME.exe file in windows folder
have you looked in the ubuntu file system for '/host' all your windows drive files are mounted on /host directory

---

### Post by Mark Phelps on 2011-08-20
You started out saying you needed to get an .exe file from your Windows install -- and that is really a different issue than where to find it.

The.exe files do not run natively in Linux; instead, SOME of them run using a workaround known as Wine -- which you have to install yourself.

But BEFORE you install Wine, you need to first go to the WineHQ site and look through the application compatibility database for the Windows app you want to run.  If it's not listed, it's most probably NOT going to work.  If it is listed, and it has a rating less than Gold, not only is it going to be a LOT of work getting it installed and configured, when your'e done, it's not going to work very well.

If you really need to use MS Windows programs on a regular basis, Linux is the wrong place to be.

---

### Post by migs73 on 2011-08-20
Edward, if as you say you have a WUBI (installed inside windows) Ubuntu install, follow the steps in the screen shots below.

Step 1 Click on places
Step 2 Click on Computer
Step 3 Double Click on File System
Step 4 Double Click on folder called Host
Step 5 You are now in your windows HDD, browse for the file you want.

---

