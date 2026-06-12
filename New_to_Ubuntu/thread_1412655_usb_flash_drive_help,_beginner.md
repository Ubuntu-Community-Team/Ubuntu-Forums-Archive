---
title: "usb flash drive help, beginner"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by drmax on 2010-02-21
Hello,
 
I just installed ubuntu 9.10(64) yesterday on a computer I built a few days ago. It is my first time on ubuntu, I am sorry for such a basic question. The installation went easy. This is the first and only os on this computer.
 
I am trying to get my wireless working with the new ubuntu install, and I would like to be able to copy iwconfig files, etc, to the flash drive, so that I can then plug the usb flash into my other windows vista computer, which has internet access, and then be able to post into the networking forum by copying from the usb flash drive, and thussly, get help setting up the wireless. I did try searching, but to no avail.
 
When I plug in the flash drive, I can see it in places, under "cruzer". I double click and open it. I then created a file called "wireless". I am not able to type or copy into this screen. It is under media/cruzer/wireless. I am sure there is an easy answer, but so far I'm stumped.
 
Once I can type and copy into a screen, do I need the usb stick in a special format so both systems (ubu and vista) can read it?
 
Thank you for helping a new user learn,
Max

---

### Post by ajgreeny on 2010-02-21
How did you create the file "wireless"?

Can you also, please, right click on the file and look at the properties ->permissions tab to see who is the owner, and what read/write permissions there are for it. It should belong to you, as your username, and you should have read and write ability.  If not we need to put that right, but let's go one step at a time.

---

### Post by drmax on 2010-02-21
Thanks ajgreeny,
 
I may have mispoke, I actually created a folder(wireless), not a file, by right clicking on the cruzer screen, then create folder. 
 
R click on wireless folder screen, properties, permissions tab shows
 
owner: max
folder access : create and delete files
file access : ---
 
group: max
folder access : none
file access : ---
 
I tried to change the access to read and write on each and both, and it would not except changes.
 
I appreciate your help,
Max

---

### Post by Linux_junkie on 2010-02-21
This might sound like a daft question but have you tried to setup your wireless card in Network manager?

---

### Post by Greenwidth on 2010-02-21
Also, what card is it?

---

### Post by drmax on 2010-02-21
Thanks Linux_Junkie,
Yes, I did try to install the network with network manager, I do have a signal, but am having problems with the setup screens. After reading the networking forum, it looked like I would need to post some rather long outputs(ifconfig, lsmod, iwconfig, etc.), and so I figured if I could figure out how to use the usb stick, it would save alot of typing. I just assumed I would be asked for some of these outputs, but perhaps I should just go ahead and try to configure the wireless.
 
Greenwidth,
Thanks for your help, I have a linksys wrt160n v3 router, and a d-link dwa-140 usb wireless stick.
 
Cheers,
Max

---

### Post by bkratz on 2010-02-21
> **drmax said:**
> Thanks Linux_Junkie,
Yes, I did try to install the network with network manager, I do have a signal, but am having problems with the setup screens. After reading the networking forum, it looked like I would need to post some rather long outputs(ifconfig, lsmod, iwconfig, etc.), and so I figured if I could figure out how to use the usb stick, it would save alot of typing. I just assumed I would be asked for some of these outputs, but perhaps I should just go ahead and try to configure the wireless.
 
Greenwidth,
Thanks for your help, I have a linksys wrt160n v3 router, and a d-link dwa-140 usb wireless stick.
 
Cheers,
Max



You might want to look at this thread

[http://ubuntuforums.org/showthread.php?t=1333255&highlight=dwa-140](http://ubuntuforums.org/showthread.php?t=1333255&highlight=dwa-140)

---

