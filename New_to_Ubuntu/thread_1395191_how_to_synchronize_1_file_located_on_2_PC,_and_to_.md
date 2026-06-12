---
title: "how to synchronize 1 file located on 2 PC, and to be updated on a third PC?"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-31
Hello


_PC_mini ubuntu:_ PC has a file on /nfsmount/username/document/mytosync.txt
this pc has clock ntpdated !
 
_PC_portable ubuntu:_ PC has a file on /home/username/document/mytosync.txt
this pc has clock ntpdated !
 
_Pendrive windows XP:_ PC has a file on E:\username/document/mytosync.txt   (pendrive)
this pc of xp has clock ntpdated !


====== 
the file has to be all the time updated on the server, and being the last version : 
_PC_Master Server share:_  /home/username/document/mytosync.txt
this pc has clock ntpdated !


Bit tricky, rsync certainly and an advanced, for xp, rsync-like for windows xp. 

Which parameters for each PC / arguemnts for ubuntu rsync would you use? 
It is very complicated synchronizing  ....  :(

Any hints are welcome !

---

### Post by theozzlives on 2010-01-31
The only thing I can think of is to have the file in one location and share it.

---

### Post by J V on 2010-01-31
Yeah, either that or rsync or you have to build yourself an svn repo xD

---

