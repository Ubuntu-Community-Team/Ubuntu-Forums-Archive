---
title: "vsftpd ports problem"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by rogers45 on 2008-11-28
I have some problem whit my config in vsftpd, the problem is when a trying to open the port 20 in my Router D-link dir-615.

The vsftpd server working great in the lokal network, but not from the outside,

And wen i trying to change the port in the config file from 20 to 21 the server go down

Sorry for my english!

My config:

```
# Put in /etc/vsftpd.conf
# Don't forget to change samurai into your local username
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=samurai
ftpd_banner=Welcome to blah FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/home/ftp
```

And the settings in my router like this:

[IMG]http://pici.se/pictures/ptBKIeUeu.png[/IMG]

---

### Post by rogers45 on 2008-11-28
Bump, some one?

/r

---

