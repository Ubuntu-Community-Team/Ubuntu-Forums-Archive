---
title: "problem with vsftpd server"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by bhaskarsanta on 2011-04-30
I am new to this ubuntu and installed ubuntu 11.04 Natty narwal in my dell laptop. I am installed vsftpd home server in my laptop. After installation it works fine with mozilla browser on first time. When i start my vsftpd next time (i tried after reboot also) it's not working and it was producing error.  I tried ubuntuforums but i didn't get the correct solution. Give me the exact solution and it's not  related to /etc/vsftpd.conf file because first time works better with this config file.

_error from terminal_
> bhaskar-laptop:~$ service vsftpd start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.60" (uid=1000 pid=2046 comm="start vsftpd ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

---

### Post by clapton_ on 2011-05-03
I have exactly the same problem and didn't find a solution. ( 11.04 too )

First time, it worked, but after rebooting, impossible to have vsftpd working. 
I tried a reinstallation, without any results .

---

### Post by bhaskarsanta on 2011-05-03
> **clapton_ said:**
> I have exactly the same problem and didn't find a solution. ( 11.04 too )

First time, it worked, but after rebooting, impossible to have vsftpd working. 
I tried a reinstallation, without any results .



Hi,
The error comes because of root privilege. I found the solution for this problem by using sudo before this command.  Ex:  bhaskar-laptop$ sudo service vsftpd start . Now my problem is in /etc/vsftpd.cong file. I tried so many combinations in that file still it is not working. Can you post your cong file in this thread and from that i can try your conf file in my ubuntu.

---

### Post by clapton_ on 2011-05-04
I already tried Sudo to start vsftpd :)

Vsftpd is starting but is shutting down immediatly.. 
What i cannot understand is why it was working before the first reboot of my computer..

---

### Post by bhaskarsanta on 2011-05-05
> **clapton_ said:**
> I already tried Sudo to start vsftpd :)

Vsftpd is starting but is shutting down immediatly.. 
What i cannot understand is why it was working before the first reboot of my computer..


I am posting my configuration file here. you can try with my conf file and see the result, why i am asking is that this was worked previously but now it's not working,
Note: Before proceeding with my conf file make sure that you make a separate copy of your cong file and this can be proceed by following steps.
root$ sudo gedit /etc/vsftpd.conf       this is your original conf file.
root$ sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.save        this will create a copy of your conf file.
root$ sudo gedit /etc/vsftpd.conf   this will open your conf file and copy and paste my conf file posted under this message.  Now you can restart the vsftpd server by root$  sudo service vsftpd restart

make sure that you can create a separate directory for ftp under home folder.
root$ sudo mkdir /home/ftp
root$ sudo cp somefile /home/ftp  this will copy some file to ftp folder.

This is my vsftpd.conf file. If you don't mind you can post your conf file to me then i can test your file in my ubuntu system.

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
#guest_enable=YES
#
# Allow anonymous FTP? (Disabled by default)
anonymous_enable=YES
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=077
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
anon_mkdir_write_enable=YES
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
chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
idle_session_timeout=120
#
# You may change the default value for timing out a data connection.
data_connection_timeout=100
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
async_abor_enable=YES
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
ftpd_banner=Welcome to Bhaskar Home FTP service.
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
#chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
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
####secure_chroot_dir=/var/run/vsftpd/empty
#secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/home/ftp/

---

