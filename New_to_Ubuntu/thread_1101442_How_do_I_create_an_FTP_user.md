---
title: "How do I create an FTP user"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by patrick666 on 2009-03-20
I created a user "fred" with home /var/www/someplace.com
I can FTP into the server OK so I am nearly there.
Problem is - fred can navigate outside is folder.
I want fred to be limited to his folder.
Patrick

---

### Post by 505 on 2009-03-20
That depends on what FTP server you are using. This feature is called chroot jail. For example, for vsftpd, see [http://www.cyberciti.biz/tips/vsftp-chroot-users-limit-to-only-their-home-directory.html](http://www.cyberciti.biz/tips/vsftp-chroot-users-limit-to-only-their-home-directory.html) For ProFTPD, see [http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html) The same feature is also available for other FTP servers.

---

### Post by patrick666 on 2009-03-20
Thanks 505
The instructions say edit /etc/vsftpd/vsftpd.conf
I do not have a vsftpd folder.
I do have vsftpd.conf in /etc/
So I edited that by uncomenting chroot_local_user=YES
I then restarted vsftpd

The FTP still works but the FTP user can still navigate anywhere.
So I guess I have either done something wrong or not done something I should have.

Just had a thought, is it worth me deleting the user and recreating him? or should the above actions have worked on already existing users.

The user can do both FTP and SSH is that normal ?

Any Ideas
Patrick

---

### Post by Almighty on 2009-03-20
I'm no expert but I think you will have to set chroot to NO if you don't want the user jailed in it's home directory.


Also, if you are using a sftp service it is normal to be able to use ssh since the ftp server uses ssh for security.

---

### Post by patrick666 on 2009-03-21
Quote
if you are using a sftp service it is normal to be able to use ssh since the ftp server uses ssh for security
Unquote
I can only SFTP not FTP - So it sounds to me as if I have not setup my vsftp correctly - does that sound sensible ?
Patrick

---

### Post by 505 on 2009-03-21
yes, looks like it. If you are running an SSH server, all users can SFTP to that server. There, the permissions are the same as when a user would login using a normal SSH session.
FTP is different, because here you can restrict users, or create FTP users that are not users on the system.

If FTP is not working, you first need to find out why. Is vsftp running? Is the correct port open and forwarded, or is a router/firewall blocking it?

---

### Post by vsiege on 2009-03-27
> **505 said:**
> yes, looks like it. If you are running an SSH server, all users can SFTP to that server. There, the permissions are the same as when a user would login using a normal SSH session.
FTP is different, because here you can restrict users, or create FTP users that are not users on the system.

If FTP is not working, you first need to find out why. Is vsftp running? Is the correct port open and forwarded, or is a router/firewall blocking it?I have the above setup vsftpd and SSH server (not sure which one) running.... so I can FTP, SFTP and SSH into my machine.... is ther any way to create a virtual hosting for sftp that administrated through a web browser (and not phpmyadmin... something a little more user friendly)?
if so, could you point me in the right direction?

---

