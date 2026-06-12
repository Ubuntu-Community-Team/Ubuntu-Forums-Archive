---
title: "System clock changes on reboot"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by woody3617 on 2009-02-16
I have been following the guides for setting the shutdown and wakeup configuration from both
[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)    and
[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)
which seem to be the most popular guides posted to follow.

I am in Brisbane, Australia (UTC+10) and my system clock is set for local time, which seems to work well with the Mythfrontend and Shepherd grabber schedules.  The output from the mythbackend log file indicates the alarm time the system will wakeup again in local time (see below).  The system shuts down after being idle for 75 seconds as expected and wakes up at the local time as expected to record the next event.  After the backend wakes  I look at the log file and find the time / date entries have advanced +10 hours from my local time which means the system went 10 hours past the recording event, and since there is nothing to do, the machine falls asleep after the prescribed time.  If I startup the Mythfront end on the system the local time is corrected as shown in the mythbackend log file below.

[B]The mythbackend settings are:
[/B]Idle Shutdown Timeout: 75 secs
Max wait for recording: 3 minutes
Startup before rec: 120 secs
Wakeup time format: yyyy-MM-dd hh:mm:ss
Command to set wakeup time: sudo /usr/bin/setwakeup.sh $time
Server halt command: sudo mythshutdown --shutdown
Pre-shutdown check-command: sudo mythshutdown --check[B]

An extract from the mythbackend.log[/B]
... shows the correct local time.date up until the point of reboot (<><><><>)

009-02-16 18:05:36.210 Scheduled 17 items in 0.8 = 0.78 match + 0.03 place
2009-02-16 18:05:45.213 I'm idle now... shutdown will occur in 75 seconds.
Running /usr/bin/setwakeup.sh to set the wakeup time to 2009-02-16 18:13:00
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo 1234807980 > /sys/class/rtc/rtc0/wakealarm
rtc_time    : 18:08:31
rtc_date    : 2009-02-16
alrm_time    : 18:13:00
alrm_date    : 2009-02-16
alarm_IRQ    : yes
alrm_pending    : no
24hr        : yes
periodic_IRQ    : no
update_IRQ    : no
HPET_emulated    : no
DST_enable    : no
periodic_freq    : 1024
batt_status    : okay
<><><><><><><><><>
[COLOR=Magenta]2009-02-17 04:13:54.694[/COLOR] Using runtime prefix = /usr
2009-02-17 04:13:54.803 Empty LocalHostName.
2009-02-17 04:13:54.887 Using localhost value of mythserver
2009-02-17 04:13:55.063 New DB connection, total: 1
2009-02-17 04:13:55.108 Connected to database 'mythconverg' at host: localhost
2009-02-17 04:13:55.153 Closing DB connection named 'DBManager0'
2009-02-17 04:13:55.169 Connected to database 'mythconverg' at host: localhost
2009-02-17 04:13:55.172 New DB connection, total: 2
2009-02-17 04:13:55.174 Connected to database 'mythconverg' at host: localhost
2009-02-17 04:13:55.410 Current Schema Version: 1214
Starting up as the master server.
etc...
2009-02-17 04:14:08.051 UPnpMedia: BuildMediaMap Done. Found 0 objects
[COLOR=Magenta]2009-02-16 18:14:36.839[/COLOR] MainServer::HandleAnnounce Playback
2009-02-16 18:14:36.864 adding: mythserver as a client (events: 0)
2009-02-16 18:14:36.865 MainServer::HandleAnnounce Monitor
2009-02-16 18:14:36.866 adding: mythserver as a client (events: 1)[B]

The setwakeup.sh file[/B]
#!/bin/sh
#$1 is the first argument to the script. It is the time in seconds since 1970
#this is defined in mythtv-setup with the time_t argument

LOG=/var/log/mythtv/mythbackend.log
SECS=$(date -d "$1 $2" "+%s" -u)
echo Running $0 to set the wakeup time to $1 $2 >>$LOG
echo 0 > /sys/class/rtc/rtc0/wakealarm      #this clears your alarm.
echo $SECS > /sys/class/rtc/rtc0/wakealarm     #this writes your alarm
echo "echo 0 > /sys/class/rtc/rtc0/wakealarm" >>$LOG
echo "echo $SECS > /sys/class/rtc/rtc0/wakealarm" >>$LOG
cat /proc/driver/rtc  >>$LOG

Any ideas?

---

