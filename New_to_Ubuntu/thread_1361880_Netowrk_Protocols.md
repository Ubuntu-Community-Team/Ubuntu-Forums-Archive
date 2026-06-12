---
title: "Netowrk Protocols"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by Swenghk on 2009-12-22
Hello everyone, I want to learn how to network using a terminal or some sort of shell (if those are even practical anymore hahaha). I was thinking of learning SSH, Telnet, and after that, my mind is drawing a blank... Am I even heading in the right direction

---

### Post by audiomick on 2009-12-22
Hi, a bit out of my range of experience, but since you haven't had an answer yet, here's my 2 cents worth.

Terminal is still current. Ubuntu server doesn't even have a GUI on it, which means the "professionals" do everything in the command line.

I know that SSH is relevant, and I see a lot of references to telnet here, so I assume that that is also relevant.

Have fun learning!

---

### Post by tripolitan on 2009-12-22
All protocols you mentioned are still relevant, some more than others. SSH should always be used instead of Telnet, but ultimately, what do you really want to achieve at the end? Answering this question will help others help you.

I use ssh all the time to access other Linux boxes and perform maintenance/start-stop services/upload files etc. Is that what you want to do? what about other protocols and service like FTP/HTTP/SMTP, etc?

---

### Post by Swenghk on 2009-12-22
I want to learn how to access remote servers and download/upload files to it. But I want to use SSH or even Telnet (yeah right!) hahaha

---

### Post by llamakc on 2009-12-22
You should play with scp and sftp to move files securely.

---

### Post by Miljet on 2009-12-22
Here is a link to get you started.
[https://help.ubuntu.com/community/SSH?action=show&redirect=SSHHowto](https://help.ubuntu.com/community/SSH?action=show&redirect=SSHHowto)

---

### Post by Swenghk on 2009-12-22
Thanks mate! And everyone else who helped! Cheers! :]

---

### Post by tripolitan on 2009-12-23
I think that ssh might be all you need. gFTP moves files from/to servers using ftp and ssh. webmin is a web interface for administering and configuring servers (installed on server). Good luck.

---

