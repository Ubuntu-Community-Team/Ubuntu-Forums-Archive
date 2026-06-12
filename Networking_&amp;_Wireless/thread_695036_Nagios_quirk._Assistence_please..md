---
title: "Nagios quirk. Assistence please."
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by DrPestilence on 2008-02-12
Hello!

So at work I'm the crazy guy that is willing to try linux related task's the current one is using Nagios to monitor a server, problem is while I follow the instructions I get to step 7,

"Configure Nagios to automatically start when the system boots.

ln -s /etc/init.d/nagios /etc/rcS.d/S99nagios

**Verify the sample Nagios configuration files.**

/usr/local/nagios/bin/nagios -v /usr/local/nagios/etc/nagios.cfg

If there are no errors, start Nagios. "

and get the following error,

bash: /usr/local/nagios/bin/nagios: No such file or directory

So I did indeed look and lo and behold this directory was not created, I tried just making it mysellf to see if that would help but it didn't have removed redownlaoded and retried , still no go.. Im still using version 6.06 of Ubuntu, might that be the problem?

any help would be great I ahve a hard time troubleshooting linux to being with much less when dealing with compileing things. :D

---

