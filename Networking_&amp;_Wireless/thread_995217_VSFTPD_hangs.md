---
title: "VSFTPD hangs"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by fuzzybear3965 on 2008-11-27
I've tried multiple things with this.  Basically vsftpd connects fine and login is fine but as soon as I try to list a directory it hangs on
```
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.

```
I'm at a loss.  I've changed from passive to active (currently, listen=YES) reinstalled from scratch multiple times.  I have opened my router ports on 20 and 21 and used firestarter to open the ports on 20-21 to no avail.  Please help.

EDIT:  I just discovered that my local connection works fine.  My internal IP address (192.168.1.8) by my router is perfect for ftp transactions and listed contents immediately.  However, any external connections fail.  I really need to access the ftp server away from home.  Please help.

---

### Post by rasensio on 2008-12-10
I'm getting the same problem and my DOS client cant connect from outside the network, my firewall has all ports open right now, I cant make it work. my config

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=077
dirmessage_enable=YES
xferlog_enable=YES
max_per_ip=10
connect_from_port_20=YES

pasv_enable=YES
pasv_address=MY_EXT_IP
pasv_min_port=1025
pasv_max_port=1045

ftpd_banner=Welcome to xxx FTP service.
chroot_local_user=YES
ls_recurse_enable=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
chmod_enable=YES
dirlist_enable=YES

#ssl stuff
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=NO
force_local_logins_ssl=NO

ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO

rsa_cert_file=/etc/vsftpd/vsftpd.pem

---

### Post by fuzzybear3965 on 2008-12-10
Hey sorry for the delay in response.  I got mine to work and it was simply a matter of typing in the external IP address manually.  My suggestion would be to delete the entries of local min and max port and restart vsftpd

```
sudo /etc/init.d/vsftpd restart
```

Do that and tell me if anything changes.  A way to test to see if it works externally in a LAN is to try to access your ftp server.  ex:  my external IP is 66.233.49.112 and so i type ftp 66.233.49.112 in my LAN and it connects externally from an internal connection.

---

