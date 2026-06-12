---
title: "chkrookit and dhclient de-mystified"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by idiotsruleintheshowerjane on 2007-11-16
first, my laptop is dying and the keyboard is dying so no caps. 
anyway, i see some talk about chkrootkit annd dhclient and prom. mode. below is a bit
of discovory so you can all relax a bit about the dhclient script(s).

1,) run chkrootkit -d sniffer to see if prom is on or  off
dah@box:/sbin$ sudo chkrootkit -d sniffer
+ [ / != / ]
+ [  != t ]
+ echo ROOTDIR is `/'
ROOTDIR is `/'
+ echo amd basename biff chfn chsh cron crontab date du dirname echo egrep env find fingerd gpm grep hdparm su ifconfig 
inetd inetdconf identd init killall  ldsopreload login ls lsof mail mingetty netstat named passwd pidof pop2 pop3 ps 
pstree rpcinfo rlogind rshd slogin sendmail sshd syslogd tar tcpd tcpdump top telnetd timed traceroute vdir w write
+ /bin/egrep (^|[^A-Za-z0-9_])sniffer([^A-Za-z0-9_]|$)
+ [  != t -a  != t ]
+ printn Checking `sniffer'... 
+ /bin/echo a\c
+ /bin/egrep c
+ 
+ /bin/echo -n Checking `sniffer'... 
Checking `sniffer'... + sniffer
+ [ / != / ]
+ [ Linux = SunOS ]
+ [  = t ]
+ [ ! -x ./ifpromisc ]
+ [  != t ]
+ ./ifpromisc -v
lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[15131])

2.)
is  dhclient  running, yes or no?

dah@box:/sbin$ ps auwx | grep   dhc

root      4435  0.0  1.3   2064   804 ?        Ss   02:30   0:00 /usr/sbin/dhcdbd --system
dhcp     15131  0.0  1.9   2452  1208 ?        S    06:16   0:00 /sbin/dhclient -1 -lf 
/var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient.eth0.pid -q -e dhc_dbus=31 -d eth0
dah      15232  0.0  1.2   2884   752 pts/3    R+   06:17   0:00 grep dhc

3.) do not need pid 4435
dah@box:/sbin$ sudo kill 4435

4.)  and begin to understand child/parent relationships.
dah@box:/sbin$ ps aauwx | grep   dhc
dhcp     15131  0.0  1.9   2452  1208 ?        S    06:16   0:00 /sbin/dhclient -1 -lf 
/var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient.eth0.pid -q -e dhc_dbus=31 -d eth0
dah      15235  0.0  1.2   2884   756 pts/3    R+   06:18   0:00 grep dhc

5.) so stop the pid of 15131 also  ,the ps that is running the dhclient

dah@box:/sbin$ sudo kill 15131

6.) verify that it is stopped
dah@box:/sbin$ ps aauwx | grep   dhc
dah      15240  0.0  1.2   2884   752 pts/3    R+   06:18   0:00 grep dhc

7.) now run chkrootkit -d sniffer again and look for PROM, and it will not be there ;-) 
dah@box:/sbin$ sudo chkrootkit -d sniffer
+ [ / != / ]
+ [  != t ]
+ echo ROOTDIR is `/'
ROOTDIR is `/'
+ echo amd basename biff chfn chsh cron crontab date du dirname echo egrep env find fingerd gpm grep hdparm su ifconfig 
inetd inetdconf identd init killall  ldsopreload login ls lsof mail mingetty netstat named passwd pidof pop2 pop3 ps 
pstree rpcinfo rlogind rshd slogin sendmail sshd syslogd tar tcpd tcpdump top telnetd timed traceroute vdir w write
+ /bin/egrep (^|[^A-Za-z0-9_])sniffer([^A-Za-z0-9_]|$)
+ [  != t -a  != t ]
+ printn Checking `sniffer'... 
+ /bin/echo a\c
+ /bin/egrep c
+ 
+ /bin/echo -n Checking `sniffer'... 
Checking `sniffer'... + sniffer
+ [ / != / ]
+ [ Linux = SunOS ]
+ [  = t ]
+ [ ! -x ./ifpromisc ]
+ [  != t ]
+ ./ifpromisc -v
lo: not promisc and no packet sniffer sockets
eth0: not promisc and no packet sniffer sockets
dah@box:/sbin$ 

8.) test your network and it will still work. ;-)


a word of caution on process id's if you are not familiar with them.  be carefull with the  kill command. read up on process ids. take care not to stop the services you need.    "man  ps" will pull up the manual on process table, assuming you have the default mann page paclage installed. ya prolly do. yup, reading is fun-da-mental ;-)

peace.

- j_k

---

