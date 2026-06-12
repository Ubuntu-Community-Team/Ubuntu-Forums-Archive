---
title: "ntpd starts two instances of the daemon"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by bsh on 2008-09-10
hi

i am on ubuntu 7.04 32bit.
for some reason, after boot, ntp starts two times. once as user ntp, which is correct. the second instance is user root. the two processes try to use the same port obviously, and therefore they can't work and fill my syslog.
when i kill the root process, it starts working.
i have absolutely no idea why it starts up two times, and where do i look for to find the startup.
in different runlevels (rcX.d) i have found ntp, but only once in each runlevel. there must be another place where it is started after boot.

does anyone know where do i find where and how ntpd will be started after reboot? and why it starts two instances?
thanks

---

### Post by kevdog on 2008-09-10
All the runlevels just add symbolic links to the programs they want to start up.  Is ntpd listed twice in runlevel 3 (I think this is the default run level for ubuntu -- I think).

The real scripts (where the symbolic links are pointing) are in /etc/init.d/  There might be a ntp file here or within a ntp subdirectory (Not at computer here to check -- but just look).  If you look at the ntp script, is there any indication the process is called twice within the script?

---

### Post by bsh on 2008-09-10
no, there's only one ntp file in rc3.d (S99ntp)
also no sign of the process starting 2 times in /etc/init.d/ntp either. (well, as far as i can tell). however, the /etc/init.d/ntp script runs the ntp daemon as "user ntp", which is right.
but there is a ntp daemon running too, with user "root", and it used to have nearly the same PID as the other one, usually one higher. so i assume they are ran in consecutive order. so the thing that runs the daemon for the second time must be following the normal ntp startup script.

---

### Post by ksarkies on 2009-03-16
For the record, and to help frantic googlers, it is quite likely that you have listed more than one timeserver, and ntp has not been able to contact one or more of them. It appears to start additional instances for this case. I had three timeservers listed and two could not be contacted. There were two daemons running. By replacing the three timeservers with contactable pool timeservers the number of daemons dropped back to one. Check the timeservers by running ntpdate (this is deprecated but still has its uses). The condition should not be serious as long as there is at least one contactable timeserver.

Ken

---

