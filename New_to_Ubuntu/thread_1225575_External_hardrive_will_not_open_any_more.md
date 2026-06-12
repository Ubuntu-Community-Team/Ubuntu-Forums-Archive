---
title: "External hardrive will not open any more"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by numbness05 on 2009-07-28
Hi there people.

Very strange but my External hardrive has just decided that it will no longer allow me to view or copy any of its folders in linux...

Seemed to be working fine and then all of a sudden I went to mount it one day and it wouldn't mount.. 

now its seems to be mounting but not letting me go any further then to see my folders.

I know the data is still there as I have had it all up and running in windows (a terrible shame)

Any idea's wha may be causing these issues and how i may go about resolving them please any body?

Many many thank yous!

---

### Post by lisati on 2009-07-28
Stand by for the "did Windows shut down properly?" and "did you use 'safely remove hardware'?" questions!
(That's my best guess at the moment)

---

### Post by nmaster on 2009-07-28
if the issues are intermittent then it could be that the drive is failing. if you want though, you could try storing the data somewhere else and then reformatting.  i've never encountered a problem like this before.

---

### Post by renkinjutsu on 2009-07-28
may be a permissions problem.. have you tried to chown the files yet?

---

### Post by numbness05 on 2009-07-28
nope all been safely removed from windows I have had this problem a few times.. I knew that was coming lol thanks...

---

### Post by numbness05 on 2009-07-28
> **renkinjutsu said:**
> may be a permissions problem.. have you tried to chown the files yet?



Chown? not familiar with it how would I go about using or trying chown please?

---

### Post by renkinjutsu on 2009-07-28
before you go chown'ing things, you should check if you already own the files .. do an ls -l on the directory (once you get it to mount) and it should say your username somewhere in it if you own it.

and chown is used like this ```
chown user:group /path/to/file/or/directory
```

---

### Post by numbness05 on 2009-07-28
Thank you every one for your suggestions I'm aking it that neal.m.master is right and the Hardrive is just on its last legs as its refusing to even mount now and also have difficulties retrieving all data even on windows...

A real shame thats a life times collection of music that i have copied from all my CD's that i no longer own all lost..most upsetting.. 

Thank you once again people....

---

### Post by HotShotDJ on 2009-07-28
> **numbness05 said:**
> A real shame thats a life times collection of music that i have copied from all my CD's that i no longer own all lost..most upsetting.Don't panic... you might be able to recover much of that collection.  About 3 years ago, I successfully recovered a partition full of irreplaceable data using [Recover Is Possible Linux (RIPLinux)]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip/") along with the brilliant application "[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")."

---

