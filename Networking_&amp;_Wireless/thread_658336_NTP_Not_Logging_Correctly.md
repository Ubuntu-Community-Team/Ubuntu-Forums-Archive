---
title: "NTP Not Logging Correctly"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by rodtempleton on 2008-01-04
I've got a box configured as an NTP server for internal use and would like all NTP information to be logged separately in a log file I created called /var/log/ntp.log 

However, even after configuring /etc/syslog.conf with:

ntp.*            /var/log/ntp.log

Nothing is getting written to the file.  I did stop and restart the syslog service, and have also tried rebooting the box functioning as the NTP server as well.

Can anyone shed some light into what I might be doing wrong here?  It seems like a simple thing, but even doing a Google search hasn't brought up anything that's been able to help with this.

Thanks,
Rod

---

### Post by metoor30 on 2008-01-04
There is an -l option to specify a log file for ntpd, I found this in the man pages.

Just add "-l /var/log/ntp.log" in the /etc/init.d/ntp file.  Here is an example of how I did this on my ubuntu box:

start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --startas $DAEMON -- -p $PIDFILE **-l /var/log/ntp.log** -u $UGID $NTPD_OPTS

Find this line in the /etc/init.d/ntp file and make the change.  Then restart ntp.  Hope this helps!

---

### Post by rodtempleton on 2008-01-07
That did get it.  Thank you very much.

Cheers,
Rod

---

