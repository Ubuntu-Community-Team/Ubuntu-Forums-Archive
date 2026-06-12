---
title: "Help get Arpwatch setup"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by hansoffate on 2008-09-17
I followed this tutorail to help get arpwatch setup.
[http://24h.atspace.com/it/security/arpwatch.htm](http://24h.atspace.com/it/security/arpwatch.htm)

After a system restart, here is what I have.
jolly@UbuntuBox:~$ ps -ef | grep arpwatch
arpwatch  5399     1  0 15:01 ?        00:00:00 /usr/sbin/arpwatch -i eth0 -f eth0.dat -a -n 169.237.125.0/24 -m ######@#######.edu -u arpwatch -N -p
arpwatch  5570  5399  0 15:01 ?        00:00:00 [arpwatch] <defunct>
jolly     5868  5836  0 15:02 pts/0    00:00:00 grep arpwatch

However, so far there has been nothing written in arp.dat or eth0.dat and there are a good amount of computers on our network.

Any ideas?

Thanks,
Hans

---

### Post by pytheas22 on 2008-09-17
I thought that arpwatch just logs to the normal system log (I don't know what you mean by arp.dat and eth0.dat).  Did you look at /var/log/syslog to see if it recorded anything?

---

### Post by hansoffate on 2008-09-17
> **pytheas22 said:**
> I thought that arpwatch just logs to the normal system log (I don't know what you mean by arp.dat and eth0.dat).  Did you look at /var/log/syslog to see if it recorded anything?

It is finding new stations, but it should be pumping the changes to arp.dat and emailing us.  I just installed sendmail.  I'll try figuring out how to configure it for our campus' smtp server.

```
jolly@UbuntuBox:~$ tail -25 /var/log/syslog
Sep 17 15:01:23 UbuntuBox kernel: [   40.380255] eth0: no IPv6 routers present
Sep 17 15:01:26 UbuntuBox arpwatch: new station 169.237.125.222 0:19:b9:f7:fb:cc eth0
Sep 17 15:01:31 UbuntuBox arpwatch: new station 169.237.125.32 0:18:8b:57:f8:f6 eth0
Sep 17 15:01:31 UbuntuBox arpwatch: execl: /usr/lib/sendmail: No such file or directory
Sep 17 15:01:36 UbuntuBox arpwatch: execl: /usr/lib/sendmail: No such file or directory

```

---

### Post by pytheas22 on 2008-09-17
Yeah, I'd suspect an issue with sendmail--make sure ports are configured correctly on the Ubuntu machine and other networking equipment, etc.

You may also want to look into [OSSEC]("http://ossec.net/"), which will send you email based on ARPwatch events, among lots of other things (you could configure OSSEC to only warn you about ARPwatch stuff if you want), by watching the syslog itself.  OSSEC can also forward snort alerts, which makes it a convenient way to centralize a network-security monitoring system, if that's what you're trying to do.  It takes some work to get configured, but once it's up, OSSEC is a great intrusion-detection system.

---

### Post by hansoffate on 2008-09-17
> **pytheas22 said:**
> Yeah, I'd suspect an issue with sendmail--make sure ports are configured correctly on the Ubuntu machine and other networking equipment, etc.

You may also want to look into [OSSEC]("http://ossec.net/"), which will send you email based on ARPwatch events, among lots of other things (you could configure OSSEC to only warn you about ARPwatch stuff if you want), by watching the syslog itself.  OSSEC can also forward snort alerts, which makes it a convenient way to centralize a network-security monitoring system, if that's what you're trying to do.  It takes some work to get configured, but once it's up, OSSEC is a great intrusion-detection system.

Awesome, ossec sounds perfect. I'll take a look at ossec and try to configure it tomorrow at work (just getting off right now). That is exactly what I'm trying to do, monitor our network for intrusions and what not. 

Thanks for the post.  I'll let you know how it goes tomorrow.

---

### Post by tsoul on 2010-04-06
hey guys I found this blog with guides on setting up ossec as well as arpwatch with mail notification pretty awesome.

h-t-t-p://aimlinux[.com]

thanks

---

