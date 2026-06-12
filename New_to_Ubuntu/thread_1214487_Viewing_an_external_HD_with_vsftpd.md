---
title: "Viewing an external HD with vsftpd"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by chinaCat86 on 2009-07-16
Hi, I tried for many hours the other night and I cannot quite figure this out. 

quite simply I want to be able to view files on my external HD on my bedroom laptop that has XP installed. 
I originally tried a samba server but that ran SOO slow. so I installed vsftpd and configured it to not allow annon usrs and allow local hosts. I next 
mount --bind /home/usrAcct /media/ 
/home/usrAcct being my home dir when i ftp 127.0.0.1 and /media/ of course being where my HD can be found.

long story short when i connect and try to open the drive I am told I do not have the permissions to open the folder. Any ideas? the External HD is formated as NTFS.

---

### Post by AndThenWhat on 2009-07-16
Okay I ran into the same problems with my local file server.  What you should do is:
1.) Install some sort of SFTP program for the Windows XP machine ([http://jameser.blogspot.com/2006/07/tip-31-simple-portable-sftp-server-for.html](http://jameser.blogspot.com/2006/07/tip-31-simple-portable-sftp-server-for.html))

2.) In Ubuntu, go to (Places -> Connect To Server...)

```
Service Type: SSH
Server: Put your Windows XP computer's local IP address here
Port: You can leave it blank
Folder: /
```

3.) Click 'Connect'.

4. Enter User/Password for SFTP and you're in.


Just in case you didn't know your Windows XP machine's local IP, you can find it by logging into your router's control panel.

Hope that helps.

---

### Post by MontelEdwards on 2009-07-16
> Okay I ran into the same problems with my local file server.  What you should do is:
1.) Install some sort of SFTP program for the Windows XP machine ([http://jameser.blogspot.com/2006/07/...erver-for.html]("http://jameser.blogspot.com/2006/07/tip-31-simple-portable-sftp-server-for.html"))

2.) In Ubuntu, go to (Places -> Connect To Server...)

 	Code:
 	Service Type: SSH
Server: Put your Windows XP computer's local IP address here
Port: You can leave it blank
Folder: / 
3.) Click 'Connect'.

4. Enter User/Password for SFTP and you're in.


Just in case you didn't know your Windows XP machine's local IP, you can find it by logging into your router's control panel.

Hope that helps.n00b plz, 
SFTP is a lot slower that Samba.

---

### Post by AndThenWhat on 2009-07-16
> **MontelEdwards said:**
> n00b plz, 
SFTP is a lot slower that Samba.

It may be slow but it will be much easier to setup by the sound of it.

---

### Post by toupeiro on 2009-07-16
> **AndThenWhat said:**
> It may be slow but it will be much easier to setup by the sound of it.

Here's an idea:

mount your NTFS drive with a GID=<name_of_group>,umask=0007 switch, then create that name_of_group and add your FTP account to it.  

This should give owner and group RWX, and since your FTP account belongs to that group, you should be golden.

---

### Post by chinaCat86 on 2009-07-16
What then is your suggestion montel?

Toupeiro I will try your idea when I return home from work. Although, posting in the beginners forum I'd be lying if I said I knew exactly what you were talking about.

...I  think I can figure it out though.

---

### Post by MontelEdwards on 2009-07-16
> **chinaCat86 said:**
> What then is your suggestion montel?

Toupeiro I will try your idea when I return home from work. Although, posting in the beginners forum I'd be lying if I said I knew exactly what you were talking about.

...I  think I can figure it out though.
Setup a little FileZilla FTP server on Windows, then connect to it through nautilus

---

