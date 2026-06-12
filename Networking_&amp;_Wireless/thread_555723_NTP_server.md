---
title: "NTP server"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by elleric on 2007-09-20
Hi, I am pretty new to this so forgive me if i sound foolish anywhere.

I am trying to set up and run a SNTP server on a Ubuntu 7.04 system i have going. I cant seem to find any utilities or packages to help.

Any ideas on what i can do to get this up and running?

thanks,
Elleric

---

### Post by robert_pectol on 2007-09-20
Sure.  Do the following at the command prompt:
```

sudo apt-get install ntp

```
Then, read up a little:
```

man ntpd

```
Then, make a backup of your ntp configuration file:
```

sudo cp /etc/ntp.conf /etc/ntp.conf.bak

```
Finally, modify /etc/ntp.conf to your hearts content, according to the documentation found in the man page listed above, and whatever else you can turn up with an appropriate google search.  Don't forget to reload the ntp daemon after making changes to /etc/ntp.conf:
```

sudo /etc/init.d/ntp restart

```
Good luck!

---

