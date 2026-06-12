---
title: "Unable to connect through ftp on VSFTPD"
date: 2013-11-22
forum: Networking &amp; Wireless
---

### Post by colby.shores on 2013-11-22
[COLOR=#333333]I am unable to connect new user accounts to vsftpd. I have a chroot_list file and a user_list stored in /etc/vsftpd.[/COLOR]
[COLOR=#333333]I believe my vsftpd.conf file is formatted properly. Hopefully someone on here can spot what I am doing wrong.[/COLOR]
[COLOR=#333333]I intend of having users be jailed to their home directories.[/COLOR]

[COLOR=#333333]Thanks in advance[/COLOR]
[COLOR=#333333]Cole

[/COLOR]```
listen=YES
ftpd_banner=Aloha stranger!
write_enable=YES
connect_from_port_20=YES
dirmessage_enable=YES
use_localtime=NO
idle_session_timeout=600
data_connection_timeout=120
pam_service_name=vsftpd
anonymous_enable=YES
anon_upload_enable=NO
anon_mkdir_write_enable=YES
local_enable=YES
local_umask=022
userlist_enable=NO
userlist_deny=NO
userlist_file=/etc/vsftpd/user_list
xferlog_enable=YES
xferlog_std_format=YES
xferlog_file=/var/log/vsftpd/vsftpd.log
deny_email_enable=NO
banned_email_file=/etc/vsftpd/banned_emails
chroot_local_user=YES
chroot_list_enable=NO
chroot_list_file=/etc/vsftpd/chroot_list
local_root=
pasv_max_port=0
pasv_min_port=0
user_sub_token=
nopriv_user=nobody
secure_chroot_dir=/usr/share/empty
```[COLOR=#333333]
[/COLOR]

---

