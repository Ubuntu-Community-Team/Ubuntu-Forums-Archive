---
title: "How can I use vsftpd for both LAN and WAN simultaneously?"
date: 2015-02-18
forum: Networking &amp; Wireless
---

### Post by nhtrader on 2015-02-18
kubuntu 14.04.1 LTS x64
kde 4.13.3
Qt Version: 4.8.6
vsftpd 3.0.2


My problem is that I can't access my FTP server simultaneously from both LAN and WAN. If I have WAN access, I can't use it on the LAN and if I set it up for the LAN I can't access it from outside the home.

I have a working FTP server, I can access my FTP server away from my home using dynamic DNS (WAN), but then can't use on the home network (LAN)
If I change vsftpd.conf and restart the FTP server, then I can use on the home network (LAN), but then can't use away from the home (WAN).

Here is my vsftpd.conf which is setup for WAN access:

```

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=NO
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES

connect_from_port_20=YES
ftpd_banner=Welcome to TEST
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem

listen_port=99
pasv_enable=YES
pasv_addr_resolve=YES
pasv_max_port=9999
pasv_min_port=9900
pasv_address=my.dynamic.ip.address.com
max_per_ip=6
max_clients=3


```

---

