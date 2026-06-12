---
title: "Creating ftp only user with limited access"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by mryno on 2009-02-09
I need to create a user that has access to only one directory. He will be uploading files to that directory that will be used by my application, but I obviously don't want him to see any other application files. I saw a couple other posts, but they had a bunch of jibberish in them. :-) I need a step by step. I created a user using 'adduser'. The user is 'user1' and is in group 'user1' for our purposes. Thanks in advance!

Ryan

---

### Post by Felix-the-Cat on 2009-03-14
FTP is very insecure by todays standards and is widely unused because of this. SFTP has all but replaced it. I have done exactly what your taking about with FTP and I can think of more fun ways to spend my time. There is a package in the repositories called scponly that will automatically set up SFTP that will fit the description of your desired end result. The user will have to login using WinSCP, however. If you go [Here]("http://www.ubuntugeek.com/scponly-limited-shell-for-secure-file-transfers.html") you will find a step by step guide for this.

---

