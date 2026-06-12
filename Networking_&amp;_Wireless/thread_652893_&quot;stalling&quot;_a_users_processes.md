---
title: "&quot;stalling&quot; a users processes"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by spx3 on 2007-12-29
A friend of mine is having an account on one of my servers.
The only problem is,sometimes he has processes that consume lots of bandwidth or,
that consume the cpu of the server.
I would like to know if besides using "renice" re-prioritize his processes ,is there a way
of actually "stalling" them,like freezing them for some ammount of time ?

---

### Post by spd106 on 2007-12-30
Perhaps try limiting the resources available to them via the /etc/security/limits.conf file. See [http://gentoo-wiki.com/SECURITY_Limit_User_Processes](http://gentoo-wiki.com/SECURITY_Limit_User_Processes)

For more direct control I believe you can send signals to processes to stop them, but I haven't tried it. I've only really used kill (and xkill) for non-responding processes.

---

### Post by spx3 on 2007-12-30
I was reffering to stopping the process if stopping means that I have the possibility
of resuming the process with no data loss,just freezing.
is there any SIG I could send in order to do this?

---

### Post by spd106 on 2007-12-31
You probably want to send a SIGSTOP.

E.g. 
```
$ kill -s STOP 11342
```
```
$ kill -s CONT 11342
```
Where 11342 is the pid of the process you want stopped/started. If you don't own the process you'll need sudo access.

See [http://en.wikipedia.org/wiki/SIGSTOP](http://en.wikipedia.org/wiki/SIGSTOP)

---

