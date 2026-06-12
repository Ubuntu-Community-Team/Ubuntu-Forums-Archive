---
title: "TFTP-HPA help needed"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by w33mhz on 2006-08-14
OK, here's the problem:

I have downloaded and installed the tftp-hpa dameon.  It shows as installed, it also show as to start on boot, but it doesn't.  I can't manually start it either.

---

### Post by dodox on 2006-10-16
Daemon mode

/etc/default/tftpd-hpa
RUN_DAEMON = yes

---

### Post by sdowney717 on 2007-08-15
where do the files go in the filesystem for the tftp-hpa server?
The reason is I wanted to push some bin files into a pap2 phone adapter.

[http://www.angelfire.com/droid/pap2/](http://www.angelfire.com/droid/pap2/)

this shows the general idea

---

### Post by davidgarcin on 2007-11-21
sdowney - 
Typically the files go in /tftpboot, although you may have to set that in the config file:
/etc/default/tftpd-hpa

there should be a line that reads:
OPTIONS="-l -s /tftpboot"

You might also try tftpd, with this how-to, I found it useful even if it didn't entirely work for me (it worked for everyone else though)

[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

Hope that helps.
-Dave

---

