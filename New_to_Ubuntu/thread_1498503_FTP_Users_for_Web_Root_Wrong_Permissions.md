---
title: "FTP Users for Web Root Wrong Permissions?"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by roscius on 2010-05-31
I've set up Apache and vsftpd - all went great.

I wanted to add an FTP user that would be able to send/add files to the default web root, so I added a new user - webftp

I did sudo usermod -d /var/www webftp

I then did sudo chown -R webftp /var/www - maybe my first mistake?
and then sudo chmod -R 755 /var/www

Worked fine, I can log in remotely via an ftp client using webftp username/password, I am locked in to the /var/www directory remotely (which is good).

But...

When I upload files via the ftp client they end up on the server with 0600 permissions and I have to manually change them in the ftp client to 0777 permissions so that they are visible on the website.  I do that and everything seems ok.

Two questions:

1.  What do I do to get the files when they upload in the ftp client to automatically 0777 so that I don't have to manual set the permissions (like they do on all the other websites I upload to that smarter people than me have configured...)

2.  Did I muck up the permissions on the /var/www directory?  Should I set them back to anything.

The www directory currently is:

drwxrwxrwx 2 webftp root 4096 Jun 1 01:16 www

I'm using a standard ubuntu 10.04 LTS server installation (it's running in a cloud).

Thanks for guidance or direction!

---

