---
title: "vsftpd and 500 OOPS: child died"
date: 2015-04-12
forum: Networking &amp; Wireless
---

### Post by cdb10 on 2015-04-12
I installed vsftpd.
This is my configuration file /etc/vsftpd.conf:

```

$ cat /etc/
Display all 268 possibilities? (y or n)
pioflor@pioflor-IdeaPad-S210-Touch:~$ cat /etc/vsftpd.conf
anonymous_enable=NO
local_enable=YES
write_enable=YES
chroot_local_user=YES
local_umask=022
# My Config
pasv_enable=YES
pasv_addr_resolve=YES
#user ddns address
pasv_address=ueftptest.no-ip.org
#choose and range you like
pasv_min_port=4242
pasv_max_port=4252

# the list of users to give access
userlist_file=/etc/vsftpd.userlist

# this list is on
userlist_enable=YES
# It is not a list of users to deny ftp access
userlist_deny=NO

#one more
allow_writeable_chroot=YES
seccomp_sandbox=NO


```
This is my configuration file: /etc/vsftpd.userlist
```

$ cat /etc/vsftpd.userlist
ftpuser

```

This is my configuration file: /etc/shells
```

$ cat /etc/shells
# /etc/shells: valid login shells
/bin/sh
/bin/dash
/bin/bash
/bin/rbash
/usr/sbin/nologin


```
This is my configuration file: /etc/pam.d/vsftpd
```

$ cat /etc/pam.d/vsftpd
# Standard behaviour for ftpd(8).
#auth   required        pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

# Note: vsftpd handles anonymous logins on its own. Do not enable pam_ftp.so.

# Standard pam includes
@include common-account
@include common-session
@include common-auth
auth    required        pam_shells.so


```
Furthermore, I did the command:
```

sudo useradd -d /ftp_lenovo -s /usr/sbin/nologin ftpuser
sudo passwd ftpuser
sudo chown -R ftpuser /ftp_lenovo1
sudo chmod 775 /ftp_lenovo1/

```
After all, during I try to log in localhost:
```

$ ftp localhost
Connected to localhost.
500 OOPS: child died

```
What could be the cause of failure?

---

### Post by michi1983 on 2015-04-13
There are some things which are different from the very latest version of vsftpd.
Have you followed this exact tutorial?
[https://help.ubuntu.com/community/vsftpd](https://help.ubuntu.com/community/vsftpd)

---

### Post by cdb10 on 2015-04-14
I changed the configuration file for the recommended [https://help.ubuntu.com/community/vsftpd](https://help.ubuntu.com/community/vsftpd)
```

pioflor@pioflor-IdeaPad-S210-Touch:~$ cat /etc/vsftpd.conf 
 anonymous login 
anonymous_enable=NO 
# Let local users login 
# If you connect from the internet with local users, you should enable TLS/SSL/FTPS 
local_enable=YES
# Write permissions 
write_enable=YES

# 1. All users are jailed by default:
chroot_local_user=YES
chroot_list_enable=NO

# 2. Just some users are jailed:
chroot_local_user=NO
chroot_list_enable=YES
# Create the file /etc/vsftpd.chroot_list with a list of the jailed users.

# 3. Just some users are "free":
chroot_local_user=YES
chroot_list_enable=YES
# Create the file /etc/vsftpd.chroot_list with a list of the "free" users.

userlist_deny=NO
userlist_enable=YES
userlist_file=/etc/vsftpd.allowed_users

# Useful to not write over hidden files:
force_dot_files=YES

# Hide the info about the owner (user and group) of the files.
hide_ids=YES

# Connection limit for each IP:
max_per_ip=2

# Maximum number of clients:
max_clients=20

pasv_min_port=12000
pasv_max_port=12100


ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
# Filezilla uses port 21 if you don't set any port
# in Servertype "FTPES - FTP over explicit TLS/SSL"
# Port 990 is the default used for FTPS protocol.
# Uncomment it if you want/have to use port 990.
# listen_port=990
pioflor@pioflor-IdeaPad-S210-Touch:~$ 
pioflor@pioflor-IdeaPad-S210-Touch:~$ sudo service vsftpd restart
stop: Unknown instance: 
vsftpd stop/waiting
pioflor@pioflor-IdeaPad-S210-Touch:~$ 



pioflor@pioflor-IdeaPad-S210-Touch:~$ ftp localhost
ftp: connect: Connection refused
ftp> 

```

---

