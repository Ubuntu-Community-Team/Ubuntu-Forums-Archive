---
title: "[SOLVED] Synchronizing a local folder"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by Line on 2008-08-25
Hi
I work on two computers and want to be able to synchronize a local folder. My  idea is to use a FTP-server for exchange. (no need for privacy)

Is there a good solution for this job out there?
Is the FTP idea bad?

Thanks

---

### Post by SpaceTeddy on 2008-08-25
do you want a two sided sync or is there a master and a slave ?
If this is a master/slave situation i'd use rsync (possibly over ssh). That does the job pretty well for me. For a twosided sync i have no idea... maybe someone else can helps there ?

hope it helps :)

---

### Post by Line on 2008-08-25
I am sory for my bad choice of words..
It wold be nice to syncronize a folder with a online server when the day is done, and be able to get acces to the files at home

rsync looks like a nice program :)

---

### Post by SpaceTeddy on 2008-08-25
in this case - rsync. definetly. it is made for exaclty that purpose. I'd suggest you read up on how rsync works... also, i cann supply this [[COLOR="Blue"]link [/COLOR]]("http://troy.jdmz.net/rsync/")to a page that explains how to run rsnapshot over an ssh connection - ok, not exactly what you want, but rsnapshot is only a script that utilizes rsync. So in the end, if that works, rsync will aswell. 

hope it helps :)

---

### Post by Line on 2008-08-29
The problem is sucessfully solved with [ftpsync]("http://sourceforge.net/projects/ftpsync/"), a simple effective script :)

---

