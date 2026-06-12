---
title: "Audacity - WTH?!"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by SPARTAN-118 on 2009-11-07
Okay, I wasn't sure whether to post this in Multimedia Production or Multimedia and Video, so I posted here.

I am trying to do some Voice-overs for an anime adaptation of my favourite online comic, [TwoKinds]("http://twokindscomic.com/").

However, when I try to open Audacity, I get this error: 

"The system has detected that another copy of Audacity running.
Running two copies of Audacity simultaneously may cause data loss or cause your system to crash.

Use the New or Open commands in the currently running Audacity process to open multiple projects simultaneously."

Well, I run ```
ps ax | grep audacity
``` and this is what I get:
```
matthew@ubuntu:~$ ps ax | grep audacity
 6330 pts/0    S+     0:00 grep audacity
```As you can see, Audacity is apparently not running, despite this error message.

I go to System -> Administration -> System Monitor and Audacity is not in the Processes tab. 

So, how do I kill a process that isn't even running?

I'd appreciate any help I can get.

Thanks,
SPARTAN-118

---

### Post by Mrandersonjr on 2009-11-07
Try entering killall audacity in a terminal,and if that doesn't work then restart or you may have to reinstall audacity.

---

### Post by SPARTAN-118 on 2009-11-07
Well, I tried to upgrade to 9.10, but it failed halfway because I didn't have enough disk space (yeah, I know 1Gb isn't a lot, need an external hard drive soon).

So maybe it corrupted Audacity, and I might have to reinstall it.

Will try that, and tell you how it goes.

-SPARTAN-118

---

