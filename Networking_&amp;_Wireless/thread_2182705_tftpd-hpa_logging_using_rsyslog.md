---
title: "tftpd-hpa: logging using rsyslog"
date: 2013-10-22
forum: Networking &amp; Wireless
---

### Post by bloodychaos on 2013-10-22
I installed Xubuntu 12.04 as a dedicated TFTP server a couple of weeks ago to provision configuration files for IP phones. I noticed that the logs are all going to /var/log/syslog. Is there a way I can tweak rsyslog so that the tftpd-hpa logs go to /var/log/tftp.log instead? I tried looking for manuals and guides but I wasn't able to find something relevant. Any help is really appreciated!

Here's my config for tftpd-hpa
```
tftp@MBSTFTPHOTEL:/etc/default$ cat tftpd-hpa
# /etc/default/tftpd-hpa
RUN_DAEMON="yes"
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/tftp"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="-s -c -v"

```

---

