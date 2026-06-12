---
title: "How can i recieve syslog data to my ubuntu box?"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by blop on 2007-09-24
Hi all im having some problems with my router and it has an option to send out log files to a syslog server....i know of an application on windows to recieve the messages but not in Ubuntu...

can someone suggest something....i have been looking..

---

### Post by duncs on 2007-09-28
Edit "/etc/default/syslogd" as root and add in '-r' to the SYSLOGD options.

Restart syslogd ("/etc/init.d/sysklogd restart" as root), open your firewall on port 514, then you should see the log info appearing in /var/log/syslog.

  Duncs

---

