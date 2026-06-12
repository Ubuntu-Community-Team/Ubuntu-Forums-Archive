---
title: "Bastille Error while Installing on Ubuntu"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by lwoodtri on 2006-11-09
Hello All,

I get the error listed below on my bastille install when running the generated answer script.  I am not running syslog, but syslog-ng, and it appears the install / hardening is choking on  the syslog version.  

Has anyone seen this and if so what to do to fix?  Thanks in Advance.  

cb

[B]ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 3.0.
ERROR:   open /etc/logrotate.d/syslog failed.
ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 3.0.
# Couldn't append line to /etc/logrotate.d/syslog, since open failed.Executing Temporary Directory Specific Configuration
########################################################
Errors have occurred in the configuration.
Please view the following file for more details:
        /var/log/Bastille/error-log
########################################################


[/B]

---

