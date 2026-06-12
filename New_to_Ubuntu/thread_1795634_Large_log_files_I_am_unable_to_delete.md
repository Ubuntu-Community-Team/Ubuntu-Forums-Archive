---
title: "Large log files I am unable to delete"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by thejoester on 2011-07-03
OK so I have Ubuntu 10.10 installed on a 20GB partition. Recently I had issues where this partition was full and ran out of space. 

After investigating with the Disk Usage Analyzer, I found 13.5 GB of log files in /var/log

the main offenders are:

ufw.log 3.0GB
messages 3.0GB
kern.log 3.0GB
syslog 1.3GB
kern.log.1 1.1GB
messages.1 1.1GB
ufw.log.1 1.1GB

Here are my questions:
Is it normal for these files to get so big?
Is it safe to delete them?
Can I set the logging on these to only log until the file reaches a certain size then purge older entries?
I seem to be unable to delete these files through the file manager, do I need to do this through the terminal using "sudo"?

Thank you,

---

### Post by iponeverything on 2011-07-03
> **thejoester said:**
> OK so I have Ubuntu 10.10 installed on a 20GB partition. Recently I had issues where this partition was full and ran out of space. 

After investigating with the Disk Usage Analyzer, I found 13.5 GB of log files in /var/log

the main offenders are:

ufw.log 3.0GB
messages 3.0GB
kern.log 3.0GB
syslog 1.3GB
kern.log.1 1.1GB
messages.1 1.1GB
ufw.log.1 1.1GB

Here are my questions:
Is it normal for these files to get so big?
Is it safe to delete them?
Can I set the logging on these to only log until the file reaches a certain size then purge older entries?
I seem to be unable to delete these files through the file manager, do I need to do this through the terminal using "sudo"?

Thank you,

I would turn off your iptables logging, that is probably the reason your logs are growing so big.


set your preferences for log log rotation in /etc/logrotate.conf

There is no issue with deleting the logs.

this will delete everything ending in "log" or "1" without prompting:

```

cd /var/log/
sudo \rm *log *1 

```

---

