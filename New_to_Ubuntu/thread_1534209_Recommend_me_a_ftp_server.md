---
title: "Recommend me a ftp server"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by Vichfret on 2010-07-19
I'm looking to setup a ftp server, could you tell me about some servers you know and their main features/characteristics. If it has a good cli/gui, security features, how popular it is, etc.

---

### Post by Kay The Bantu on 2010-07-19
FileZilla is a popular choice here are some links
Documentation: [http://wiki.filezilla-project.org/Documentation]("http://wiki.filezilla-project.org/Documentation")
Download:[http://filezilla-project.org/download.php]("http://filezilla-project.org/download.php")

hope this helps

---

### Post by jerenept on 2010-07-19
Isn't FileZilla for _Accessing_ an FTP server?

I think that ubuntu has FTP built in or something.

Do you want to share the files on your Ubuntu computer via FTP?

---

### Post by WRDN on 2010-07-19
Theres an FTP Server guide here: [https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html)

---

### Post by aeiah on 2010-07-19
i use vsftpd and have never had a problem with it. depending on what you're using it for, it may be far easier (or more secure) to use ssh though. i have ftp available only locally to transfer large files to my netbook. it goes about 30% quicker than ssh but if i was opening it to the outside world, id go with ssh.

---

### Post by lkraemer on 2010-07-19
VSFTP - [http://vsftpd.beasts.org/](http://vsftpd.beasts.org/) - Server
vsftp is in Synaptics package manager.

Filezilla - for Clients to access via FTPES so it's secure.


Ref:
[http://ubuntuforums.org/showthread.php?t=518293&highlight=HOWTO%3A+vsftp](http://ubuntuforums.org/showthread.php?t=518293&highlight=HOWTO%3A+vsftp)
[http://www.brennan.id.au/14-FTP_Server.html](http://www.brennan.id.au/14-FTP_Server.html)
[http://ubuntuforums.org/showthread.php?t=30709&highlight=HOWTO%3A+Openssh](http://ubuntuforums.org/showthread.php?t=30709&highlight=HOWTO%3A+Openssh)
[http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)
[https://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/ref-guide/s1-ftp-servers.html](https://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/ref-guide/s1-ftp-servers.html)


lk

---

### Post by Iowan on 2010-07-19
[Here]("http://ubuntuforums.org/showthread.php?t=79588") is another option...

---

### Post by blukes on 2010-07-20
Try PROFTPD : 

  	 	 	 	 	```
sudo apt-get install proftpd gadmin-proftpd 
```

After you install it'll be in Applications/System Tools.

---

### Post by Unlimited Power on 2010-07-20
> **jerenept said:**
> Isn't FileZilla for _Accessing_ an FTP server?

Not really - they have a server, too ( ONLY for Windows ).

---

### Post by 4rtur on 2010-07-20
VSFTP +1 secure, chrooted and very easy to set up.

---

### Post by Vichfret on 2010-07-23
I am using proftpd, vsftpd looks better but I couldn't get the authentication to work I only could login as anonymous, I tried very hard but it didn't work, maybe I'll keep trying later.

---

