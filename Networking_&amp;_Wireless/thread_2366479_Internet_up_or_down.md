---
title: "Internet up or down"
date: 2017-07-18
forum: Networking &amp; Wireless
---

### Post by zkab on 2017-07-18
I want to write a script that checks - every minutes - that my Internet connection is up and logs/mails me the times when it is down.
We have had some problem the last 6 month that our ISP can't keep the connection up and running.
In discussion with our ISP I want to show them the log ...
Please give me some guidelines how to write such a script.

---

### Post by TheFu on 2017-07-18
Common issue.  My notes:

```
internet-up.cron 
#
# cron-jobs for internet connection up
#

MAILTO=root
LOG=/var/log/internet-up.log
SCRIPT=/root/bin/internet-up.sh

*/5 * * * *     root if [ -x $SCRIPT ]; then $SCRIPT >> $LOG fi

```
The actual ping script.
```

#!/bin/bash

# Meant to be run every 5 min and logged to a logfile which gets rotated weekly

PING=`/bin/ping -c 1 8.8.8.8|/bin/grep loss`
NOW=`/bin/date +'%Y%m%d-%H%M%S'`

echo "$NOW      $PING"
```
Don't forget to setup the logrotate.d/ settings
```
/etc/logrotate.d$ more internet-up 
/var/log/internet-up.log {
        weekly
        missingok
        rotate 26
        compress
        copytruncate
        notifempty
        create 640 root root
}

```

---

### Post by zkab on 2017-07-19
Thanks for your elaborate answer.
I did following ... guess I understood you correctly:
```
loke@loke:~$ su
Password: 
root@loke:/home/loke# crontab -l

#
# cron-jobs for internet connection up
#

MAILTO=root
LOG=/var/log/internet-up.log
SCRIPT=/root/bin/internet-up.sh

*/5 * * * *     root if [ -x $SCRIPT ]; then $SCRIPT >> $LOG fi

root@loke:/home/loke# ls -la /root/bin/internet-up.sh 
-rwxrwxr-x 1 root root 203 jul 19 15:04 /root/bin/internet-up.sh
root@loke:/home/loke# cat /root/bin/internet-up.sh 
#!/bin/bash

# Meant to be run every 5 min and logged to a logfile which gets rotated weekly

PING=`/bin/ping -c 1 8.8.8.8 | /bin/grep loss`
NOW=`/bin/date +'%Y.%m.%d-%H:%M:%S'`

echo "$NOW      $PING"

root@loke:/home/loke# ls -l /etc/logrotate.d/internet-up 
-rw-r--r-- 1 root root 167 jul 19 16:26 /etc/logrotate.d/internet-up
root@loke:/home/loke# cat /etc/logrotate.d/internet-up 
/var/log/internet-up.log {
        weekly
        missingok
        rotate 26
        compress
        copytruncate
        notifempty
        create 640 root root
}
```

Some questions though:
1) rotate 26 ... why so many log-files ?
2) MAILTO=root ... how do I get the mail ?

---

### Post by TheFu on 2017-07-19
1) half a year isn't that long.  Handy to have when dealing with my ISP.
2) You need an MTA setup to get email.  All my systems have postfix as a satellite-node and email gets forwarded thanks to common /etc/aliasas setting to the main network email server.

Does /root/bin/internet-up.sh work for root in a shell?

---

### Post by zkab on 2017-07-19
Sounds OK - then I keep rotate 26
I have Thunderbird installed on the same system - how can I route logrotate-mail to Thunderbird ?
Don't quite understand ... '/root/bin/internet-up.sh work for root in a shell' ... when I log in as root I can execute internet-up.sh

---

### Post by TheFu on 2017-07-19
Is the log file getting entries?

Thunderbird isn't an MTA. Sorry.

---

### Post by zkab on 2017-07-19
Yes - it gets entries ... every 5th minutes
```
2017.07.19-16:30:01      1 packets transmitted, 1 received, 0% packet loss, time 0ms
2017.07.19-16:35:01      1 packets transmitted, 1 received, 0% packet loss, time 0ms
2017.07.19-16:40:01      1 packets transmitted, 1 received, 0% packet loss, time 0ms
2017.07.19-16:45:01      1 packets transmitted, 1 received, 0% packet loss, time 0ms
2017.07.19-16:50:01      1 packets transmitted, 1 received, 0% packet loss, time 0ms
2017.07.19-16:55:01      1 packets transmitted, 1 received, 0% packet loss, time 0ms
2017.07.19-17:00:01      1 packets transmitted, 1 received, 0% packet loss, time 0ms
2017.07.19-17:05:01      1 packets transmitted, 1 received, 0% packet loss, time 0ms
2017.07.19-17:10:01      1 packets transmitted, 1 received, 0% packet loss, time 0ms
2017.07.19-17:15:01      1 packets transmitted, 1 received, 0% packet loss, time 0ms
2017.07.19-17:20:01      1 packets transmitted, 1 received, 0% packet loss, time 0ms
2017.07.19-17:25:01      1 packets transmitted, 1 received, 0% packet loss, time 0ms

```

---

### Post by zkab on 2017-07-19
I discovered that postfix was installed by default on my system ...

---

### Post by zkab on 2017-07-20
The script works fine but I have some basic questions ...
1) How do I see that the connection to Internet is lost - log file ?
2) I will try to get postfix working - what is the script mailing - log file ?

---

### Post by TheFu on 2017-07-20
> **zkab said:**
> The script works fine but I have some basic questions ...
1) How do I see that the connection to Internet is lost - log file ?
2) I will try to get postfix working - what is the script mailing - log file ?

Create whatever reporting you like. You have the logs full of time stamped records of up/down status.
My reports look like this:
```
  Using /var/log/internet-up.log ... 
 Period 20170716-062612  - 20170720-110011
  Total Time: 6036 (min) 100.60 (hrs)
  Percent Up Time: 99.93 % 
  Percent Down Time: 0.07 % 
  Total Down Time: 4 min or 0.07 hrs
 Currently: UP

``` Use your imagination.

It isn't the script mailing anything. It is cron. This is the default cron behavior and it mails the output from the command, if there is any.  Controlling cron emails to get only what you want has been solved for decades. There must be hundreds of guides on the internet which explain it.

---

### Post by zkab on 2017-07-20
OK - thanks ... I will start to dig into some tutorials

---

