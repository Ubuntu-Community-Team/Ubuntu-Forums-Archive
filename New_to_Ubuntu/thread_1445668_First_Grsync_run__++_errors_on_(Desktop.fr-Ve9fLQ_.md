---
title: "First Grsync run  ++ errors on (Desktop/.fr-Ve9fLQ Permisson Denied (13)) ? Normal"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by mikodo on 2010-04-02
Hello everyone,

I ran my first ever Grsync and received about a Zillion errors like the one below. They all have .fr-Ve9flQ and have /Videos in the line. Is this anything to worry about, or anything that needs fixing?

rsync: send_files failed to open "/home/mikodo/Desktop/.fr-Ve9fLQ/home/mikodo/Videos/var/lib/python-support/python2.4/cherrypy/tutorial/tut06_default_method.py": Permission denied (13)

Thank you.

---

### Post by japhyr on 2010-04-04
I'll share my experience with grsync, not all of which I understand as of yet.  When copying some of my directories, like my home directory, I usually get no errors.  But when I back up some of my root directories, such as /usr/local, /etc, and /var, I often get a lot of errors.  For now, I am assuming there are a bunch of files I don't really need copies of.

I notice these are in a directory preceded by a dot (.fr-Ve9fLQ), which I believe is a configuration directory or something like that.  I also notice it is a .py (python) file, but I don't know what to make of that.

I will be curious to read a more experienced user's response.

---

### Post by captain_rob on 2010-09-26
I have the same experience as the last poster and encounter lot of "Permission denied (13)" messages if I want to backup some root directories.

Are those files perhaps not necessary or do I need to change some Grsync settings to include them?

Pls help. 

 
Example:
rsync: opendir "/var/backup" failed: Permission denied (13)
rsync: opendir "/var/cache/ldconfig" failed: Permission denied (13)
rsync: opendir "/var/cache/system-tools-backends/backup" failed: Permission denied (13)
rsync: opendir "/var/lib/PolicyKit" failed: Permission denied (13)
rsync: opendir "/var/lib/gdm" failed: Permission denied (13)
rsync: opendir "/var/lib/mysql" failed: Permission denied (13)
rsync: opendir "/var/lib/polkit-1" failed: Permission denied (13)
rsync: opendir "/var/log/gdm" failed: Permission denied (13)
rsync: opendir "/var/log/samba/cores" failed: Permission denied (13)
rsync: opendir "/var/run/PolicyKit" failed: Permission denied (13)
rsync: opendir "/var/run/cups/certs" failed: Permission denied (13)
rsync: opendir "/var/run/gdm" failed: Permission denied (13)
rsync: opendir "/var/run/samba/winbindd_privileged" failed: Permission denied (13)
rsync: opendir "/var/run/sudo" failed: Permission denied (13)
rsync: opendir "/var/spool/cron/atjobs" failed: Permission denied (13)
rsync: opendir "/var/spool/cron/atspool" failed: Permission denied (13)
rsync: opendir "/var/spool/cron/crontabs" failed: Permission denied (13)
rsync: opendir "/var/spool/cups" failed: Permission denied (13)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]

---

