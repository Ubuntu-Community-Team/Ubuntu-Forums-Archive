---
title: "Cannot Login to ProFTPd as root"
date: 2015-01-21
forum: Networking &amp; Wireless
---

### Post by actionmystique on 2015-01-21
_**Environment**_: Ubuntu 14.10, ProFTPd 1.3.5

Hello everyone, 

Despite root access being allowed (RootLogin directive ON), all connections as root user are being rejected by proftpd (and the password is OK).
[https://drive.google.com/file/d/0B5fXyIn0-GDFZmZaSzducXBmZEE/view?usp=sharing](https://drive.google.com/file/d/0B5fXyIn0-GDFZmZaSzducXBmZEE/view?usp=sharing)
I can login with other users credentials.
Anyone has succeeded with that already or may provide a tip?

---

### Post by Lars Noodén on 2015-01-23
I think people might be uncomfortable helping to log in as root over an unencrypted connection where [the password will be transmitted as plain text because of FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  If you do that over the open internet, your machine will get taken over sooner or later.

If you have SSH running on the machine then it includes SFTP already as it is part of the package openssh-server.  That can be used to transfer securely.  However, using root even for SFTP is kind of strange.  What problem are you trying to solve?  There is probably a better way.

---

### Post by actionmystique on 2015-01-23
Thanks for your reply.
I'm aware of the security concerns. The use case is different from what you've imagined. I'm doing this login **internally**:

I have a Windows VM (KVM) which cannot access the host linux file system; it's easy to do with linux VMs but I've haven't been able to perform a passthrough with a Windows 10 VM. Using FTP is the only way I've found to exchange information between both systems. From time to time, this VM needs to access some root-owned files... hence the root login.

If this feature is not available within proftpd, despite the official documentation, then I guess the only way out is to implement an SSH server.

---

