---
title: "Ftp for camera"
date: 2018-07-10
forum: Networking &amp; Wireless
---

### Post by BobvanderPoel on 2018-07-10
I'm having a totally stupid moment! I have a cheap video cam which will save images to my computer using FTP. Until today it was working just fine ... so I reset the camera. Now, I can get the ftp save stuff to work.

In the camera there is a settings screen which I have filled in as follows:

Server Address: 	192.168.1.66
Server Port: 21
User name: ftpuser
Password: 	secret
Passive mode: 	On 
Path: 	/home/ftpuser
Auto create dir: 	On 

I press the <test> button, and it fails. Can't establish a ftp connection. I have tried using my host name (Mellowood) and localhost, but no difference. 

I've checked the username/password and they certainly seem to be fine. From a terminal I can login as ftpuser.

I can ping 192.168.1.66 as well as mellowood (from the /etc/hosts file).

I have tried different ports including 20 (which my vsftpd.conf file is set to permit) and 10099. 

Here is my /etc/vsftpd.conf file:

 listen=NO
listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO
pasv_enable=Yes
pasv_min_port=10000
pasv_max_port=10100
allow_writeable_chroot=YES

Help ... I'm lost :)

---

### Post by Skaperen on 2018-07-10
change listen=NO to listen=YES and restart it.

---

### Post by BobvanderPoel on 2018-07-10
> **Skaperen said:**
> change listen=NO to listen=YES and restart it.

I just got success! 

First off, changing to listen=NO did not work. Matter of fact, it didn't work at all. I have no idea why ... I'd appreciate a primer.

The problem I was having is that I was entering all the data in the camera data, but I was not doing an <apply> before <test>. Guess it's been too long of a day!

Thanks.

---

### Post by Skaperen on 2018-07-11
listen=YES means that it will listen for incoming connections in the original IPv4 address space the internet went public with.  the new address space is IPv6 which the FTP server could also listen to (no real reason to have it not do so unless you are very paranoid about it). so, basically, you had the server listening on IPv6 only and the camera likely can't do it since it is an old one.  so you want to be using IPv4 and have the server listening on it.  the reason it is "listen=" instead of "listen_ipv4" is because the software was created without support for IPv6 initially, and when they thought of what name to use, there was only on address space and no real reason to specify it.  there is now but names for doing IPv4 are just the old generic names, so long running config files don't stop working.

addresses in IPv4 are like "192.168.1.66".

addresses in IPv6 are like "fd12:d210:004a:c198:0000:0000:0000:0001:0066" (shortened to "fd12:d210:4a:c198::1:66").

is the camera saving videos now?  then the next thing you probably want to do is write a script to detect when a video is saved and upload it to a space online where you can share it with a select group of friends.

---

### Post by BobvanderPoel on 2018-07-11
Yes, it's working just fine.

I now need to make some decisions as to how to store all this crap, how many days to keep, and whether to use the camera's motion detection or to use a program like motion. I looked at zoneminder but it seems a bit of overkill for one little camera! All things for tomorrow :)

---

