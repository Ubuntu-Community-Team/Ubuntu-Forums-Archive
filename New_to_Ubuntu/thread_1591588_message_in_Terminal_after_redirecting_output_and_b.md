---
title: "message in Terminal after redirecting output and build completes?"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by T. Jump on 2010-10-09
I'm not sure about the following behavior so thought I would put it  out to see if there is an error I need to resolve, or simply a process  that I need explained.


I'm also not sure if this is an Ubuntu issue, a Linux issue, or other... but here goes.


 I ran my "make build" in two different ways; one with just "make build" and one with "make build > output" (so I could review the full script).

 
 With just "make build" the process finished and returned to the command prompt.
 

With "make build > output", after the process had finished (script  in output document identical to what was in the terminal with "make  build") a new set of data was displayed in the terminal (see below).


With the other examples of using "make build > output" the times it would parse something back to the terminal window was when there was an error. As I fixed the errors these breaks back to the terminal window would stop. So I'm wondering if this indicates a new error, but because the "make build" now completes successfully (at least it appears to), I'm wondering if this data in the terminal window is just a behavior related to redirecting the output script using the  ">" process and something to do with returning to the terminal once a process completes.


 I would appreciate any feedback here.


 T. Jump






srv1bf537@ubuntu:~/srv1-linux-read-only$ make build > output6
1562 entries written to /home/srv1bf537/srv1-linux-read-only/uClinux/staging/usr/share/terminfo
make[5]: warning: jobserver unavailable: using -j1.  Add `+' to parent make rule.
make[5]: warning: jobserver unavailable: using -j1.  Add `+' to parent make rule.
make[5]: warning: jobserver unavailable: using -j1.  Add `+' to parent make rule.
make[5]: warning: jobserver unavailable: using -j1.  Add `+' to parent make rule.
This is not dpkg install-info anymore, but GNU install-info
See the man page for ginstall-info for command line arguments
Entries that will be compiled:
1:linux
2:vt100
3:vt220
4:xterm
4 entries written to /home/srv1bf537/srv1-linux-read-only/uClinux/romfs/usr/share/terminfo
Guessed module directory as /home/srv1bf537/srv1-linux-read-only/uClinux/romfs/lib/modules/2.6.28.10-ADI-2009R1.1-svn26
srv1bf537@ubuntu:~/srv1-linux-read-only$

---

### Post by NIN101 on 2010-10-09
```
make build > output 2> /dev/null
```
Usually, error messages are written to stderr. If you redirect them with 2>, you shouldn't see them on the terminal anymore.

---

