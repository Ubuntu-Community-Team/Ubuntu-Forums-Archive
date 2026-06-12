---
title: "Trying to learn to read logs"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by spursncowboys on 2009-09-29
Is there a good place that explains the different logs and an explanation of what is in them?

---

### Post by Cypher on 2009-09-29
I think you can poke around /var/log and kinda figure out what's there..:)

The one to start with is /var/log/messages which contains a lot o info, the other files there are broken down based on what the syslog/klog settings are. So you might have /var/log/daemon.log that captures all daemon output and so on.

A couple of other log files don't have any information that's useful or human readable.

I think just looking at /var/log/messages, /var/log/syslog will get you most of what you need..

---

### Post by pedro3005 on 2009-09-29
Try going to System > Administration > Log File Viewer.
Also check out [http://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/](http://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/)

---

### Post by vipulkelkar on 2009-09-29
I was just going thru the files in /var/log
can anyone give a brief idea about the log files
does the dmesg log file store all the events right from the boot.
what do the othr files store

---

