---
title: "Please help me setup LAMP"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by Redkore on 2009-11-16
Hello World!

I've installed Ubuntu server in virtual machine trying to learn and practice LAMP administration for upcoming little project of mine. I'm complete noob, have linux for 3 days now (my last attempt was over 10 years ago when I spent half day trying to mount cd and swore my love to windows). I have all components installed which seems to be working, I just can't get my head around user privileges and file ownership. I have installed vsftpd but can't setup permissions the way I want. It seems files in /var/www needs to be owned by www-data user so I can read and write to that dir via apache and PHP, but I also want to be able to upload files via FTP and edit them as well (over FTP, remotely). Now, I can't access FTP with www-data user since I don't know the password, while I create user webmaster apache can't process files because of wrong ownership, if I set anonymous access and allow creation of files by anon and make new uploads owned by nobody, in vsftpd.conf, I can't upload anything at all. While connection is active I have 3 processes of vsftpd owned by root, nobody and ftp. Upon disconnecting only root stays. Whats more, while I had webmaster account with home dir set in /var/www and root_dir from vsftpd.conf pointing to the same folder, I was able to browse filesystem freely which is not desired.

So how can I make this work? I want files in /var/www to be secure, only accessible by apache from within the system and ftp deamon. I'm talking of unsecured FTP for now, will try to learn FTPS or SFTP later. My idea on production server was to login via SSH, enable FTP, beam files, disable FTP, logout. This is  how it's being done in real world?

Thanks for help!

---

### Post by Redkore on 2009-11-17
Bump

---

### Post by gypsumwolf on 2009-12-02
Did you check the [Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/index.html")?

Here is a chmod calculator if you need it: [http://mistupid.com/internet/chmod.htm]("http://mistupid.com/internet/chmod.htm")

Files and Permissions: [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html")

---

