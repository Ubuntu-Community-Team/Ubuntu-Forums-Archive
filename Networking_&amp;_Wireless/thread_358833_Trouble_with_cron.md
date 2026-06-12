---
title: "Trouble with cron"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by bcardarella on 2007-02-11
I wrote a simple bash script that runs a program (xmltv) that outputs an xml file into my home directory. Everytime it will overwrite the previous copy.

I want this to run in cron so I added to crontab:

00 00 * * * /home/brian/tv_update

The bash script runs perfectly fine if I execute it manually. And I can see in /var/log/syslog that cron is running the job at the appropriate time but the output is not being written. Are there permission issues when cron has to write to a user directory? I set chmod ugo+w on the pre-existing output file but this didn't make a difference. Any help?

---

### Post by moshuptrail on 2007-02-11
For whatever reason, jobs that run from cron do not execute a .profile, so PATH is not set.
You pretty much have to either use full paths for everything in your script, or explicitly set up variables with whatever paths you need.

---

### Post by bcardarella on 2007-02-11
Thank-you that worked.

---

