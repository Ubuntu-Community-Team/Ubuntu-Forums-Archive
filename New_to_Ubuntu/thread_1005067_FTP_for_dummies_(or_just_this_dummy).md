---
title: "FTP for dummies (or just this dummy)"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by doctorbighands on 2008-12-07
Hello,

I'm having enormous problems doing something that I think should be VERY simple. I've Googled my fingers off, but to no avail. Can someone help me? Here's what's happening:

1) I have downloaded and installed vsftpd. When I call up "ftp://<my IP address>" in a browser, nothing happens.

2) Where do I move files so that, when I finally get an FTP server running, they show up in a browser and/or gFTP? Do they go into /var/www like my website? Do they go into /home/something-or-other? Do they go elsewhere?

3) The only reason I want an FTP server is to share files between myself and my cousin. How do I make it so that only he and I can log in to the FTP server and up/download files?

Like I said, this should be really easy, I'm sure, but I'm frustrated to no end with it. Any help is very much appreciated.

(I'll post my vsftpd.conf file later if it'll help. I can't right now, because my server is running updates.)

---

### Post by doctorbighands on 2008-12-07
The contents of my vsftpd.conf file:

```

# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=YES
#
# Uncomment this to allow local users to log in.
local_enable=NO
#
# Uncomment this to enable any form of FTP write command.
write_enable=NO
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=022
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
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=NO
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format
xferlog_std_format=YES
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
# Beware that turning on ascii_download_enable enables malicious remote parties
# to consume your I/O resources, by issuing the command "SIZE /big/file" in
# ASCII mode.
# These ASCII options are split into upload and download because you may wish
# to enable ASCII uploads (to prevent uploaded scripts etc. from breaking),
# without the DoS risk of SIZE and ASCII downloads. ASCII mangling should be
# on the client anyway..
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
ftpd_banner=Welcome to the GNU/Linux Users Group, National Institute of Technol$
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES

pam_service_name=vsftpd
userlist_enable=YES
#enable for standalone mode
listen=YES
tcp_wrappers=YES
#My additions
no_anon_password=YES
listen=YES
anon_root=/home/ftproot

```

---

### Post by doctorbighands on 2008-12-07
Okay, I've made some progress. Very little, but still...

I've discovered that vsftpd looks to /home/ftp for files. So, that question is answered.

I have changed my vsftpd.conf to the following. Will this be good? Should something be changed?
```

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
chown_username=nick
ftpd_banner=Welcome to blah FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/home/ftp

```

I still haven't figured out how to password protect the /home/ftp folder. I'd love to know.

---

### Post by jimmy the saint on 2008-12-07
Try reading the bits of this tutorial that deal with ftp.  It uses proftp, which I have used and found to be relatively painless.  I have never heard of vstpd, so I cannot comment on it, but if you are not attached to it specifically, this guide and its predecessors have been good resources for me in the past.
[http://www.howtoforge.com/perfect-server-ubuntu-8.10](http://www.howtoforge.com/perfect-server-ubuntu-8.10)

---

### Post by doctorbighands on 2008-12-07
Right now, I am attached to vsftpd because I finally got an FTP page online. I don't want to mess with something else!

I tried using "htpasswd" and it doesn't prompt me for a password when I load the FTP site.

I am absolutely stumped on this.

---

