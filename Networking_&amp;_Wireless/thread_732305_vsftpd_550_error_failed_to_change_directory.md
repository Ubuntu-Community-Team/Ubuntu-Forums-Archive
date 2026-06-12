---
title: "vsftpd 550 error failed to change directory"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by bturrie on 2008-03-22
I've read lots of posts on this problem no help so far. I'm running vsftpd on a kubuntu feisty system. I can call ii up using firefox at [ftp://escher.turriehome.com](ftp://escher.turriehome.com). when I do that i see the index of ftp... but nothing else. The sub directories under /var/ftp do not appear.


if i try to enter one of the directories that i can't see I get

"550 error failed to change directory"

and this in my vsftpd.log file

Sat Mar 22 18:10:00 2008 [pid 12800] [ftp] OK LOGIN: Client "192.168.1.8", anon password "<no_password>"
Sat Mar 22 18:10:00 2008 [pid 12802] [ftp] FAIL DOWNLOAD: Client "192.168.1.8", "/ spool", 0.00Kbyte/sec

I've inactivated my firewall and done a

chmod 777 /var/ftp

here's my vsftpd.conf

listen=YES
anonymous_enable=YES
anon_world_readable_only=NO
local_enable=YES
no_anon_password=YES
write_enable=YES
anon_upload_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_file=/var/log/vsftpd.log
chroot_local_user=NO
ls_recurse_enable=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

I'm running out of ideas. What am I missing here?

---

