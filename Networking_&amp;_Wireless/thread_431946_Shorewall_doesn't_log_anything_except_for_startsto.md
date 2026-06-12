---
title: "Shorewall doesn't log anything except for start/stop"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by beanfield on 2007-05-03
I'm used to shorewall logging in /var/log/messages from past distros, but I don't show any logging information for shorewall actions (except for when I start or stop shorewall).

](*,) 

The only output I get in /var/log/messages:
May  3 13:12:51 alpha:  Shorewall restarted

shorewall v3.2.6-2
1 interface
sysklogd 1.4.1-20ubuntu4

useful lines from shorewall.conf:
```
VERBOSITY=2
LOGFILE=/var/log/messages
LOGFORMAT="Shorewall:%s:%s:"
LOGTAGONLY=No
LOGRATE=
LOGBURST=
LOGALLNEW=
BLACKLIST_LOGLEVEL=
MACLIST_LOG_LEVEL=info
TCP_FLAGS_LOG_LEVEL=info
RFC1918_LOG_LEVEL=info
SMURF_LOG_LEVEL=info
LOG_MARTIANS=No
```

useful lines from policy:
```
#SOURCE         DEST            POLICY          LOG LEVEL       LIMIT:BURST
$FW             net             ACCEPT
net             $FW             DROP            info
net             all             DROP            info
# The FOLLOWING POLICY MUST BE LAST
all             all             REJECT          info
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE
```

my syslogd.conf file
```
#  /etc/syslog.conf     Configuration file for syslogd.
#
#                       For more information see syslog.conf(5)
#                       manpage.

#
# First some standard logfiles.  Log by facility.
#

auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
#cron.*                         /var/log/cron.log
daemon.*                        -/var/log/daemon.log
kern.*                          -/var/log/kern.log
lpr.*                           -/var/log/lpr.log
mail.*                          -/var/log/mail.log
user.*                          -/var/log/user.log
uucp.*                          /var/log/uucp.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.info                       -/var/log/mail.info
mail.warn                       -/var/log/mail.warn
mail.err                        /var/log/mail.err

# Logging for INN news system
#
news.crit                       /var/log/news/news.crit
news.err                        /var/log/news/news.err
news.notice                     -/var/log/news/news.notice

#
# Some `catch-all' logfiles.
#
*.=debug;\
        auth,authpriv.none;\
        news.none;mail.none     -/var/log/debug
*.=info;*.=notice;*.=warn;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none          -/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg                         *

#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#       news.=crit;news.=err;news.=notice;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       |/dev/xconsole
```

Any help on this would be appreciated.

---

### Post by beanfield on 2007-05-03
The output of a shorewall show log

```
# /sbin/shorewall show log
Shorewall-3.2.6 Log at  - Thu May  3 13:50:40 CDT 2007

Counters reset Thu May  3 13:12:51 CDT 2007

#
```

---

