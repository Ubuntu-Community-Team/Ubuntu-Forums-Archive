---
title: "virtualbox installed but cant find how to open it!"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by gfunkera on 2009-08-10
hi i have jaunty jackalope and i downloaded the virtualbox version that was recommended for this version of ubuntu on the official website.. its basically the newest version (3.0, i think).. 

anyway, its installed but i cant open it! i typed in virtualbox into the terminal and it came back saying to download virtualbox-ose, but that interferes with the version thats already installed (i know this because i went through a whole bunch of uninstalling and installing virtualbox 3, 2.14, and virtualbox-ose a few times) 

when i have 3.0 installed theres no icon or anything i can find, no command will work to get it going (i tried vboxgtk also and nothing happened)... i have noticed that when i have virtualbox-ose or vboxgtk installed, there are icons for them in the accessories menu of the applications menu... but when i click on them, nothing happens, no program opens,....

how do i get to the GUI?!??!!??!?!?!?!?!?!?!?!?!!??!?!!?

---

### Post by bowens44 on 2009-08-10
There should be a link under Applications/System Tools

---

### Post by mrgreggie on 2009-08-10
I had a similar problem on one of my systems.  For some reason it did not display after installing it.  So I right clicked on "Applications" and selected "edit menus".  When I did, under System Tools it was already checked.  So, I unchecked it, rechecked it, and BAM... it was in the menu.  I hope this helps.

---

### Post by DrDevice on 2009-08-10
If that doesn't work, just type "VirtualBox" in the Alt-F2 run window, that's what I do.  :)

---

### Post by bowens44 on 2009-08-10
OK, I remember now, I had to log out  and then log back in for the link to appear.....

---

### Post by gfunkera on 2009-08-10
okay i did what mrgreggie said to do and it worked! but now i have a new problem!!
 
im stuck in windows 7! im using virtual box and i entered capture mode but i cant exit it! i pressed the Right Ctrl button (which is designated as the home key by default) and still its stuck in capture mode.. 
 
when i do press the control button it shows the true position of the mouse because i have my ubuntu set to indicate where the mouse is with a visual animation when i push either ctrl button..
 
how can i get virtualbox to realize that i want out of capture mode?!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by mrgreggie on 2009-08-10
Not sure if there is a potential conflict with right ctrl on your system, but changing it might be something to try.  To get out of Windows in the meantime, select shutdown from the start menu.  Once it gets done shutting down the VM, you should be able to get back to Ubuntu.  Again, i'm not sure why the right ctrl key isn't working, but changing it to see whether it makes a difference would be a start.

---

### Post by rodh on 2009-08-11
I had a simular issue.  I made the Menu Key the default,  it dosn't seem to have issue there.

---

### Post by ReddogOne on 2009-08-11
> **mrgreggie said:**
> Not sure if there is a potential conflict with right ctrl on your system, but changing it might be something to try...

Or try installing the guest additions and you don't need to capture and re-lease the mouse.

---

