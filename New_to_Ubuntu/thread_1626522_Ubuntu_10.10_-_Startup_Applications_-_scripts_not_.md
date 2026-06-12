---
title: "Ubuntu 10.10 - Startup Applications - scripts not executing?"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by babybruin on 2010-11-20
hello

Ive recently turned to Ubuntu 10.10 as my primary operating system on my Macbook pro (5,5)

Ive been messing around, getting things set up over the last couple of weeks but one thing I keep running into is startup applications (System->Preferences->Startup Applications)

I have attempted putting several items in there and none seem to be executing.  Most recently, I tried running a terminal command for syndaemon: 

syndaemon -i 1 -d

and nothing appears to happen.  I have had similar problems with other attempts.  I have tried scripts and direct terminal commands.  In each case the scripts/commands execute fine when run manually, but dont seem to be executed when the system starts up.

Ive looked at many forum posts trying to find one that deals with this issue, but none of the cases I found worked for me.

Has anyone had issues like this?

---

### Post by acrazyplayer on 2010-11-20
I'm not quite sure but I just read that for scripts they must be in your "rc" file and also must be made executable. For terminal commands I think that's your problem. Its a command to do in a terminal. When ubuntu starts up its like typing the command on a empty desktop, it wont do a thing becuase its not in a terminal. But I could be and probably am very wrong, good luck

---

### Post by babybruin on 2010-11-20
thanks for the reply, I'll give that a try

---

### Post by kid1000002000 on 2010-11-20
same problem, desktop drapes doesn't load.

The above post makes sense, but it doesn't seem to work for my problem, at least.  I'd be interested in any solutions that come up here as well.

---

