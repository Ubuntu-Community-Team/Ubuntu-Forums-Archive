---
title: "Next Questions"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by kakashi_12 on 2009-05-15
Not sure where the other thread went. i have a hard time finding my posts on here unless i search for them. i made one just like that and couldnt find it even through search. oh well, anyway...

1. how do i make a shortcut? is it called a launcher in linux?

2. how do i do a dual display clone to my tv? or just single display to tv.  i have an svideo cable.

3. ( i forgot the 3rd question)

4. if ubuntu stores it's updated version and the previous version in the grub loader then does that mean that the information is stored twice (the whole os)? how does that work?

---

### Post by hobo14 on 2009-05-15
1. Menus and panels need launchers.  Shortcuts (links) to files or folders in Nautilus or on your desktop can just be made by dragging a file with the middle mouse button and choosing "make link".  Or hold shift-ctrl when you drag with the left mouse button.

2. Plug it in, go to System > Preferences > Screen Resolution

4. GRUB isn't storing anything, it's just pointing at which OS should be loaded.

---

### Post by kpkeerthi on 2009-05-15
4. [http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/")

---

### Post by alphacrucis2 on 2009-05-15
> **kakashi_12 said:**
> Not sure where the other thread went. i have a hard time finding my posts on here unless i search for them. i made one just like that and couldnt find it even through search. oh well, anyway...


Click the down arrow beside search and select "find all your threads" or "find all your posts". They are at the bottom of the pop up list.

...

> 4. if ubuntu stores it's updated version and the previous version in the grub loader then does that mean that the information is stored twice (the whole os)? how does that work?

Grub reads a small text file in /boot/grub called menu.lst which grub uses to display the boot menu. The information in that file also tells grub how to find the corresponding kernels or OS's such as Windows which you select from the menu.

---

### Post by L Campbell on 2009-05-15
> **kakashi_12 said:**
> Not sure where the other thread went. i have a hard time finding my posts on here unless i search for them. i made one just like that and couldnt find it even through search. oh well, anyway...

1. how do i make a shortcut? is it called a launcher in linux?

2. how do i do a dual display clone to my tv? or just single display to tv.  i have an svideo cable.

3. ( i forgot the 3rd question)

4. if ubuntu stores it's updated version and the previous version in the grub loader then does that mean that the information is stored twice (the whole os)? how does that work?

If you want to find threads that you are subscribed to, got to the top of this page, left hand side and click on 'User CP'.

---

### Post by 3rdalbum on 2009-05-15
When GRUB lists Ubuntu multiple times, it's not listing copies of the entire operating system. It's just listing the current kernel and one or two old kernels, for safety. Kernels are relatively small - about 110 megabytes. If you want to get rid of the old kernel versions in Synaptic Package Manager, then that's fine - just make sure the one you keep works alright!

---

### Post by muteXe on 2009-05-15
3.  No i won't marry you :(

---

### Post by kakashi_12 on 2009-05-15
LOL... it's ok i'm engaged anyway.
 haha.
 
I remember the 3rd question now. Is there a ctrl alt del equivelant for linux to kill processes?

---

### Post by VCoolio on 2009-05-15
There is the system monitor where you can kill processes and you can set a keybinding for that. In a terminal you can run 'top', look for your process id and do 'kill pid', or if for example the process is firefox do 'killall firefox'. The latter will kill all windows of that application, the former only the one you pointed to.
There is also a panel icon to kill windows; rightclick on panel >add to panel and scroll down to find it. You click that icon, then the bad app and it will die. 

You can also do alt+SysRq(=PrintScreen)+k, which will kill everything and gets you back to the login screen.
If you're really stuck you can do alt+SysRq+ r e i s u b , where you do the reisub while holding alt+sysrq and with a second between each character. This will force a reboot.

---

### Post by kakashi_12 on 2009-05-15
AWESOME!!! Thank dude. What do those string of characters stand for? r e i s u b

---

### Post by VCoolio on 2009-05-15
It's all [here]("http://en.wikibooks.org/wiki/Linux_Guide/Freezes#Alt.2BSysRq")

---

### Post by kakashi_12 on 2009-05-17
ok, i tried to display to the tv. but that didn't work! i tried the detect displays button and the mirror checkbox. nothing.

---

### Post by kakashi_12 on 2009-05-20
???

---

### Post by Bölvaður on 2009-05-20
look at my signature and then continue reading.


Connect the computer to the external monitor before turning anything on.
Then turn the monitor on.
Then turn the computer on.

Now it if didnt work then, then try open Display settings again and check if it detects the external display now. If it does but doesnt show any image, then try change resolution and hz of that display.
If you dont have any external monitor poping up there I guess you will have to make a new thread dedictated to that problem. I am still sure some one else had this problem.. try searching very hard on this forum.


Btw shortcuts are made 2 ways.
Directories (have already been stated) where your link acts as a shortcut to a directory
And Lunchers, where you put a command like "frozen-bubble" into it. The command can be anything, it can even be "gnome-terminal -e "ls -R /" so you can see that you can do what ever you want with it... like logging into wireless networks quicker than with the manager that comes with gnome

---

