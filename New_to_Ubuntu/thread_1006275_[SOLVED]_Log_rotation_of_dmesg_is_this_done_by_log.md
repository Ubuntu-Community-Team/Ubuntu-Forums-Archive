---
title: "[SOLVED] Log rotation of dmesg: is this done by logrotate or dmesg itself?"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by dash86no on 2008-12-09
Hi,

I'm trying to teach myself about syslog and logrotate in prep for the LPIC exam. 

So I look in logrotate.conf:

***************************

# see "man logrotate" for details
# rotate log files weekly
weekly

# keep 4 weeks worth of backlogs
rotate 4

# create new (empty) log files after rotating old ones
create

# uncomment this if you want your log files compressed
#compress

# packages drop log rotation information into this directory
include /etc/logrotate.d

# no packages own wtmp, or btmp -- we'll rotate them here
/var/log/wtmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}

/var/log/btmp {
    missingok
    monthly
    create 0660 root utmp
    rotate 1
}

# system-specific logs may be configured here

************************

And this all looks reasonable: rotate every 4 weeks, create new log files etc. 

So then I take a look in /var/log/ but here I notice dmesg already has several files rotated even though I only installed this copy of Ubuntu a couple of days ago. 

So I'm thinking the answer must be in /etc/logrotate.d/ but I look in there and cant find anything to do with dmesg.

Looking at the size of the dmesg log files I can see that dmesg.0 is 38k and all the compressed dmesg.1 .2 etc are 12k, so I'm guessing these are being rotated based on size and not time. 

Does anyone know what is controlling the dmesg log file rotation?

Cheers

---

### Post by geirha on 2008-12-09
It is not rotated regularly, but rather once each boot. This happens in /etc/init.d/bootmisc.sh. (For the record I didn't know this already, I just did "grep -r dmesg /etc" ;) )

---

### Post by dash86no on 2008-12-09
> **geirha said:**
> It is not rotated regularly, but rather once each boot. This happens in /etc/init.d/bootmisc.sh. (For the record I didn't know this already, I just did "grep -r dmesg /etc" ;) )

ha, the old grep trick. Should have thought of that!

Cheers for the answer.

---

### Post by dash86no on 2008-12-09
> **dash86no said:**
> ha, the old grep trick. Should have thought of that!

Cheers for the answer.

Although looking at the file now, I notice that although kernel messages are being saved into /var/log/dmesg thanks to this script, I don't see any log rotation commands?

---

### Post by geirha on 2008-12-09
```
man savelog
``` :)

---

### Post by dash86no on 2008-12-11
> **geirha said:**
> ```
man savelog
``` :)

Ahh, ok i get it. Thanks for that!

---

