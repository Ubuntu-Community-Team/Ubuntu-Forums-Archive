---
title: "windows proftpd over samba on ubuntu 7.10"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by psychobeauty on 2008-03-31
i ve made a workgroup between 2 pc the ubuntu to the windows over samba..

but i want to have a folder in the share path to let me put files and go to the proftp..

i have create the folder to go to ftp-shared(which  is the folder of the files that go online) but in the windows pc when i try to put a file in that folder..it outputs the message that i dont have permissions..


how can i make it work??

---

### Post by pault_barrett on 2008-04-01
Hey Psyco,

Try using the command 

chmod -R 777 ftp-shared

That should give full access to that folder

---

### Post by superprash2003 on 2008-04-01
you could also try installing gproftpd a gui for proftpd which allows you to set all permissions etc via a GUI

---

### Post by psychobeauty on 2008-04-01
thanx a lot chmod solve it...

---

