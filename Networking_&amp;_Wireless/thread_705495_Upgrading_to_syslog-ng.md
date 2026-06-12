---
title: "Upgrading to syslog-ng"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by clievers on 2008-02-23
Hi everyone,

I have Ubuntu Feisty installed and have recently turned on the remote syslog. I have started playing around with pfsense embedded in an ALIX 2 system (like a WRAP). Anyways, I turned on the remote syslog as storing permanent logs for the embedded pfsense requires a syslog server. So I have this working but I have noticed that everything for remote syslog is placed in the syslog.log file. I want to also start doing remote syslogs between multiple linux machines.

What I want as an end result is to have separate files for each individual machine, so not all remote logs just go into the one syslog.log file. This doesn't seem possible with sysklogd, as there doesn't appear to be a way to filter on a host, like the articles for syslog-ng suggest.

So if I were to upgrade to syslog-ng, I understand that it would remove my sysklogd. What I want to know is if this will delete / screw up my current logging. I have a lot of log files and rotated log files. When an upgrade to syslog-ng is done, will it automatically "import" the log rules and logrotate rules, etc? I haven't used the syslog-ng before, so I'm not sure what it will do.

Thanks very much in advance.
Cheers !!!

---

