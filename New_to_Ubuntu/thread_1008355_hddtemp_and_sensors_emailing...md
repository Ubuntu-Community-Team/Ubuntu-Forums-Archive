---
title: "hddtemp and sensors emailing.."
date: 2008-12-11
forum: New to Ubuntu
---

### Post by colskinet on 2008-12-11
Hi

I am keen to have a daily report emailed to me showing info from 'hddtemp' and 'sensors'.

What's the best way to go about this?

Graphing it would be a nice option too, but would like to get the system emailing me first.

Thanks in advance

Colin

---

### Post by albinootje on 2008-12-11
For emailing hddtemp, install smartmontools, and look at /etc/smartd.conf

See also : [http://www.cyberciti.biz/tips/howto-monitor-hard-drive-temperature.html](http://www.cyberciti.biz/tips/howto-monitor-hard-drive-temperature.html)

(What do you mean with "info from sensors" ? Are you referring to Conky or some other graphical program showing system-info ?)

---

### Post by albinootje on 2008-12-11
Of course you can also set up a cronjob which emails you the hdd temperature.

Use this to set up the cronjob : crontab -e 

And configuring /etc/aliases and also your MTA (e.g. postfix) that emailing to "root" actually works.

---

### Post by colskinet on 2008-12-11
> **albinootje said:**
> For emailing hddtemp, install smartmontools, and look at /etc/smartd.conf

See also : [http://www.cyberciti.biz/tips/howto-monitor-hard-drive-temperature.html](http://www.cyberciti.biz/tips/howto-monitor-hard-drive-temperature.html)

(What do you mean with "info from sensors" ? Are you referring to Conky or some other graphical program showing system-info ?)

This is a Ubuntu 8.10 server so no GUI..

I would like a mail report showing me the output of "sensors" if possible.

Hope that makes sense!

---

