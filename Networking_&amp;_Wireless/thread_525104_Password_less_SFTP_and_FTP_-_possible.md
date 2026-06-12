---
title: "Password less SFTP and FTP - possible?"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by yeoheric on 2007-08-13
Hi,

There are two apps in my company that needs to connect to our business partners' servers. One is using plain old ftp and the other sftp. 

My question is, are there client apps that allows for scripted sftp and ftp access? I mean like putting the relevant username and passwords into a config file and running it as a cron job to grab and put data?

The sftp server is a Windows based Tectia server and the ftp server is on a standard IIS.

Pls assist.

Thanks

Eric

---

### Post by operator207 on 2007-08-14
SFTP, yes. see [http://ubuntuforums.org/showthread.php?t=238672](http://ubuntuforums.org/showthread.php?t=238672) for information on setting up passwordless SSH and rsync, though once you do this, you can ssh into the remote box without a password from THAT account. scp is just an extension of ssh.

I see your using scp on windows, I am not sure whre you would put the key on that server though, unless you can ssh into that server also, then there should be a .ssh dir somewhere for that user your scping in with.

FTP, not really sure, though if you value your passwords on an open network, do not use ftp. It sends the passwords in clear text. Unless your using ftps.

---

