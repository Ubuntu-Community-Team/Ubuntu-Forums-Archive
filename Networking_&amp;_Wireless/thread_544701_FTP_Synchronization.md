---
title: "FTP Synchronization"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by syuusuke on 2007-09-06
Hello,

Does anyone know of a tool that can synchronize a FTP remote directory to a local directory?  For example, any files that has been changed to the remote ftp directory, the software will run on the local machine and syncs the missing files locally without syncing the entire directory thus saving bandwidth.  It's kind of like the "weex" application but the other way around, local pulling from remote ftp directory instead of pushing.  A built in automatic scheduler would be nice also but not part of the requirement.

Can anyone recommend me a software that can do it?  Or has any cool commands I don't know about so I can build a custom script?

Thanks a bunch,

---

### Post by kevdog on 2007-09-06
Id take a look at unison, although I think this requires an ssh (not ftp) connection. (It may be able to work through ftp, Im not sure).

Anyway, its very easy to use, and to make it run at a timed interval, I would add it to your crontab.

It works for me, and even has an optional gui if you want it.  Id recommend compiling from source if you are into such things, but the repository version will also work.
[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

---

### Post by syuusuke on 2007-09-07
thanks for the recommendation but i just found out that the ftp command offers the "newer" switch which definitely help solving my problem.  all i need is to take your advice and use crontab and automate the task.  thanks again.

---

### Post by HermanAB on 2007-09-07
You should look into rsync and lftp.  Lftp can transition directories recursively and will retry until a transfer succeeds.

Cheers,

H.

---

### Post by syuusuke on 2007-09-11
lftp is pretty cool!  i will definitely look into it.  thanks for the suggestion!

---

