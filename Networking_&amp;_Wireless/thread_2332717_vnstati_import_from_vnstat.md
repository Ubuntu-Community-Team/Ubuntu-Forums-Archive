---
title: "vnstati import from vnstat"
date: 2016-08-03
forum: Networking &amp; Wireless
---

### Post by Drenriza on 2016-08-03
Hi all

is it possible to make a dump from vnstat --dumpdb on one machine and import this into vnstati on another machine to create the summary image?
I cant see anything about this in the man page, but maybe you can pipe it in or something?

The thing is that i dont want to install unnecessary packages from vnstati, and if i could i would like to dump from different systems and than generate
the image on my local machine.

Side note: Anyone know what it means when vnstat says 
> ethX added, 100 Mbit bandwidth limit.
X interfaces added. Limits can be modified using the configuration file
Does vnstat limit the interface to 100Mbit or?
Its not very descriptive.

Thanks on advance!!
Kind regards

---

### Post by Vergo on 2016-08-07
> **Drenriza said:**
> is it possible to make a dump from vnstat --dumpdb on one machine and import this into vnstati on another machine to create the summary image?
I cant see anything about this in the man page, but maybe you can pipe it in or something?
You can export the database on one machine with --exportdb (--dumpdb in older vnStat versions) and import it back on another machine with --importdb (starting from version 1.12). Note that vnstati doesn't support importing by itself so the vnstat command needs to also be available but it's not necessary to have the daemon running if the machine is only used for processing imported databases. Some temporary directory can be used with --dbdir.

> **Drenriza said:**
> Side note: Anyone know what it means when vnstat says 

Does vnstat limit the interface to 100Mbit or?
Its not very descriptive.

The default configuration provided in the package has the 'MaxBandwidth' option set to 100 which result in vnStat mentioning that this is the failsafe limit for that specific interface that was found. Any traffic faster than that gets discarded from vnStat point of view as false / glitch. More recent versions will autodetect the correct value for most interfaces and the message has also been improved. The full documentation is in vnstat and vnstat.conf man pages even in older versions.

---

### Post by Drenriza on 2016-08-25
@Vergo Thanks for the reply!!

---

