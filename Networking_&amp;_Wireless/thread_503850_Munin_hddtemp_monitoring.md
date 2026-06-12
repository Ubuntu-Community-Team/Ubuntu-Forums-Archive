---
title: "Munin hddtemp monitoring"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by tg1 on 2007-07-18
Hi there!

I'm running ubuntu server 7.04 on my server (at home), and have just finished installing Munin.
Have successfully installed the sensors and ip_ plugins, but when I try to add the hddtemp plugin, no graph (no picture at all actually) is displayed. (See attachment.)

hddtemp itself is working "perfectly", and returning temp values like this:
```
/dev/sda: ST3250820AS                             : 35Â°C
/dev/sdb: WDC WD5000AAKS-65TMA0                   : 34Â°C
/dev/sdc: WDC WD5000AAKS-65TMA0                   : 32Â°C
/dev/sdd: WDC WD5000AAKS-65TMA0                   : 33Â°C
/dev/sde: WDC WD5000AAKS-65TMA0                   : 32Â°C
/dev/sdf: WDC WD5000AAKS-65TMA0                   : 34Â°C
/dev/sdg: WDC WD5000AAKS-65TMA0                   : 34Â°C
```

I've also confirmed that this line is present in /etc/munin/plugin-conf.d/munin-node:
```
[hddtemp_smartctl]
user root
```

Also, when I run
*/etc/munin/plugins/hddtemp_smartctl autoconf yes*
it returns this:
*no (no drives known)*

Any ideas?


-TG

---

### Post by dudestir on 2007-08-02
I had a similar issue.

On the munin site there was an updated hddtemp_smartctl plugin that supports SATA drivers.

I downloaded this, moved it into the /usr/share/munin/plugins dir and now I am getting hard drive temperatures.

Hope that helps you.

Dean

---

### Post by tg1 on 2007-08-10
> **dudestir said:**
> I had a similar issue.

On the munin site there was an updated hddtemp_smartctl plugin that supports SATA drivers.

I downloaded this, moved it into the /usr/share/munin/plugins dir and now I am getting hard drive temperatures.

Hope that helps you.

Dean

It worked, thanks. :)

-TG

---

