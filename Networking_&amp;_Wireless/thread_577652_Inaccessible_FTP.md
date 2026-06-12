---
title: "Inaccessible FTP"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by rajjpajj on 2007-10-16
Hi everyone,

I have been running a server for about four years now, and recently I switched from Gentoo to Ubuntu 7.04 because I needed to leave it with some folks who didn't really know Linux.
[COLOR="Red"]
I'm running:
Ubuntu 7.04 Feisty Fawn.
VSFTPD
D-Link DIR-625 Router H/W Ver. A1[/COLOR]

Now the FTP is broken. They can access it from the LAN but it is not entirely accessible from outside the LAN. I have the ports forwarded properly and I have also tested it in a DMZ. When it was in DMZ it had the same troubles. **The exact problem I have** is when I connect remotely the FTP lists the root of the FTP and then I can only go one directory deeper. Any further directory changes causes the ftp to stall. I cannot go deeper and I cannot go back "up" directories either.

Here is my **config**:
```
anonymous_enable=NO
allow_anon_ssl=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
anon_upload_enable=NO
ascii_download_enable=NO
ascii_upload_enable=NO
check_shell=YES
chmod_enable=YES
chown_uploads=YES
chown_username=ftpul
chroot_local_user=YES
connect_from_port_20=NO
dirlist_enable=YES
dirmessage_enable=YES
force_local_data_ssl=NO
force_local_logins_ssl=NO
hide_ids=YES
local_enable=YES
passwd_chroot_enable=NO
pasv_enable=YES
ssl_enable=NO
userlist_deny=YES
userlist_enable=YES
userlist_file=/etc/vsftpd.user_list
write_enable=YES

connect_timeout=60
data_connection_timeout=300
file_open_mode=0750
listen_port=21
max_clients=5
max_per_ip=3
#pasv_max_port=
#pasv_min_port=

ftpd_banner=!PRIVATE FTP UNAUTHORIZED USERS NOT PERMITTED!
```

Here is the **connection log in GFTP**:
```
Successfully changed local directory to /home/****
Looking up ***.***.***.***
Trying ***.***.***.***:21
Connected to ***.***.***.***:21
220 !PRIVATE FTP UNAUTHORIZED USERS NOT PERMITTED!
USER *****

331 Please specify the password.
PASS xxxx
230 Login successful.
SYST

215 UNIX Type: L8
TYPE I

200 Switching to Binary mode.
CWD /

250 Directory successfully changed.
Loading directory listing / from server (LC_TIME=C)
PASV

227 Entering Passive Mode (***,***,***,***,193,234)
LIST -aL

150 Here comes the directory listing.
226 Directory send OK.
CWD /software

250 Directory successfully changed.
PWD

257 "/software"
Loading directory listing /software from server (LC_TIME=C)
PASV

227 Entering Passive Mode (***,***,***,***,37,96)
LIST -aL

150 Here comes the directory listing.
226 Directory send OK.
CWD /software/Updates, Patches
```

Thats where it stalls, if I click anymore directories it will just spit out CWD's for each one but it will never actually change the directory.

Any help is *greatly* appreciated!

---

### Post by rajjpajj on 2007-10-18
Well after two days of exhausting trail and error I finally fixed the problem. 

The problem was with my configuration file. The way VSFTPD was handling connection was broken. So I disabled PASV/Passive mode and enable  PORT mode and PORT Promiscuous. It works now!

```
anonymous_enable=NO
allow_anon_ssl=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
anon_upload_enable=NO
ascii_download_enable=NO
ascii_upload_enable=YES
background=YES
check_shell=NO
chmod_enable=YES
chroot_local_user=YES
connect_from_port_20=YES
dirlist_enable=YES
dirmessage_enable=NO
force_local_data_ssl=NO
force_local_logins_ssl=NO
hide_ids=YES
listen=YES
local_enable=YES
nopriv_user=ftpdl
pam_service_name=vsftpd
passwd_chroot_enable=NO
[COLOR="Red"]pasv_enable=NO
pasv_promiscuous=NO
port_enable=YES
port_promiscuous=YES[/COLOR]
secure_chroot_dir=/var/run/vsftpd
ssl_enable=NO
userlist_deny=YES
userlist_enable=YES
userlist_file=/etc/vsftpd.user_list
write_enable=YES
xferlog_enable=YES
xferlog_file=/var/log/vsftpd.log

connect_timeout=60
data_connection_timeout=300
file_open_mode=0750
listen_port=21
max_clients=10
max_per_ip=5
#pasv_max_port=
#pasv_min_port=

ftpd_banner=!PRIVATE FTP UNAUTHORIZED USERS NOT PERMITTED!

rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

```

Hope this helps future peoples.

---

