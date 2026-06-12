---
title: "FileZilla connection issue"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by cressrt on 2010-01-31
I have migrated (hopefully) to Ubantu and am trying to upload changed files to one of my websites. I used to use Dreamweaver on Windows and have used Kompozer to modify but could not publish with this.  I have tried FileZilla and this also is failing. I connect to a Linux server and this does not appear to be an option under Filezilla. Am I doing something wrong or do I need another programme?

---

### Post by louieb on 2010-01-31
Haven't used filezilla on Linux - don't know any reason it would not work.

Anyway program I have use to connect and update my websites include gnome-commander - gftp  and nautilus.   BTW: I'm hosted on a Linux server too. But that should not make a difference - ftp is ftp.

---

### Post by cariboo on 2010-01-31
Is your user a member of the group that owns the directory that you are trying to upload files to? If you have ssh installed on the the server you can access the server using sftp, which is much more secure than ftp.

To use sftp, open nautilus (Places->Home Folder) and in the location bar type:

```
sftp://user@server
```

enter your password when asked, and navigate to the directory you are trying to upload files to. once in the directory right clcik on a file and check which group owns it. Once you have this info you can add yourself to the group by opening a terminal and typing:

```
sudo gpasswd -a <user> <group>
```

---

### Post by cressrt on 2010-02-01
Thanks for replies, I will try the options mentioned; what I was saying about FileZilla is that it does not give Linux as a "Server Option" to be uploaded to.

---

### Post by cressrt on 2010-02-01
Gnome Commander works well, very simple; will use this for now.

---

