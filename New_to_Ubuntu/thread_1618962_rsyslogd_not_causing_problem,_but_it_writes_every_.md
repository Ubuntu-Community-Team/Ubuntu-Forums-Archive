---
title: "rsyslogd not causing problem, but it writes every couple of seconds"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by mphatyonah on 2010-11-11
Hi 'yall,
  The other day I built a Shuttle XS35 without a hdd or a od with 1G internal memory, and no swap. It is running 10.04.1-64 on a 4G usb drive. Purpose of this box is to provide video to a TV screen. Anyway I notice that when the box was idle the usb drive was being accessed every couple of seconds, endlessly. I ran iotop -o and found rsyslogd to be the primary culprit. It is writing to the usb drive every couple of seconds. Is it filling my usb drive with logs? What the heck is this for and can I make it go away without affecting other parts of the OS? :confused:

---

### Post by toekneewood on 2010-11-11
What do you get if you run any of the following to see what log files is being written to the most
```

tail -f /var/log/messages

```
or
```

tail -f /var/log/syslog

```

---

### Post by toekneewood on 2010-11-11
To see which log files currently are setup with logrotate
```

ls -l /etc/logrotate.d

```

The logrotate utility settings, itself, are configured via the config file logrotate.conf 
```

to view
cat /etc/logrotate.conf
or to edit
sudo nano /etc/logrotate.conf

```

---

### Post by mphatyonah on 2010-11-11
Thank you for replying.

tv@tv-desktop:~$ tail -f /var/log/messages
Nov 11 09:56:07 tv-desktop kernel: [14941.220137] pwrdown, 0x6(BIT6)=71
Nov 11 09:56:09 tv-desktop kernel: [14943.220135] pwrdown, 0x6(BIT6)=71
Nov 11 09:56:11 tv-desktop kernel: [14945.220047] pwrdown, 0x6(BIT6)=71
Nov 11 09:56:13 tv-desktop kernel: [14947.220049] pwrdown, 0x6(BIT6)=71
.....and repeats every 2 seconds

tv@tv-desktop:~$ tail -f /var/log/syslog
Nov 11 10:00:23 tv-desktop kernel: [15197.220103] pwrdown, 0x6(BIT6)=71
Nov 11 10:00:25 tv-desktop kernel: [15199.220117] pwrdown, 0x6(BIT6)=71
Nov 11 10:00:27 tv-desktop kernel: [15201.220117] pwrdown, 0x6(BIT6)=71
.....and repeats every 2 seconds

tv@tv-desktop:~$ ls -l /etc/logrotate.d
total 56
-rw-r--r-- 1 root root 126 2010-04-19 04:56 apport
-rw-r--r-- 1 root root 173 2010-04-15 04:27 apt
-rw-r--r-- 1 root root  79 2010-04-09 10:41 aptitude
-rw-r--r-- 1 root root 135 2010-02-19 01:07 consolekit
-rw-r--r-- 1 root root 248 2010-06-18 11:18 cups
-rw-r--r-- 1 root root 112 2010-04-15 13:24 dpkg
-rw-r--r-- 1 root root 146 2010-05-18 12:42 jockey-common
-rw-r--r-- 1 root root 157 2010-04-30 09:21 pm-utils
-rw-r--r-- 1 root root  94 2010-03-07 00:36 ppp
-rw-r--r-- 1 root root 515 2010-02-24 13:27 rsyslog
-rw-r--r-- 1 root root 166 2010-03-05 14:38 ufw
-rw-r--r-- 1 root root 114 2010-04-29 10:46 unattended-upgrades
-rw-r--r-- 1 root root 106 2010-03-07 04:54 wpa_action
-rw-r--r-- 1 root root 114 2010-03-07 04:54 wpa_supplicant

I see rsyslog is on the list. Does that mean the log file is written over each time it writes? If so, then the log file growing would not be a issue. But I do believe that with rsyslog writing every couple of seconds would prevent a hdd from ever parking or powering down when the computer is not in use. That would be an issue. Is this a bug?

---

### Post by toekneewood on 2010-11-11
I think the log files are appended to and then when they hit the conf settings work (week,month) etc it then creates a *.gz
```

ls -lh /var/log/

```
this will give you a list

If you change some of the following settings you could reduce/stop this.  This is a print screen from my machine
```

twood ~ $ cat /etc/logrotate.conf 
# see "man logrotate" for details
# rotate log files weekly
#weekly
daily

# keep 4 weeks worth of backlogs
rotate 4
rotate 7

# create new (empty) log files after rotating old ones
create

```
you will need to restart the deamon for the settings to take affect

---

### Post by toekneewood on 2010-11-11
Just been watching my logs.  I do not get any log entries every few seconds.  I can't find anything in google from your log files.  This is not normal behaviour.  I will do a bit more digging about and ask some one the lad's in the team.

---

### Post by toekneewood on 2010-11-11
Not sure if these are any good, but here they are anyway.  Got to go home now, so good luck
[http://wolfewebservices.com/blog/mediatomb-log-file-27gb](http://wolfewebservices.com/blog/mediatomb-log-file-27gb)
[https://bugs.launchpad.net/ubuntu/+source/mediatomb/+bug/488318](https://bugs.launchpad.net/ubuntu/+source/mediatomb/+bug/488318)

---

### Post by mphatyonah on 2010-11-12
I opened a new thread in General Help hoping that I can find some help there.  [http://ubuntuforums.org/showthread.php?t=1619788]("http://ubuntuforums.org/showthread.php?t=1619788")

---

### Post by gotliebk on 2011-01-23
I was experiencing the same problem with my XS35 under Fedora.  The culprit is a rather chatty driver line that probably should have been turned off before they posted the driver. 

 I was able to get rid of it by hunting down the offending line of code in rtl_dm.c in the HAL/rtl8192/ directory of the source code and commenting it out.  I then did the usual 

make clean
make all
make install

to reinstall the driver.  Rebooted just make sure the new driver loaded and the message was gone.  There are still a few other annoying log messages coming from the driver but they are not enough of a problem to hunt down.   Hope this helps. 

P.S.  The line you need is precisely line 3838 in the file rtl_dm.c.   It is located in the HAL/rtl8192/ subdirectory.

---

