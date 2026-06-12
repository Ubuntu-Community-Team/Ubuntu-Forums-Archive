---
title: "Syslog Issue (6.10 Server)"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by Strider on 2007-02-20
Hi all,

I recently installed Ubuntu 6.10 Server.  I wanted to enable syslog remote capabilities so the system can log syslog messages.  I edited /etc/syslog.conf file and changed the following:

```

SYSLOGD="-u syslog"
to
SYSLOGD="-r -u syslog"

```

I restarted the syslog daemon but was not able to capture any remote syslog info.  tcpdump reports that udp/514 was no reachable.  After troubleshooting the issue I found that the "SYSLOGD" options were not being passed to the start-stop-daemon (located in /etc/init.d/sysklogd script).

It turned out that the /etc/init.d/sysklogd file has the following line:
```

test ! -r /etc/default/syslogd || . /etc/default/syslogd

```

runs /etc/default/syslogd which re-writes the SYSLOGD options to "" (none).  

I resolved this by changed the variable in /etc/init.d/syslogd from SYSLOGD to OPTIONS and replace the variable reference within the file.

Not sure if this is by design or not.  I did not find any docs stating to modify /etc/default/syslogd instead of /etc/init.d/syslogd.  At any rate, this resolved my problem I was having.

I hope this is helpful to anyone having a similar issue.  If anyone know why this is the way it is, please let me know.

-Mike

---

### Post by palm101 on 2007-03-19
thank you for the tip.

---

### Post by rdsmf on 2007-05-14
I just wanted to say thanks for find the solution to this problem, VERY GOOD TIP !!!!!!

---

### Post by afternine on 2007-05-24
I have (better said, had)  exactly the same problem. Nice cause investigation, thanx for the tip!

Bye

---

### Post by spiderwort on 2007-06-10
For those of you just stumbling onto this thread, the more correct solution to this issue is to leave the /etc/init.d/sysklogd script alone. Take yourself over to /etc/defaults, and edit the syslogd script. Put your "-u syslog -r" in there.

In fact, if you are at all concerned about security on your system, edit that file anyway (leave off the "-r" if you're not trying to do remote logging), as there is a bug which is causing all syslogging to be run as root in feisty.

See launchpad bug 117309 if you are interested in details. There should be a fix coming out, I just have no idea when.

......................spiderwort

---

### Post by johnnyb0y on 2008-05-13
Just to add to the previous post, the file can be found at:

/etc/default and not /etc/defaults

Full path is /etc/default/syslogd

Thanks for the tip - it worked for me on 8.04 Hardy Heron 64. Been bugging me for a while.

Cheers

JB

---

