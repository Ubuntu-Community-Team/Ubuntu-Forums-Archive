---
title: "ubuntu server"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by jj3502 on 2010-01-13
hi,

im trying to setup a ubuntu server (using the desktop 9.10 edition, becaues im new and just starting to learn commands) 

the computers on the network are windows (except for my ubuntu netbook, that won't need to be connected)

the computers are:
windows vista sp2
windows 7 (mine!)
windows xp pro sp3
windows xp pro sp3

(im using ubuntu because i don't want to pay micro$oft the $$$ for  window$ server)

i want the server to be a:

print server
file server (not protected, every one has read write access to one folder)

--------------------------------------------------

when i set up the computer the screen res was set, i was able to set up vnc and conect to it, and remove the monitor but, now i cant change the res is there any way i can (without picking up my monitor and connecting it just to change the res).

--------------------------------------------------

thx in advance! :P

---

### Post by HermanAB on 2010-01-13
Hmm, well, VNC is mostly a Windows thing.  On Linux, VNC is almost always the wrong solution.  Install ssh-server (if you installed Ubuntu server version then it is likely already installed and running).  Then connect to it with:
$ ssh user@server gnome-panel

and go click happy.

---

### Post by jj3502 on 2010-01-13
vnc is woking fine (unless the res in a **big** problem) and i have installed open ssh-server on server and putty on my pc and its all working fine

my main problem is setting up the print and file server to work with windows, all the windows comps see each other but not the Ubuntu box but Ubuntu sees the windows comps

---

### Post by jj3502 on 2010-01-13
ok i got windows to see the server, YAY!

in the attached image is the server rdc and windows looking at the server.

The blue is the linked share that i want to rename.

The red is two test folders that i deleted on the server how do i get rid of them on the network?

:confused:

---

### Post by dmillerct on 2010-01-13
> **jj3502 said:**
> ok i got windows to see the server, YAY!

in the attached image is the server rdc and windows looking at the server.

The blue is the linked share that i want to rename.

The red is two test folders that i deleted on the server how do i get rid of them on the network?

:confused:

On the ubuntu box, when you right click on the folder labeled "server file share", select properties and all the way to the right there should be a "share" tab. You should be able to rename the share there.

---

### Post by jj3502 on 2010-01-13
every thing is working now! thanks for the help everyone :)

---

