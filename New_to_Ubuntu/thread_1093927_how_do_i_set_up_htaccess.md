---
title: "how do i set up htaccess"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by rd123 on 2009-03-12
i set up the Apache2 without much of a prob but i am trying to configure htaccess so i can update my website using ftp or ssh do i just create a new folder called HTDOCS  and then point ftp to that directory or are there a set of default folders somewhere

my first attempt at ftp on Ultimate Ubuntu 1.8 (ver8.04 i believe) worked but typing [ftp://mysite.org](ftp://mysite.org) gave me the root of my drive and i really want to limit ftp access to the webfolder only and preferably securley what am i doing wrong if its any help first time round i installed ProFTPD

ive been a long term user of windows server 2003 and am finding the transition a little harder than expected and FAILURE is not a OPTION

---

### Post by Peter09 on 2009-03-12
First ssh is a better option than FTP - its secure and has more facilities such as scp, sshd, sftp etc.

AN ssh server can be built simple with the command

```
sudo apt-get install openssh-server
```

Where you login to when using FTP will be determined by the configuration file for the FTP server that you are using.

If you set up the configuration file to use PAM authentication then you will login through your normal user account on the system. It appears that you are logging in a s root? at the moment.

---

### Post by rd123 on 2009-03-12
i know i may sound a bit dumb but i am assuming i have logged in as a user i went the oem install route updated after install and then did the end user configuration it is the /home/user folder that is visible in FTP (my bad) which i would rather not have - preferring to allow the web folder for a particular user only to have access to one folder which would preferably show in ftp as HTDOCS giving access to default web files /var/www/user1/ and am using the sudo command to access root

---

### Post by Peter09 on 2009-03-12
If you are using PAM authentication, which it sounds like your are you can specify the users default directory by editing /etc/passwd. As always be careful editing a system file. You can then can make a user login on your server to a directory that you specify.

To stop the user changing directory you need to edit the ftp configuration file to disable/enable chroot.

---

