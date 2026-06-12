---
title: "Scheduling Updates to a set time"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by Hariharakadan on 2010-09-09
I'm looking for a way to schedule security / package updates at a certain time of the day. Preferably between the hours of 2:00AM-6:59AM. My isp uses a FAP (Fair Access Policy) and if I was to go over their set limit. (400mb/day) I would be out of service for 24 hours. Thank you.

---

### Post by aeiah on 2010-09-09
set up a cron job. because normally you'd need to use sudo apt-get update etc, you'd want to add it to your root crontab

```

sudo crontab -e
```

then
```

0 1 * * * apt-get update && apt-get -y upgrade

```
this runs it at minute 0, hour 1 of every day (ie, 1:00am)

if you'd like to log any errors you could use -qq (or just -q to log everything) and pipe that to a text file somewhere, eg:

```

0 1 * * * apt-get update && apt-get -y -qq upgrade >> /root/apt.log

```



this is untested

---

### Post by bredman on 2010-09-09
I think aeiah meant to write

0 1 * * * /usr/bin/apt-get update && /usr/bin/apt-get -y upgrade

---

### Post by Hariharakadan on 2010-09-09
Much appreciated folks. I'll be sure to test this tonight. Now I can get some sleep!

---

