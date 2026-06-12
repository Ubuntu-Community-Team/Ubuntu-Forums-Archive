---
title: "apache2 help"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by williamwade on 2007-04-01
i have been using xubuntu for about 3weeks now and i decided to set up a lamp server

i installed ubuntu server 6.06.1(with xubuntu gui) lamp on 2 machines (1 mac(for testing), 1 pc(for use)) 

i have been told that to upload files to it via ftp i need to install mod_ftp

how do i go about this

also how do i use the root user

---

### Post by dmizer on 2007-04-02
if you're dead set on using mod_ftp, then i don't think i can help you.

if you simply want a working ftp server so you can upload your web files, there are many options available for you other than mod_ftp.  i use proftpd on my lamp box.  the howto i used for configuring proftpd is located in the 3rd link in my sig.  give it a shot, and if you run into problems, you might try performing a search on that thread before posting.

---

### Post by jlk on 2007-04-02
You need to use some form of file transfer to upload files from your workstation to either of your apache servers.  mod_ftp is an Apache add-on module that allows the apache web server to act as an ftp server and allow you to transfer files from your workstation to the server using FTP.

Having said that,  using FTP  is a security risk  as all the user names and passwords are sent in the clear.  I suggest you migh want to look at sftp.  Just google for sftp.  Lots of references.

If you only have a few files to transfer, you could use scp.

```
scp local_file_name(s) user_name@SERVER_IP_ADDRESS:/directory/path/on/server
```
or if you have DNS set up
```
scp local_file_names(s) user_name@SERVER_NAME:/directory/path/on/server
```

You will be prompted for the password of the user_name 

Hope that helps

---

