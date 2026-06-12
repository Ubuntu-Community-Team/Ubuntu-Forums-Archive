---
title: "vsftpd permission denied problem"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by Tony_Pickett on 2013-09-11
I have a local network that i use in my lab (studying for my CCNA)
I have a laptop running Xubuntu 12.10 connected to a number of Cisco boxes.
I have tftp working - at least to the extent that I can copy configs from the laptop to the Cisco boxes, but not the other way - I believe tftp is built that way, so i'm looking at setting up ftp to copy from the Cisco boxes to the laptop.
I have vdftpd running:



```
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
vsftpd  3895 root    3u  IPv4  66637      0t0  TCP *:ftp (LISTEN)

```
The FTP folder is in my home folder as follows:[INDENT]/home/tony/Network/ftp
/home/tony/Network/tftp
/home/tony/Network/www

[/INDENT]
I have the tftp instance running here as well as apache2 and they seem to be happy there.
When I try and copy a config from one of my Cisco boxes, I get this:
```
FRS2#copy nvram: ftp 
Source filename []? startup-config
Address or name of remote host []? 192.168.2.41
Destination filename [frs2-confg]? 
Writing frs2-confg 
%Error writing ftp://192.168.2.41/frs2-confg (Permission denied)
FRS2#

```

And here is the ftp config file (/etc/vsftpd.conf) : (edited out the comments for brevity)


```
listen=YES
#listen_ipv6=YES
# Allow anonymous FTP? (Disabled by default)
anonymous_enable=yes
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
anon_upload_enable=YES
#
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
#xferlog_file=/var/log/vsftpd.log
#idle_session_timeout=600
#data_connection_timeout=120
#nopriv_user=ftpsecure
#async_abor_enable=YES
#ascii_upload_enable=YES
#ascii_download_enable=YES
#ftpd_banner=Hello, this is my FTP - you are not welcome.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#chroot_local_user=YES
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#ls_recurse_enable=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

```

I suspect I need to play with the permissions somewhere, but I have no clue where or what to change.
Anyone point me in the right direction?
Thanks.

---

