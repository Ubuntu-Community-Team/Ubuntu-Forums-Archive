---
title: "vsftpd &amp; chroot driving me nuts !!!!"
date: 2015-02-18
forum: Networking &amp; Wireless
---

### Post by Raptor Ramjet on 2015-02-18
Hello,

I've set up vsftp semi successfully on Ubuntu server 14.10 and am now trying to disallow users from leaving their home directories but no matter what I try as soon as I log in with Puttys "SFTP" I can "cd.." up the directory tree.

A condensed verson of my vsftp.conf file is as follows (all comments removed):

```

listen=NO
listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
idle_session_timeout=600
data_connection_timeout=120
ftpd_banner=Blah, blah, blah...
chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
allow_writeable_chroot=YES
passwd_chroot_enable=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
rsa_private_key_file=/etc/ssl/private/vsftpd.pem
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
require_ssl_reuse=NO
ssl_ciphers=HIGH

```

I've currently got two ftp users set up ("ftptest1" with a home directory of "/home/ftptest1" and "ftptest2" with a home directory of "/home/ftpuser2") and have put "ftptest1" in the "/etc/vsftpd/chroot_list" file.  

```

ftpuser1

```

However no matter whether I set "chroot_list_enable=YES" or "chroot_list_enable=NO" *both* users can log in and then *both* users can use "cd.." to walk up the directory tree into "/home".  I was expecting that at least one of the users would be successfully chrooted !

And yes I have restarted the vsftpd server between config file changes :)

This is totally frustrating as has wasted the best part of two evenings so far !!! 

So if anyone could point out where I'm going wrong I'd be most grateful ?

Thank you.

---

