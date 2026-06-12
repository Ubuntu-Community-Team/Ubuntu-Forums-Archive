---
title: "Ubuntu's version of Event Log?"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by dr.peters12 on 2010-09-05
I'm a long time Windows user who's just switched over to Ubuntu.  And so far, I'm enjoying it!

In Windows, I'd often check the event log for early warnings of system problems.  Which logs should I check in Ubuntu?  Are there any errors that are normal?

---

### Post by ex_isp on 2010-09-05
**Linux Log files and usage**

 => **/var/log/messages** : General log messages
 => **/var/log/boot** : System boot log
 => **/var/log/debug** : Debugging log messages
 => **/var/log/auth.log** : User login and authentication logs
 => **/var/log/daemon.log** : Running services such as squid, ntpd and others log message to this file
 => **/var/log/dmesg** : Linux kernel  ring buffer log
 => **/var/log/dpkg.log** : All binary package log includes package installation and other information
 => **/var/log/faillog** : User failed login log file
 => **/var/log/kern.log** : Kernel log file
 => **/var/log/lpr.log** : Printer log file
 => **/var/log/mail.*** : All mail server message log files
 => **/var/log/mysql.*** : MySQL server log file
 => **/var/log/user.log** : All userlevel logs
 => **/var/log/xorg.0.log** : X.org log file
 => **/var/log/apache2/*** : Apache web server log files directory
 => **/var/log/lighttpd/*** : Lighttpd web server log files directory
 => **/var/log/fsck/*** : fsck command log
 => **/var/log/apport.log** : Application crash report / log file


Hope this helps!


Ex

---

### Post by 7bn on 2010-09-05
I use System > Administration > Log File Viewer - depends on what you want to look at for which log is relevant. You can also quickly cat or tail the logs in /var/log.

---

### Post by dr.peters12 on 2010-09-05
Are errors usually listed as "error" in the logs?  Is there any point to going to /var/log and just grep'n?

Thanks

---

### Post by Rubi1200 on 2010-09-06
grep is a fantastic way of looking for stuff; highly recommended. You can also use egrep and fgrep (see the man pages for more information).

---

### Post by Rubi1200 on 2010-09-06
> **dr.peters12 said:**
> Are errors usually listed as "error" in the logs?  Is there any point to going to /var/log and just grep'n?

Thanks
> Are errors usually listed as "error" in the logs?
Not necessarily; you may have to use other search terms such as fail/failed etc. It also depends on what you are looking for; e.g. authentications attempts, you might search for terms like root, login etc.

---

