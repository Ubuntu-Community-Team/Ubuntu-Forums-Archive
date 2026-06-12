---
title: "File transfer"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by chono on 2008-12-12
I have 2 ubuntu pcs, im using samba for file transfer. but i only get 400k/sec is there another program i can easily install to transfer large files?

---

### Post by handydan918 on 2008-12-12
ssh works pretty well.
 
```
sudo apt-get install openssh-server
```
Then
```
sudo update-rc.d -f ssh remove &&
update-rc.d ssh defaults
```
Then
```
/etc/init.d/ssh start
```

To transfer a file, do scp /source/directory/file target.ip.address:/target/directory

To copy a directory, do as above, but use ```
scp -r
``` (recursive)

---

### Post by chono on 2008-12-12
I still have the same speeds maybe my router:/ thanks:D

---

### Post by lkraemer on 2008-12-13
I just installed Filezilla, and then you need an FTP Server running
on one machine so I used vsftpd (Very Secure FTP Daemon) and it worked good.
In fact the 10 Gig Virtual Disk Image (VDI) transfered fast, and I
was impressed.  It took a bit for me to figure out Filezilla since
I had not used it before but I can use it now.  All you need is the
FTP Server's IP Address and the Login & Password.

You might look at this choice, or maybe others have better suggestions.

Just make sure an FTP Server is running on one machine, and use Filezilla
on the other.

Here are the commands I used to get vsftpd configured & to start/stop/restart vsftpd:
  sudo gedit /etc/vsftpd.conf

  sudo /etc/init.d/vsftpd stop
  sudo /etc/init.d/vsftpd start
  sudo /etc/init.d/vsftpd restart

Good Luck.

lk

---

