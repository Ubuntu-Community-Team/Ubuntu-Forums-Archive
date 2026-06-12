---
title: "vsftpd, connection issues."
date: 2016-01-21
forum: Networking &amp; Wireless
---

### Post by pingaan on 2016-01-21
Hi,

I'm not sure this is the right forum for it, but I'll try anyway.

I recently put up a FTP server using vsftpd. I can't figure out what's wrong but I am able to connect via SFTP but not FTP. Port forward is set up.
Here's my conf:

```
listen=ON
listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
chroot_local_user=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO
user_sub_token=pi
local_root=/home/pi/FTP
```

Regards.

---

### Post by pingaan on 2016-01-23
No one?

---

### Post by steeldriver on 2016-01-23
Can't help with your vsftp setup, but just wanted to note that sftp will be handled by your ssh server so the fact that it works doesn't really tell you much

How exactly is port forwarding set up? Does vsftp work if you leave the configuration default? Can you telnet to port 21?

---

### Post by pingaan on 2016-01-23
You sir are my hero! How could I forget about telnet? I forwarded 21 to the correct IP but appearently it router failed at it's one task! ZzZz.. According to the interface it is open but it's not. 
I'll sort it from here.

Thanks!

---

### Post by pingaan on 2016-01-24
Hmm.. Haven't had the chance to try yet, but it shoudn't be necessary on a LAN? I mean, it's possible to connect on all different kinds of ports without having to open any ports. My guess is that the problem still remains.

---

### Post by steeldriver on 2016-01-24
Sorry I don't understand what you mean by "shouldn't be necessary on a LAN"

Really all I'm suggesting is that you verify that the ftp service is listening on an external (to the machine) interface e.g. stuff like

On the server
```

sudo netstat -nlp | grep :21

```

From a local client
```

telnet *ser.ver.lan.ip* 21

```

---

### Post by pingaan on 2016-01-24
Thanks for taking your time, but I found the issue.. Permission! chown root did the trick! ;-)
For annyone countering the same issue, try: 
```
sudo chown -cR root /etc/vsftpd.conf
```

Cheers.

---

