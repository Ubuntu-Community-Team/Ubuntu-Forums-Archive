---
title: "vsftpd - help? 500 OOPS: child died"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by BikeHelmet on 2010-02-26
Hi. I have a NAS running Ubuntu 9.04

I'm trying to set up vsftpd so that someone can drop files in a dropbox folder.

Initially I had anonymous FTP working, but then I realized anyone could download the files using [ftp://My_IP/](ftp://My_IP/)

The files aren't really important, but I'd prefer not to blow my upstream bandwidth.

So now I've set up a new user account, and am attempting to get vsftpd to allow it - but it isn't working. The error message is [COLOR="Red"]500 OOPS: child died[/COLOR]

So maybe someone can look through here and point out what's set wrong. I've been searching google for hours, but none of the tutorials or articles have the answer.

```
listen=YES
listen_ipv6=NO

anonymous_enable=NO
local_enable=YES

#anon_root=/media/Storage_A3/FTP
local_root=/media/Storage_A3/FTP


write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#anon_umask=022
#local_umask=022


userlist_enable=YES
userlist_deny=NO
userlist_file=/etc/vsftpd.user_list 


chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
passwd_chroot_enable=YES


#vsftpd.chroot_list and vsftpd.user_list contain the username and a newline


#ftp_username=ftp
#anon_upload_enable=YES
#anon_mkdir_write_enable=YES
#anon_other_write_enable=YES
#no_anon_password=YES


#tcp_wrappers=YES


#guest_enable=YES
#guest_username=bikehelmet


#delete_failed_uploads=YES
#dirlist_enable=NO

#ssl_enable=YES
#allow_anon_ssl=YES
#force_anon_data_ssl=YES
#force_anon_logins_ssl=YES


chown_uploads=YES
chown_username=bikehelmet

ftpd_banner=Connected. Create a new folder and drop files wherever you want.


# Display .message file when entering dir.
#dirmessage_enable=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#xferlog_file=/var/log/vsftpd.log
#xferlog_std_format=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES

secure_chroot_dir=/var/run/vsftpd

pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
```


I'd grep it, but I have no clue what the grep command is.

Edit: User is listed properly in user_list and chroot_list files. SELinux isn't even installed.

---

### Post by Kakers on 2010-02-26
Do you have the user listed in /etc/vsftpd.user_list ?

---

### Post by BikeHelmet on 2010-02-26
> **Kakers said:**
> Do you have the user listed in /etc/vsftpd.user_list ?

> #vsftpd.chroot_list and vsftpd.user_list contain the username and a newline

Yes.

Initially I thought maybe there was an issue with the username being an email address, so I added a new user that was just a regular name, and removed the email address. Still doesn't work.

---

### Post by Kakers on 2010-02-26
This may help you:
[http://rackerhacker.com/2007/06/14/500-oops-error-from-vsftpd/](http://rackerhacker.com/2007/06/14/500-oops-error-from-vsftpd/)

---

### Post by BikeHelmet on 2010-02-26
That is one of the links I googled. None of the answers work.

I suspect the issue is related to the user_list file. I just don't understand why including it messes things up. I really don't want my main account accessible from the internet.

Edit: Might have an answer [here]("http://www.linuxquestions.org/questions/linux-software-2/vsftpd-how-to-lock-users-into-a-specified-directory-tree-619896/"). Going to mess with more settings.

---

### Post by BikeHelmet on 2010-02-26
These options had to be turned off:
```
#passwd_chroot_enable=YES


#userlist_enable=YES
#userlist_deny=NO
#userlist_file=/etc/vsftpd.user_list 


#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd.chroot_list

```
If any are enabled, it doesn't seem to work properly.

Unfortunately, this means my main account can be used to login to FTP, because vsftpd isn't behaving properly. Oh well - it's chroot'd to an FTP folder, so hopefully that isn't a security risk.

---

