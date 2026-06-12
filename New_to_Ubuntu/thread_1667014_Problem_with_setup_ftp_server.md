---
title: "Problem with setup ftp server"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by alfamuzjak on 2011-01-14
I have problem with seting up ftp server, im using ubuntu server 10.10 with no gui.
I will show u all my steps,i dont know what im doing wrong:
After installing vsftpd i change only this options from its default in /etc/vsftpd.conf and this options are only uncommented:

```
Listen=YES
anonymous_enable=YES
local_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd

rsa_cert_file=/etc/ssl/private/vsftpd.pem 
```

...When i restart vsftpd service and try to connect with anonymous it said:login fail:

530 login incorrect.
login failed.
ftp>

By the way im using virtual mashine, and when i try to connect with my windows browser: [ftp://ip.address](ftp://ip.address).

i pass into ftp index location.

---

