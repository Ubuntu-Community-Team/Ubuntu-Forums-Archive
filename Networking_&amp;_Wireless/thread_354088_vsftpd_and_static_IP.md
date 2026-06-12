---
title: "vsftpd and static IP"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by euki on 2007-02-05
Hi, I have got a problem with setting up vsftpd for access from outside of my local network. First something about my connection - I am connected with my local static IP 10.51.xx.xx to my ISP and ISP maps this IP to my static one 62.240.180.xxx . I am able to connect to my Linux (EdgyEft) machine from within my local ISPs network ([ftp://login: password@10.51.xx.xx)](ftp://login: password@10.51.xx.xx)), but not from outside ([ftp://login: password@62.240.180.xxx)](ftp://login: password@62.240.180.xxx)). ShieldsUp scan port showed that port21 is open and my vsftpd.conf is 

```

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=NO
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=login
ftpd_banner=Welcome to FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
chroot_local_user=YES
pasv_enable=YES
pasv_address=62.240.180.xxx

```

The last two pasv lines are not there while connecting locally, but I thought that I simply add them to send my static IP as pasv_adress out and its gonna work from outside world....but nothing.

Help, please. :confused: :)

---

### Post by euki on 2007-02-06
SOLVED

Hmm, ok, so the solution is really easy - its simply working. The problem was, that I tried to connect from another local computer (same 10.51. network) with that [ftp://62.240.xx](ftp://62.240.xx)  static IP adress and it simply does not work like that - u probably cannot connect to another local computer with its static (outside) IP, but u have to use the local one.......and static one from outside your network......strange :)

Thanks :)

---

