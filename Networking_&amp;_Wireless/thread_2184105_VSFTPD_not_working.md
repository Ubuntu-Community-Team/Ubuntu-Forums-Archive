---
title: "VSFTPD not working"
date: 2013-10-27
forum: Networking &amp; Wireless
---

### Post by jplamb13 on 2013-10-27
Hi all,


I am having trouble with VSFTPD and Ubuntu, I have installed it multipul times and changed the vsftpd.conf settings too many times to count. When ever i try to ftp in to the machine using filezilla on a local windows pc it comes back as fails saying 
```

Status:    Connecting to 192.168.1.19:21...
Status:    Connection established, waiting for welcome message...
Response:    220 Welcome to opensly FTP.
Command:    USER lambnet
Response:    530 Permission denied.
Error:    Could not connect to server

```


I have followed many guides online but nothing seems to work, 


My current vsftpd.conf file looks like this 


```
# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Disabled by default)
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#anon_umask=027
#anon_other_write_enable=YES


#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=027
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
chown_uploads=YES
chown_username=www-data
file_open_mode=0777
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
ftpd_banner=Welcome to opensly FTP.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES


#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd




# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/private/vsftpd.pem


chmod_enable=YES
dirlist_enable=YES


userlist_enable=YES
tcp_wrappers=YES
userlist_deny=NO



```


As i have said i have changed this loads of times and keep setting it back to the original copy so i am sort of hoping that i am missing something simple. I have checked that the firewall is not stopping anything and then changed the owner of the folder Etc but no luck. anybody got any ideas?


Many thanks

---

### Post by Lars Noodén on 2013-10-28
If you are looking for a way to make secure file transfers for system users, then you might look at SFTP instead.  It's worlds easier to get running: just install the package OpenSSH-server and you have SFTP right out of the box.  chrooted and sftp-only access is also very, very easy to configure, each needing only a line or two in the config file.  

FileZilla supports SFTP and so do Nautilus, Thunar and PCManFM, to name a few.  So unless you specifically need vsftp, you might look at SFTP instead.

---

### Post by Newbunto on 2013-10-29
> **jplamb13 said:**
> 

```

userlist_enable=YES
userlist_deny=NO

```



As you are using a userlist, I would suggest explicitly setting the [FONT=courier new]userlist_file[/FONT] option to the default ([FONT=courier new]/etc/vsftpd.user_list[/FONT]) and of course this file must exist and contain the list of users who are permitted to use FTP.

> As i have said i have changed this loads of times

Are you restarting the service after changing all the config files? The man page doesn't seem to spell out whether the service will detect changes to its config files either periodically or immediately or not at all.

How are you starting the service and what user is it running as? (This is a part that I can't help you with because I am not running VSFTPD under Ubuntu but another Linux distro.)

> changed the owner of the folder

Of what folder exactly?

Some servers are sensitive to their config files allowing *too much* access. Assuming that VSFTPD is being started as root then I would ensure that all VSFTPD config files are owned by root and allow only user root access.

I would suggest not using chroot until you have got it working without chroot.

---

### Post by Mariane on 2013-10-29
> **Lars Noodén said:**
> If you are looking for a way to make secure file transfers for system users, then you might look at SFTP instead.  It's worlds easier to get running: just install the package OpenSSH-server and you have SFTP right out of the box.  chrooted and sftp-only access is also very, very easy to configure, each needing only a line or two in the config file.  

FileZilla supports SFTP and so do Nautilus, Thunar and PCManFM, to name a few.  So unless you specifically need vsftp, you might look at SFTP instead.

Oh, thank you ever so much! 

I typed killall vsftpd. Then I just had to type "apt-get install openssh-server" and it worked, right out of the box! I use Konqueror, I pointed it to [ftp://blablabla](ftp://blablabla), and I could upload my files, drag and drop, easy!

---

### Post by Newbunto on 2013-10-29
> **Lars Noodén said:**
> So unless you specifically need vsftp, you might look at SFTP instead.

"Secure" is being used in two different ways here.

"Secure" in SFTP means "attempt to make it impossible to intercept or alter the network traffic in transit". That is clearly desirable in the general case. FTP by itself gives you none of this. That may not be a big problem if FTP is being used only within a private network. It may not be a problem at all if FTP is transparently layered over a secure protocol e.g. IPSec. It may not be a problem at all if FTP over SSL is used and VSFTPD does apparently support this.

"Secure" in VSFTPD means "attempt to make the implementation as robust as possible against attempts to compromise or otherwise defeat the server". That is clearly desirable in the general case. This is why I use VSFTPD. Various SFTP implementations may or may not achieve the same or better levels of robustness.

We sometimes see in one day more than 1000 attempts to compromise or defeat various servers that we run - and that can originate from any idiot anywhere in the world with an internet connection and a script. Plucking plaintext passwords may actually be more difficult to attempt. (That said, we do where possible also limit plaintext passwords to being transmitted over secure protocols.)

---

