---
title: "Virtual Hosts and FTP"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by Jloser on 2010-08-25
I have an ubuntu server setup with virtual hosts running multiple domains on the same IP address.

domain1.com
domain2.com

I have just configured FTP via VSFTPD and I am looking to only allow ftp to one site, and most preferable would be a subdomain of one site.  

Something like ftp.domain3.com

How do I accomplish that?

---

### Post by Yizi on 2013-02-06
I would like to know that too, specify a user for a virtual site e.g. user1 is associated with the folder /var/www/domain.com/public_html

Anyone?

---

### Post by greenpeace on 2013-02-06
Hi, 

This thread is over a year old, but here's how I would do it.


Once you have VSFTP installed:

1. edit "/etc/vsftp.conf" as the root user, changing/setting these options:

```
userlist_file=/etc/vsftpd.userlist
userlist_enable=YES
userlist_deny=NO
```

2. create "/etc/vsftpd.userlist" and add the desired usernames to the file, each one on a separate line.

```
sudo nano /etc/vsftpd.userlist
```

3. then use **adduser** to create unix users on the server:

```
sudo adduser --home /path/to/users/ftp/dir --shell /usr/sbin/nologin <username>
```

replacing <username> with the name of the FTP user (which must match what you included in the /etc/vsftpd.userlist file).  There is a series of questions, which are not too important, although including the user's real name can be useful in the future.

4. finally, restart vsftpd:

```
sudo service vsftp restart
```

And then test it!

---

