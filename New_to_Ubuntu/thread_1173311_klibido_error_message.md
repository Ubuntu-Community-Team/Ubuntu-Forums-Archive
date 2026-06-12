---
title: "klibido error message"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by wiab4355 on 2009-05-29
Hi all

This error message popped from Klibido

"There was an error writing to disk - the download queue has been paused. Chances are that the filesystem is out of space. Correct the error and restart the queue."

But I checked filesystem properties and...

Filesystem properties: Free space 44.3 GB

Does anyone know what's going on?

Ian

---

### Post by yester64 on 2009-10-27
I have the same error. It appears to be the newsgroups database which is broken.
If you rename it and let Klibido create a new one and don't reload the previous session it will run again.
The downside is, that you have to select the newsgroups again since they disappear.
Havent found any clue how to solve it, but that worked at least:-?

There is another thread with the same topic.
[http://ubuntuforums.org/showthread.php?t=539209&highlight=klibido+error](http://ubuntuforums.org/showthread.php?t=539209&highlight=klibido+error)

Just restored the db file again and started it over the console and did only get the error for 'absolute path', every newsgroup is there but queu is empty ????

> **wiab4355 said:**
> Hi all

This error message popped from Klibido

"There was an error writing to disk - the download queue has been paused. Chances are that the filesystem is out of space. Correct the error and restart the queue."

But I checked filesystem properties and...

Filesystem properties: Free space 44.3 GB

Does anyone know what's going on?

Ian

---

