---
title: "rsyslog server saves logs from router also in /var/syslog"
date: 2016-05-14
forum: Networking &amp; Wireless
---

### Post by tubos2 on 2016-05-14
I have setup my ubuntu server as syslog server to accept all my logs from my router
and save them in a seperate mikrotik.log file in the /var folder.

Everything works but i notice that all messages are also copied in the /var/syslog logfiles.

Is there a way I can stop having these routermessages in my /var/syslog log?
Below are my config files for syslog.

**/etc/rsyslog.d/mikrotik.conf**
```
$template RouterLog, "/var/log/mikrotik.log":fromhost-ip, isequal, "192.168.2.1" -?RouterLog
& stop
```
[B]
/etc/rsyslog.d/50-default.conf[/B]
```

#  Default rules for rsyslog.
#
# First some standard log files.  Log by facility.
#
auth,authpriv.*         /var/log/auth.log
*.*;auth,authpriv.none      -/var/log/syslog
#cron.*             /var/log/cron.log
#daemon.*           -/var/log/daemon.log
kern.*              -/var/log/kern.log
#lpr.*              -/var/log/lpr.log
mail.*              -/var/log/mail.log
#user.*             -/var/log/user.log


#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
#mail.info          -/var/log/mail.info
#mail.warn          -/var/log/mail.warn
mail.err            /var/log/mail.err


#
# Logging for INN news system.
#
news.crit           /var/log/news/news.crit
news.err            /var/log/news/news.err
news.notice         -/var/log/news/news.notice
#
# Emergencies are sent to everybody logged in.
#
*.emerg                                :omusrmsg:*


#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
    news.err;\
    *.=debug;*.=info;\
    *.=notice;*.=warn   |/dev/xconsole
                                          


```

---

### Post by mcparty2 on 2016-07-19
In /etc/rsyslog.d/ create a file called 10-networkdevices.conf
add the following in there:

```

:fromhost-ip, startswith, "192.168.2.1" /var/log/mikrotik.log
& ~

```

Then restart rsyslog. It should work for you.

I hope this helps

---

