---
title: "Users got login problems"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by ahbb on 2008-12-14
HI,

Some of my users keep in having this problem when they have pinged out, and then try to log in again and there session is open they can get back in.

Then i need to log in and kill there old session before they can log in again.

Is there a way I can increase tty or pty sessions coz i see it's only set at 16.

root@shells:~# cat /proc/user_beancounters
Version: 2.5
       uid  resource           held    maxheld    barrier      limit    failcnt
      119:  kmemsize        4247063    4980141   11055923   11377049          0
            lockedpages           0          0        256        256          0
            privvmpages       20748     102316     102400     102400         10
            shmpages           1945       2617      21504      21504          0
            dummy                 0          0          0          0          0
            numproc              54         69        240        240          0
            physpages         13715      20565          0 2147483647          0
            vmguarpages           0          0      33792 2147483647          0
            oomguarpages      13720      20568      32768      32768          0
            numtcpsock           68         72        360        360          0
            numflock             44         52        188        206          0
            numpty               16         16         16         16       1542
            numsiginfo            0         36        256        256          0
            tcpsndbuf        243704     375628    1720320    2703360          0
            tcprcvbuf        214872     724292    1720320    2703360          0
            othersockbuf       8944      55692    1126080    2097152          0
            dgramrcvbuf           0      12852     262144     262144          0
            numothersock         12         22        360        360          0
            dcachesize            0          0    3409920    3624960          0
            numfile            1238       1532       9312       9312          0
            dummy                 0          0          0          0          0
            dummy                 0          0          0          0          0
            dummy                 0          0          0          0          0
            numiptent            10         10        128        128          0
root@shells:~#

login as: root
root@shells password:
Server refused to allocate pty
stdin: is not a tty

Could i please get help on this.

Thanks

Andrew

---

### Post by cmnorton on 2008-12-16
How do the users log out?

Also, is there anything interesting in /var/log/* (messages, syslog in particular)?

---

### Post by ahbb on 2008-12-20
thanks for the help, the problems was solved.

Andrew

---

