---
title: "Memory and cache"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by bartcramer on 2010-04-05
Hi guys, 

I am confused on where the memory goes. 

free -m: 

```

            total       used       free     shared    buffers     cached
Mem:         15880      10498       5382          0       1070       1183
-/+ buffers/cache:       8243       7637
Swap:         3812         45       3766

```

I understand this as: of the 16 GB of memory, 10.5 is used. However, some of it used by cache, so really, only 8.2 is used, leaving 7.6 for remaining processes. 

top gives me only one active process, taking 2.5 GB of memory. However, there might be memory-hungry processes that do not take up CPU, but are waiting for some external event to start working again. So I used ps -eF (it's a multi-user computer) to look after that. However, there is nohing noticeable, except:

```

myusername    658 11871 99 659430 2592644 3 15:41 pts/3   05:30:16 command

```

So, how can I see what is taking the 8.2 - 2.5 = 6.7 GB of memory, if it's not in the cache, and not taken by other active processes? 

Thanks in advance!

---

### Post by r-senior on 2010-04-05
If you run top, then press "f", you get to display any field you like, e.g. "q" toggles resident memory size, "o" toggles virtual image size. Press return to get back to the process view. Pressing "F" allows you to change the sort order in a similar way.

Press "h" for help on additional options in top.

---

### Post by bartcramer on 2010-04-05
Neat trick! I get (when sorting according to "memory usage"): 

```

  658 myusername   18  -2 2575m 2.5g 5556 R  100 15.9 377:44.80  44m 3000 2.5g command                                                                            
 4393 root      20   0  180m  13m 1192 S    0  0.1   1:20.66 167m  136 153m console-kit-dae                                                                  
23815 root      18  -2 76664 3396 2612 S    0  0.0   0:00.03  71m  424  740 sshd                                                                             
11871 myusername   18  -2 17508 2440 1544 S    0  0.0   0:00.04  14m  776 1092 bash                                                                             
23830 myusername   18  -2 17480 2412 1548 S    0  0.0   0:00.10  14m  776 1064 bash

```

So still the mystery is unsolved...

---

### Post by NightwishFan on 2010-04-05
I like this page:
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

I doubt there is anything out of order, but off the top of my head I cannot really see a way to confirm.

---

### Post by bartcramer on 2010-04-05
Good website :)

I did take disk caching into account, though...

---

### Post by NightwishFan on 2010-04-05
In my experience the numbers never seem to add up. ;) I still doubt anything is wrong though.

---

### Post by bartcramer on 2010-04-05
I don't think anything is wrong, but what I would like to know is whether:
- something is actually using that memory, and I can't use it
- that memory is not used, so I can use it

One of the reasons I could think of is that there is some user that I am not allowed to see, and that that user is running a process that does not use CPU, but still uses disk cache. It may be an ignorant suggestion, though.

---

### Post by NightwishFan on 2010-04-05
I suppose the memory is really free. Go by the +/- buffers/cache numbers in free -m. What it says is free is free as far as I am concerned. I will look up the command to list processes.

For more advanced memory usage:
```
cat /proc/meminfo
```

---

### Post by bartcramer on 2010-04-05
So that is the problem: free -m says there is only 8 GB available (in the -/+ cache row!), but there is 16 GB in the machine, and only one process of 2.5 GB running. 

If I'd trust free -m, it means that 5.5 GB has disappeared.

---

### Post by NightwishFan on 2010-04-05
Oh I see! I am so sorry I did not notice that is what you meant. Free is only showing used and free memory, not total in the buffers/cache line. It adds up.
8243+7637=15880

Here is mine, showing all of my 3gb of ram:
```
free -m
             total       used       free     shared    buffers     cached
Mem:          2985       1697       1287          0         73       1067
-/+ buffers/cache:        557       2428
Swap:         4290          0       4290

```

Edit: I need to run some virtual machines or something and start to use some of that RAM. I am still used to being on only 800mb! :D

---

### Post by bartcramer on 2010-04-05
No, it doesn't add up. 

I would think that the memory of all processes would add up to 8243 Mb. However, there is only one process running of 2.5 Gb...

I hope my question becomes clearer now...

---

### Post by NightwishFan on 2010-04-05
Try this command:
```
ps aux
```

Do you have a graphical desktop?

