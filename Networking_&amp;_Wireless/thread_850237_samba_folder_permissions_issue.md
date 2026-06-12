---
title: "samba folder permissions issue"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by badperson on 2008-07-05
Hi,

I have a network with three machines; ubuntu server, ubuntu desktop and windows laptop. 

I can connect to the server and read the files from both machines, no problem. 

if I create a folder from the server, both of the other machines can read/write to that folder. 

If I create a folder from the laptop, it can read/write, but the desktop is read only, 

If I create a folder from the desktop, it can read/write, but the laptop is read only. 

I tried gksudo nautilus, and changing the permissions of the folder that way, and I tried unclicking "read only" on the windows machine, also permissions in the desktop, but I can't create folders from a client machine that the other client can write to. 

Anyone know how to solve this?

thanks!!
happy fourth. 
bp:guitar:

---

### Post by superprash2003 on 2008-07-05
considering the folder you create would be a subfolder of another folder.. in your ubuntu server change the permissions of the folder such that OTHERS have read and write access.. and apply this to enclosed files..there is an option like that

---

### Post by badperson on 2008-07-05
I"m pretty sure I did that...but it didn't work. 
will try again, thanks. 
bp

---

