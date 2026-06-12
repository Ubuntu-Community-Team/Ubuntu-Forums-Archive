---
title: "[SOLVED] Vsftp ntfs --bind mount problem"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by Plasma_NZ on 2008-08-28
Ok running vsftp, login required etc..

I've tried sharing some mounted ntfs drives like so, hasn't work, as flashFXP cant access them but can every other folder..

> # Put in /etc/vsftpd.conf
# Don't forget to change samurai into your local username
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=NO
listen_port=20
chown_uploads=NO
chown_username=ftp
ftpd_banner=Welcome to blahblah-more-bla FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/var/ftp/

made a folder in /var/ftp/ 

then made a folder inside /var/ftp/ntfs-drive1

then mounted /media/sdd5/ to /var/ftp/ntfs-drive using

```
sudo mount --bind /media/sdd5 /var/ftp/ntfs-drive1
```

then access the ftp and it can enter the folder.. permissions for the folder are 777, didnt help, tried 755, didnt help..

Any ideas ?

---