[http://unixlive.editboard.com/general-linux-admin-stuff-f3/memory-usage-retrieval-on-linux-process-wise-and-general-t4.htm](http://unixlive.editboard.com/general-linux-admin-stuff-f3/memory-usage-retrieval-on-linux-process-wise-and-general-t4.htm)
[http://unixlive.editboard.com/general-linux-admin-stuff-f3/how-much-ram-is-used-per-program-t5.htm](http://unixlive.editboard.com/general-linux-admin-stuff-f3/how-much-ram-is-used-per-program-t5.htm)

---

### Post by bartcramer on 2010-04-05
Output of 'ps aux' (replacements to remove usernames): 

```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   4104   312 ?        Ss   Mar28   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   Mar28   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   Mar28   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   Mar28   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   Mar28   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   Mar28   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   Mar28   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   Mar28   0:00 [migration/2]
root        10  0.0  0.0      0     0 ?        S<   Mar28   0:00 [ksoftirqd/2]
root        11  0.0  0.0      0     0 ?        S<   Mar28   0:00 [watchdog/2]
root        12  0.0  0.0      0     0 ?        S<   Mar28   0:00 [migration/3]
root        13  0.0  0.0      0     0 ?        S<   Mar28   0:00 [ksoftirqd/3]
root        14  0.0  0.0      0     0 ?        S<   Mar28   0:00 [watchdog/3]
root        15  0.0  0.0      0     0 ?        S<   Mar28   0:00 [migration/4]
root        16  0.0  0.0      0     0 ?        S<   Mar28   0:00 [ksoftirqd/4]
root        17  0.0  0.0      0     0 ?        S<   Mar28   0:00 [watchdog/4]
root        18  0.0  0.0      0     0 ?        S<   Mar28   0:00 [migration/5]
root        19  0.0  0.0      0     0 ?        S<   Mar28   0:00 [ksoftirqd/5]
root        20  0.0  0.0      0     0 ?        S<   Mar28   0:00 [watchdog/5]
root        21  0.0  0.0      0     0 ?        S<   Mar28   0:00 [migration/6]
root        22  0.0  0.0      0     0 ?        S<   Mar28   0:00 [ksoftirqd/6]
root        23  0.0  0.0      0     0 ?        S<   Mar28   0:00 [watchdog/6]
root        24  0.0  0.0      0     0 ?        S<   Mar28   0:00 [migration/7]
root        25  0.0  0.0      0     0 ?        S<   Mar28   0:00 [ksoftirqd/7]
root        26  0.0  0.0      0     0 ?        S<   Mar28   0:00 [watchdog/7]
root        27  0.0  0.0      0     0 ?        S<   Mar28   0:00 [events/0]
root        28  0.0  0.0      0     0 ?        S<   Mar28   0:00 [events/1]
root        29  0.0  0.0      0     0 ?        S<   Mar28   0:00 [events/2]
root        30  0.0  0.0      0     0 ?        S<   Mar28   0:00 [events/3]
root        31  0.0  0.0      0     0 ?        S<   Mar28   0:00 [events/4]
root        32  0.0  0.0      0     0 ?        S<   Mar28   0:00 [events/5]
root        33  0.0  0.0      0     0 ?        S<   Mar28   0:00 [events/6]
root        34  0.0  0.0      0     0 ?        S<   Mar28   0:00 [events/7]
root        35  0.0  0.0      0     0 ?        S<   Mar28   0:00 [khelper]
root        36  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kstop/0]
root        37  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kstop/1]
root        38  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kstop/2]
root        39  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kstop/3]
root        40  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kstop/4]
root        41  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kstop/5]
root        42  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kstop/6]
root        43  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kstop/7]
root        44  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kintegrityd/0]
root        45  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kintegrityd/1]
root        46  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kintegrityd/2]
root        47  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kintegrityd/3]
root        48  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kintegrityd/4]
root        49  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kintegrityd/5]
root        50  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kintegrityd/6]
root        51  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kintegrityd/7]
root        52  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kblockd/0]
root        53  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kblockd/1]
root        54  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kblockd/2]
root        55  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kblockd/3]
root        56  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kblockd/4]
root        57  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kblockd/5]
root        58  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kblockd/6]
root        59  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kblockd/7]
root        60  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kacpid]
root        61  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kacpi_notify]
root        62  0.0  0.0      0     0 ?        S<   Mar28   0:00 [cqueue]
root        63  0.0  0.0      0     0 ?        S<   Mar28   0:03 [ata/0]
root        64  0.0  0.0      0     0 ?        S<   Mar28   0:00 [ata/1]
root        65  0.0  0.0      0     0 ?        S<   Mar28   0:06 [ata/2]
root        66  0.0  0.0      0     0 ?        S<   Mar28   0:09 [ata/3]
root        67  0.0  0.0      0     0 ?        S<   Mar28   0:16 [ata/4]
root        68  0.0  0.0      0     0 ?        S<   Mar28   0:18 [ata/5]
root        69  0.0  0.0      0     0 ?        S<   Mar28   0:09 [ata/6]
root        70  0.0  0.0      0     0 ?        S<   Mar28   0:05 [ata/7]
root        71  0.0  0.0      0     0 ?        S<   Mar28   0:00 [ata_aux]
root        72  0.0  0.0      0     0 ?        S<   Mar28   0:00 [ksuspend_usbd]
root        73  0.0  0.0      0     0 ?        S<   Mar28   0:00 [khubd]
root        74  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kseriod]
root        75  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kmmcd]
root        76  0.0  0.0      0     0 ?        S<   Mar28   0:00 [btaddconn]
root        77  0.0  0.0      0     0 ?        S<   Mar28   0:00 [btdelconn]
root        80  0.0  0.0      0     0 ?        S<   Mar28   0:41 [kswapd0]
root        81  0.0  0.0      0     0 ?        S<   Mar28   0:00 [aio/0]
root        82  0.0  0.0      0     0 ?        S<   Mar28   0:00 [aio/1]
root        83  0.0  0.0      0     0 ?        S<   Mar28   0:00 [aio/2]
root        84  0.0  0.0      0     0 ?        S<   Mar28   0:00 [aio/3]
root        85  0.0  0.0      0     0 ?        S<   Mar28   0:00 [aio/4]
root        86  0.0  0.0      0     0 ?        S<   Mar28   0:00 [aio/5]
root        87  0.0  0.0      0     0 ?        S<   Mar28   0:00 [aio/6]
root        88  0.0  0.0      0     0 ?        S<   Mar28   0:00 [aio/7]
root        89  0.0  0.0      0     0 ?        S<   Mar28   0:00 [ecryptfs-kthrea]
root        92  0.0  0.0      0     0 ?        S<   Mar28   2:13 [scsi_eh_0]
root        93  0.0  0.0      0     0 ?        S<   Mar28   0:00 [scsi_eh_1]
root        94  0.0  0.0      0     0 ?        S<   Mar28   0:00 [scsi_eh_2]
root        95  0.0  0.0      0     0 ?        S<   Mar28   0:00 [scsi_eh_3]
root        96  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kstriped]
root        97  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kmpathd/0]
root        98  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kmpathd/1]
root        99  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kmpathd/2]
root       100  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kmpathd/3]
root       101  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kmpathd/4]
root       102  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kmpathd/5]
root       103  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kmpathd/6]
root       104  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kmpathd/7]
root       105  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kmpath_handlerd]
root       106  0.0  0.0      0     0 ?        S<   Mar28   0:00 [ksnapd]
root       107  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kondemand/0]
root       108  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kondemand/1]
root       109  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kondemand/2]
root       110  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kondemand/3]
root       111  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kondemand/4]
root       112  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kondemand/5]
root       113  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kondemand/6]
root       114  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kondemand/7]
root       115  0.0  0.0      0     0 ?        S<   Mar28   0:00 [krfcommd]
xxxxxxx    657  0.0  0.0   6236  1720 pts/3    S<+  15:41   0:00 cat ../data/tiger-dev.yy
xxxxxxx    658  100 15.9 2637720 2592660 pts/3 R<+  15:41 477:33 cheap -cm -yy -mrs -default-les -packing=15 -sm=sav-45k.mem -nsolutions=1 -timeout=60 -local-cap=1000 -tsdbdump=/local/xxxxxxx/test/0.37/nv+v1-local-1000/ german_nv_v1.grm
root       900  0.0  0.0      0     0 ?        S<   Mar28   0:39 [kjournald]
root      1034  0.0  0.0  10464   416 ?        S<s  Mar28   0:00 /sbin/udevd --daemon
postfix   1192  0.0  0.0  37020  2180 ?        S    22:39   0:00 pickup -l -t fifo -u -c
root      1757  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kpsmoused]
root      1770  0.0  0.0      0     0 ?        S<   Mar28   0:00 [edac-poller]
wsun      2034  0.0  0.0  23044   420 ?        S<s  Apr01   0:00 /usr/bin/SCREEN.real -c /home/HU/wsun/.screen-profiles/profile
wsun      2035  0.0  0.0  17552   932 pts/1    S<s+ Apr01   0:00 /bin/bash
root      2167  0.0  0.0      0     0 ?        S<   Mar28   0:00 [kjournald]
root      2171  0.0  0.0      0     0 ?        S<   Mar28   0:09 [kjournald]
daemon    2363  0.0  0.0   8180   336 ?        Ss   Mar28   0:00 /sbin/portmap
statd     2392  0.0  0.0  16572   400 ?        Ss   Mar28   0:00 /sbin/rpc.statd
root      3512  0.0  0.0   6488   536 ?        S<s  Mar28   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases eth1
root      3664  0.0  0.0      0     0 ?        S<   Mar28   0:00 [rpciod/0]
root      3666  0.0  0.0      0     0 ?        S<   Mar28   0:00 [rpciod/1]
root      3667  0.0  0.0      0     0 ?        S<   Mar28   0:00 [rpciod/2]
root      3668  0.0  0.0      0     0 ?        S<   Mar28   0:00 [rpciod/3]
root      3669  0.0  0.0      0     0 ?        S<   Mar28   0:00 [rpciod/4]
root      3670  0.0  0.0      0     0 ?        S<   Mar28   0:00 [rpciod/5]
root      3671  0.0  0.0      0     0 ?        S<   Mar28   0:00 [rpciod/6]
root      3673  0.0  0.0      0     0 ?        S<   Mar28   0:00 [rpciod/7]
root      3679  0.0  0.0      0     0 ?        S<   Mar28   0:07 [nfsiod]
root      3684  0.0  0.0      0     0 ?        S<   Mar28   0:00 [lockd]
root      3798  0.0  0.0   3944   216 tty4     Ss+  Mar28   0:00 /sbin/getty 38400 tty4
root      3799  0.0  0.0   3944   216 tty5     Ss+  Mar28   0:00 /sbin/getty 38400 tty5
root      3802  0.0  0.0   3944   216 tty2     Ss+  Mar28   0:00 /sbin/getty 38400 tty2
root      3803  0.0  0.0   3944   216 tty3     Ss+  Mar28   0:00 /sbin/getty 38400 tty3
root      3806  0.0  0.0   3944   216 tty6     Ss+  Mar28   0:00 /sbin/getty 38400 tty6
root      3877  0.0  0.0   4604   276 ?        Ss   Mar28   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog    3914  0.0  0.0  10292   472 ?        Ss   Mar28   0:06 /sbin/syslogd -u syslog
root      3935  0.0  0.0   8204   172 ?        S    Mar28   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      3937  0.0  0.0   6592   284 ?        Ss   Mar28   0:00 /sbin/klogd -P /var/run/klogd/kmsg
103       3958  0.0  0.0  19316   740 ?        Ss   Mar28   0:24 /bin/dbus-daemon --system
root      4010  0.0  0.0  42916   468 ?        Sl   Mar28   0:02 /usr/sbin/ypbind -no-dbus
root      4013  0.0  0.0  13880   388 ?        S<s  Mar28   0:00 /usr/sbin/ntpd
ntpd      4014  0.0  0.0  13880   396 ?        S<   Mar28   0:00 /usr/sbin/ntpd
root      4028  0.0  0.0  44768   472 ?        S<s  Mar28   0:01 /usr/sbin/sshd
root      4149  0.0  0.0  16404   356 ?        Ss   Mar28   0:02 /usr/sbin/automount --pid-file=/var/run/autofs/_home.pid --timeout=300 --ghost /home file /etc/home.map
root      4205  0.0  0.0  16404   352 ?        Ss   Mar28   0:02 /usr/sbin/automount --pid-file=/var/run/autofs/_proj.pid --timeout=300 --ghost /proj file /etc/proj.map
root      4228  0.0  0.0  36380  1572 ?        Ss   Mar28   0:39 /usr/sbin/cfenvd
root      4241  0.0  0.0 105692  1572 ?        Ss   Mar28   0:03 /usr/sbin/cfexecd
root      4341  0.0  0.0  32872   528 ?        Ss   Mar28   0:00 /usr/lib/postfix/master
postfix   4348  0.0  0.0  37068   784 ?        S    Mar28   0:00 qmgr -l -t fifo -u
snmp      4361  0.0  0.0  45876  1580 ?        S    Mar28   3:03 /usr/sbin/snmpd -Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid
gkrellmd  4368  1.3  0.0  58716   672 ?        Ss   Mar28 156:17 /usr/bin/gkrellmd --pidfile /var/run/gkrellmd.pid
105       4390  0.0  0.0  36200  2284 ?        Ss   Mar28   0:56 /usr/sbin/hald
root      4393  0.0  0.0 185328 13968 ?        Ssl  Mar28   1:21 /usr/sbin/console-kit-daemon
root      4456  0.0  0.0  15816   676 ?        S    Mar28   0:10 hald-runner
root      4485  0.0  0.0  28484   300 ?        S    Mar28   0:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event0 /dev/input/event3 /dev/input/event4
root      4513  0.0  0.0  28484   388 ?        S    Mar28   2:24 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      4514  0.0  0.0  28492   296 ?        S    Mar28   0:00 /usr/lib/hal/hald-addon-cpufreq
105       4515  0.0  0.0  26064   308 ?        S    Mar28   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      4522  0.0  0.0  28484   376 ?        S    Mar28   0:08 hald-addon-storage: no polling on /dev/fd0 because it is explicitly disabled
root      4538  0.0  0.0  28356   372 ?        Ss   Mar28   0:00 /usr/sbin/bluetoothd
avahi     4576  0.0  0.0  30252  1152 ?        Ss   Mar28   0:27 avahi-daemon: running [cluster-11.local]
avahi     4577  0.0  0.0  29680   116 ?        Ss   Mar28   0:00 avahi-daemon: chroot helper
root      4604  0.0  0.0  67916   320 ?        Ss   Mar28   0:00 /usr/sbin/cupsd
root      4632  0.0  0.0  33296   248 ?        Ss   Mar28   0:00 /usr/bin/system-tools-backends
daemon    4705  0.0  0.0  10196   204 ?        Ss   Mar28   0:00 /usr/sbin/atd
root      4733  0.0  0.0  13644   380 ?        Ss   Mar28   0:03 /usr/sbin/cron
sgeadmin  4808  0.0  0.0  59648  1488 ?        Sl   Mar28   1:39 /usr/share/gridengine/sge_root_dir/bin/lx24-amd64/sge_execd
root      5103  0.0  0.0   3944   216 tty1     Ss+  Mar28   0:00 /sbin/getty 38400 tty1
root      5693  0.0  0.0  76664  3404 ?        S<s  23:36   0:00 sshd: xxxxxxx [priv]
xxxxxxx   5705  0.0  0.0  76664  1944 ?        S<   23:36   0:00 sshd: xxxxxxx@pts/2
xxxxxxx   5707  0.0  0.0  17468  2376 pts/2    S<s  23:36   0:00 -bash
xxxxxxx   5921  0.0  0.0  14108  1172 pts/2    R<+  23:39   0:00 ps aux
root      7807  0.0  0.0      0     0 ?        S    Apr03   0:00 [pdflush]
root      8021  0.0  0.0      0     0 ?        S    Apr03   0:05 [pdflush]
xxxxxxx  11870  0.0  0.0  23044  1424 ?        S<s  Apr04   0:01 /usr/bin/SCREEN.real -c /home/HU/xxxxxxx/.screen-profiles/profile
xxxxxxx  11871  0.0  0.0  17508  2440 pts/3    S<s  Apr04   0:00 /bin/bash
rwhod    20980  0.0  0.0   6028   576 ?        Ss   20:00   0:00 /usr/sbin/rwhod -i eth1
rwhod    20982  0.0  0.0   6028   448 ?        S    20:00   0:00 /usr/sbin/rwhod -i eth1
root     23183  0.0  0.0  76664   388 ?        S<s  Apr01   0:00 sshd: yyyyyyy [priv]
yyyyyyy  23196  0.0  0.0  76664   276 ?        S<   Apr01   0:00 sshd: yyyyyyy@pts/0
yyyyyyy  23198  0.0  0.0  18740   276 pts/0    S<s+ Apr01   0:00 -bash

```

---

### Post by NightwishFan on 2010-04-05
Odd indeed. I see only a process using 15%. Sorry I could not be of more help. I am primarily a desktop user.

---

### Post by bartcramer on 2010-04-06
That's alright :) 

Anyone else an idea? It seems a fairly basic question...

---

### Post by ibuclaw on 2010-04-06
```

[~] echo "15880 * 0.159" | bc
2524.920

```

The process taking up 15.9% memory is the process that is using 2.5GBs of RAM. ;)

(edit): I take it you have a user named "xxxxxxx" on your system that you setup... As if you aren't aware of it, be very afraid.

Regards

---

### Post by bartcramer on 2010-04-06
Obviously. 

But where did the other 5.5 GB go?

---

### Post by ibuclaw on 2010-04-06
> **bartcramer said:**
> Obviously. 

But where did the other 5.5 GB go?

Have a look at the VSZ (Virtual Set Size) and RSS (Resident Set Size) columns.

VSZ is the virtual memory size of the process, part of which may be in physical memory and part of which may be swapped to disk. RSS is the part which is in physical memory.

Count all VSZ numbers, and it may all add up.

Regards

---

### Post by bartcramer on 2010-04-06
No, it doesn't add up. All VSZ total up to 4.4 GB, still a lot less than the 8.2 reported by free -m.

---

