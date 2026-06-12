---
title: "Wifi drops occasionally"
date: 2016-02-10
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2016-02-10
Folks,

I remotely look after my girlfriend's ubuntu computer using ssh to terminal or an ssh tunnel to VNC.

Trouble is her wifi drops every so oftenand requires her to manually reconnect. She disables wifi then enables and it connectes again automatically.

To try and resolve this I set up a sudo cronjob as followss;

```
15 0,6,12,18 * * * service network-manager restart
```

Don't think that is working though, a check on syslog using 
```
sudo grep CRON /var/log/syslog
```

gives this output 
**Feb 10 08:17:01 carole CRON[25639]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)**

Any comments appreciated,

Geoff

---

### Post by howefield on 2016-02-10
Thread moved to the "*Networking & Wireless*" forum.

---

