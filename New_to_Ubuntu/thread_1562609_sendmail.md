---
title: "sendmail"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by marioward1 on 2010-08-27
Hi, 
I've been trying to install sendmail, but have been running into following errors, 

Need to get 0B/3494B of archives.
After unpacking 254kB of additional disk space will be used.
Selecting previously deselected package sendmail.
(Reading database ... 18546 files and directories currently installed.)
Unpacking sendmail (from .../sendmail_8.14.2-2build1_all.deb) ...
Setting up sendmail-bin (8.14.2-2build1) ...

You are doing a new install, or have erased /etc/mail/sendmail.mc.
If you've accidentaly erased /etc/mail/sendmail.mc, check /var/backups.

I am creating a safe, default sendmail.mc for you and you can
run sendmailconfig later if you need to change the defaults.

/etc/init.d/sendmail: line 35: /lib/init/vars.sh: No such file or directory
dpkg: error processing sendmail-bin (--configure):
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of sensible-mda:
sensible-mda depends on sendmail-bin | mail-transport-agent; however:
Package sendmail-bin is not configured yet.
Package mail-transport-agent is not installed.
Package sendmail-bin which provides mail-transport-agent is not configured yet.
dpkg: error processing sensible-mda (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sendmail:
sendmail depends on sendmail-bin; however:
Package sendmail-bin is not configured yet.
sendmail depends on sensible-mda; however:
Package sensible-mda is not configured yet.
dpkg: error processing sendmail (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
sendmail-bin
sensible-mda
sendmail
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas how to get this to work cleanly

---

