---
title: "Communication between different OS"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by ktat on 2009-06-11
Newbie, needs help!

problem:lovin linux so much I've decided to install 4 different OSs on 2 different HHDs but they're not talkin to each other.  During install my main OS (Jaunty) is on 3 separate partitions.

/
/boot
/home

when installing other OSs I give them 1 partion each ( / ) but also creat mount point for the Jaunty /home partion (i call it /cre8 ).  This is intended to allow me to access all my pic, music, etc from any OS.

Unfortunately, I'm having a problem with permisions.  I would like to be able to read and write to my /cre8 partition from any OS.

Is this possible?

---

### Post by briguy47 on 2009-06-13
> **ktat said:**
> Newbie, needs help!

problem:lovin linux so much I've decided to install 4 different OSs on 2 different HHDs but they're not talkin to each other.  During install my main OS (Jaunty) is on 3 separate partitions.

/
/boot
/home

when installing other OSs I give them 1 partion each ( / ) but also creat mount point for the Jaunty /home partion (i call it /cre8 ).  This is intended to allow me to access all my pic, music, etc from any OS.

Unfortunately, I'm having a problem with permisions.  I would like to be able to read and write to my /cre8 partition from any OS.

Is this possible?


Well, if all of the OS's you're referring to are all Linux based, you could try to right click on the folder you want to share, in Nautilus.  

Then select the Permissions tab.  

Under the "Others" section, you can select "Folder Options" : "Create and Delete Files"

and under "File access" : "Read and Write.

For good measure, I would then click the Apply Permissions to Enclosed Files.

That should allow any os that can understand Unix File Permissions to be able to read and write to that folder and it's contents.


I hope that helps.  Let me know if you have any questions!  :D

---

### Post by ktat on 2009-06-16
Thanks Briguy47 - that works nicely :)

---

### Post by briguy47 on 2009-06-16
Woot!  My pleasure!  :D

---

