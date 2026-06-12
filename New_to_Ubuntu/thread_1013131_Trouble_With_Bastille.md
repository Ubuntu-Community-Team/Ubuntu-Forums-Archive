---
title: "Trouble With Bastille"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by ArcticWalrus on 2008-12-16
I installed Bastille the other day. I know that it is supposed to be for intermediate to advanced users. I'm a beginner though but my system seems to be functioning the same way as before (no problems). However, the funny thing is... is that it may just have not installed correctly. 

Sorry for the length of this, but I just want to know if it is actually in place or more importantly if there are any problems with my system. 

I can also provide the Action log if needed but it is very long.

This is the error log: 

{Mon Dec 15 16:16:50 2008} Failed to place /psad as /usr/sbin/psad
{Mon Dec 15 16:16:50 2008} Failed to place /psadwatchd as /usr/sbin/psadwatchd
{Mon Dec 15 16:16:50 2008} Failed to place /kmsgsd as /usr/sbin/kmsgsd
{Mon Dec 15 16:16:50 2008} Failed to place /diskmond as /usr/sbin/diskmond
{Mon Dec 15 16:16:50 2008} #ERROR: chmod: File /usr/sbin/diskmond doesn't exist!
{Mon Dec 15 16:16:50 2008} Failed to place /psad-init as /etc/rc.d/init.d/psad
{Mon Dec 15 16:16:50 2008} #ERROR: chmod: File /etc/rc.d/init.d/psad doesn't exist!
{Mon Dec 15 16:16:50 2008} Failed to place /whois as /usr/bin/whois.psad
{Mon Dec 15 16:16:55 2008} ERROR:   open /etc/inittab failed.
{Mon Dec 15 16:16:55 2008} # Couldn't prepend line to /etc/inittab, since open failed.{Mon Dec 15 16:16:55 2008} #ERROR: chmod: File /usr/bin/g++ doesn't exist!
{Mon Dec 15 16:16:55 2008} ERROR:   open /etc/pam.d/xdm failed.
{Mon Dec 15 16:16:55 2008} # Couldn't append line to /etc/pam.d/xdm, since open failed.{Mon Dec 15 16:16:55 2008} ERROR:   open /etc/pam.d/kde failed.
{Mon Dec 15 16:16:55 2008} # Couldn't append line to /etc/pam.d/kde, since open failed.{Mon Dec 15 16:16:55 2008} Bastille tried to use $GLOBAL_BIN{'lppasswd'} but it does not exist.
{Mon Dec 15 16:16:55 2008} #ERROR: chmod: File  doesn't exist!

---

### Post by Hospadar on 2008-12-16
Are you running it as root? It looks like it's failing to modify files that are only modifiable by root.

How are you starting it?

---

### Post by ArcticWalrus on 2008-12-16
> **Hospadar said:**
> Are you running it as root? It looks like it's failing to modify files that are only modifiable by root.

How are you starting it?

I thought of that, I might not have been running it as root. Do you know the command line(s) to restart its modification process as root and fix the errors?

---

### Post by ArcticWalrus on 2008-12-16
Eh, just redid it in root, same errors. Everything seems fine though, some new errors suggest its been working. Thanks for your help.

---

