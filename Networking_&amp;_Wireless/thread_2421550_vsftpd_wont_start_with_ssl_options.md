---
title: "vsftpd wont start with ssl options"
date: 2019-06-23
forum: Networking &amp; Wireless
---

### Post by mikasu on 2019-06-23
Hello, I had a ftp server setup for a long time and I wanted to try setting up TLS connection again. Though, something unexpected happens with the server. I can't start it with the SSL options active in the vsftpd.conf file but when the server is already running (without the SSL variables) and I uncomment all the SSL related options and simply do :```
sudo service vsftpd reload
``` vsftpd reloads without stopping and SSL is now active and I can do TLS connections.
It is a quite unpractical setup as I would have to always do this little manipulation whenever the server suddently stops or when I reboot my physical server (it's actualy a laptop running a desktop Ubuntu release with all unnecessary programs removed). Here is my vsftpd.conf :
```
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=NO
# Uncomment this to allow local users to log in.
local_enable=YES
# Uncomment this to enable any form of FTP write command.
write_enable=YES
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=022
# Make sure PORT transfer connections originate from port 20 (ftp-data).
#connect_from_port_20=YES
# You may override where the log file goes if you like. The default is shown
# below.
xferlog_file=/var/log/vsftpd.log
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
# When "listen" directive is enabled, vsftpd runs in standalone mode and
# listens on IPv4 sockets. This directive cannot be used in conjunction
# with the listen_ipv6 directive.
listen=YES
#
# This directive enables listening on IPv6 sockets. To listen on IPv4 and IPv6
# sockets, you must run two copies of vsftpd with two configuration files.
# Make sure, that one of the listen options is commented !!
listen_ipv6=NO
#
allow_writeable_chroot=YES
# change root
user_sub_token=$USER
local_root=/home/$USER
#
listen_port=198
#
utf8_filesystem=YES
# pasv
pasv_enable=YES
pasv_min_port=20000
pasv_max_port=22000
# SSL
rsa_cert_file=/etc/ssl/private/vsftpd.pem
rsa_cert_key_file=/etc/ssl/private/vsftpd.pem
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=NO
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
require_ssl_reuse=NO
ssl_ciphers=HIGH
#
# whitelist
#userlist_enable=YES
#userlist_file=/etc/vsftpd.userlist
# when userlist_deny is set to NO, it is a whitelist
# when userlist_deny is set to YES, it is a blacklist
#userlist_deny=NO
```
I know it is still full of junk and some annotations that makes sense only for me. I read many forums online and so far I can't find the problem with my settings. Any of you, experienced users of vsftpd, have an idea why I have to do that manipulation in order to get TLS working?

---

### Post by TheFu on 2019-06-23
Why not use **openssh-server** with sftp instead?  Pretty much any Unix file manager understands the sftp:// URL and will honor ssh-keys.  So, you get easier use, better security, and much more convenience.

---

### Post by mikasu on 2019-06-24
I use these sometimes but, I don't know, I don't like it much since it gives the whole tree of the server and not only the user files... Though, I do have openssh-server installed and running so I can use that but if you have any suggestions of fixes for the vsftpd, I won't complain.
By user files I mean that the root of the "ftp server" is the root of the server and not the user's home directory

---

### Post by mikasu on 2019-06-24
Not only that, but I would also need to be able to prevent some users from being able to login from ssh so a user can't connect using either a regular linux bash or PuTTY and execute malwares after uploading them. With my current setup, I can prevent more public users from being able to use the shell (with a "ftponly" script recognized as a valid terminal that only echoes "This account is for FTP only" and prevents anyone from executing anything on these users.)
If there are options for that with the OpenSSH Server, I would gladly try them but I would like to know where I can get the infos to set it up.

---

### Post by TheFu on 2019-06-24
Sorry, I don't know the answer for any plain FTP server. Haven't set one up in over 20 yrs.  If you wait, someone else should try to help.

openssh can allow specific users access only to the sftp-server and it can limit access to specific directories, based on the userid.

The  sshd_config and sftp-server manpages explain how.
[https://www.digitalocean.com/community/tutorials/how-to-enable-sftp-without-shell-access-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-enable-sftp-without-shell-access-on-ubuntu-16-04) has a guide.

The only trick is that the **Match User** stanzas need to be at the bottom of the file. 1 for each user, if you need them to have access to different locations.  I wouldn't allow password authentication after the initial setup is completed - or only from a specific subnet on your company LAN.  Over the internet, only allow key-based authentication.  **Match Address** is the stanza that lets you have settings by different subnets.

---

### Post by mikasu on 2019-06-24
Thanks, I'll look into sftp on a vps/vm to see if that's a setup that I could do for myself. It seems like a good alternative in case there's no solutions for vsftpd. It is also quite a bit more understandable. That said, I still take inputs for vsftpd, but thanks a lot for those infos :)

---

### Post by mikasu on 2019-06-29
Seems like sftp is the way to go! It worked well on my vm and I set it  up on my server Pavilion g6. I messed up and my server is stuck on a  broken pipe at the moment... but I should be able to reboot it soon so  that's not a big problem. I did a typo and upon fixing it, I triggered a  broken pipe but the settings are good. Thanks a lot for that suggestion  and the informations and documentation you provided :D

---

### Post by mikasu on 2019-07-01
I have an issue now... my ssh and sftp don't work at all. Filezilla wont connect to the server (loosing connection) and ssh will give this error : ```
packet_write_wait: Connection to XXX.XXX.XXX.XXX port XXXX: Broken pipe
``` (I sensored the sensitive informations obviously) I browsed everywhere and I can't find any fixes for that. The server and the client got both rebooted and the pipe is still broken...

---

### Post by mikasu on 2019-07-01
Nevermind, chroot issue. I wish I could do writable chroot, because changing my whole server's file structure will be a hard task... might only do it partially. Thanks a lot, that'll be usefull once I make another server :)

---

