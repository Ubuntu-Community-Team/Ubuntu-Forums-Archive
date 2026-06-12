---
title: "How to recover MYSQL Data?"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by Guruprasad on 2009-10-15
My Ubuntu which had MYSQl-Server crashed due to EXT3 partition errors. I can access all the files from root partition using LIVE CD. I would like to copy the Mysql data using LIVE CD, then reinstall UBUNTU and then restore the MYSQL Data to the newly installed UBUNTU. Can anyone tell me how to do this?

---

### Post by Nandox7 on 2009-10-15
Hey!

Unless you changed something in the MySQL configuration you should have the db's files stored inside '/var/lib/mysql'.
(You can check inside '/etc/mysql/my.cnf' for the param 'datadir' to confirm the location)
Each DB is represented by a folder with the same name, so you just need to copy those and paste them in another mysql instance.

I hope this helps!
:)

---

