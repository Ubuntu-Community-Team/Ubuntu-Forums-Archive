---
title: "Is it possible to use ncFTP to shut down the system after all processes complete?"
date: 2015-09-04
forum: Networking &amp; Wireless
---

### Post by zair2 on 2015-09-04
As title suggests - is this possible? I have been searching and can't seem to find anything suggesting so. If this isn't possible, is there another command line FTP client that can do this?

---

### Post by SeijiSensei on 2015-09-05
Not unless you're communicating with a very insecure server.  FTP is designed for ordinary users who have no root privileges and thus cannot shut down the machine.  I'm not even sure you can get a shell prompt from an FTP session; it's been years since I've used the protocol at all.

Install openssh-server and use an SSH client.  Then you can use SCP or SFTP to conduct secure file transfer sessions with encryption.

---

