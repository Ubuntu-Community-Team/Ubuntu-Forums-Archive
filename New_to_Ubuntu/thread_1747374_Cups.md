---
title: "Cups"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by bjje on 2011-05-02
When I updated to Natty, I lost my network printers, Printing services not available. Troubleshooter on the printer dialog tells me that CUPS does not appear to be running and to correct this I should run CUPS services under system>administration>services but there is no services under administration (classic desktop).

I've tried to start CUPS as below

> sudo /etc/init.d/cups start
Rather than invoking init scripts through /etc/init.d, use the service
utility, e.g. service cups start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start utility, e.g. start cups
start: Job failed to start


??

---

### Post by Tralce on 2011-05-02
So, have you tried what it told you? 

```
sudo service cups start
```

Also, check for errors in /var/log/cups and post them, if any.

---

### Post by bjje on 2011-05-03
sure and I just get;

> start: Job failed to start
No recent errors since upgrade in  /var/log/cups

Many thanks.

---

### Post by wilddice on 2011-05-04
SOLUTION:

System> Administration > Printers  (in 'classic gnome mode')

Under the Server menu, settings, make sure the printer is published, and allow printing from the internet).

Seems the upgrade turned these settings back off (Bad package managers!!!:p)

---

### Post by bjje on 2011-05-04
(Yes, I'm using classic gnome desktop.)
That's the problem, settings button is greyed out and says, 
 > Printing service not available. Start the printing service on  this computer or connect to another serverWhich does not work as  I reported above. The start service button is greyed out and won't work  in terminal either. I'm set to localhost because there is no cups  server here and we print on network as if local printer. It worked fine before and I  didn't remember to check settings before upgrade. Duh!

---

### Post by Gallando on 2011-05-06
I had the same problem, and solved it with the great explanation at:
[http://islandlinux.org/es/howto/upgrading-ubuntu-breaks-printer-cupsys](http://islandlinux.org/es/howto/upgrading-ubuntu-breaks-printer-cupsys)

---

### Post by bjje on 2011-05-09
I never saw errors in  /var/log/cupsd/error_log but somehow today I was  able to restart cupsd without problems after I updated. I love this  place.

---

