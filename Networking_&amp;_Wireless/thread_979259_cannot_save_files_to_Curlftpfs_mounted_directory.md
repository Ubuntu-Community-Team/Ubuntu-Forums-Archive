---
title: "cannot save files to Curlftpfs mounted directory"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by 9999999999 on 2008-11-11
I've done the following:

```

~$ sudo apt-get install curlftpfs
~$ sudo mkdir /media/ftp-server
~$ sudo chown me:me /media/ftp-server
~$ sudo curlftpfs -o allow_other ftp://user:pass@ftp.example.com /media/ftp-server
~$ mkdir /media/ftp-server/test
~$ nano /media/ftp-server/test/newFile

```

When I type some stuff into newFile and attempt to save it nano gives me the following error:

```
[ Error writing newFile: No such file or directory ]
```

I get a similar error when using any other means to save or create a new file to the mounted ftp file system. 

If I use nautilus to create a new empty document I get a similar error. I'm then asked if i want to 'cancel' or 'skip', if I skip the error the new empty document will be created but I get an error if I try to modify and save that same file.

I know there is nothing wrong with the ftp site because I use it all the time via the firefox ftp add-on.

I don't really have any ideas what could be wrong. I'm still pretty noob.

---

### Post by yirgen on 2009-08-11
*Bump*

Sorry - I know this is a dead thread... But I have the exact same problem! 

Any suggestions?

---

### Post by asedas on 2009-09-10
any ideas? I have the same error when i try to write anything to mounted folder :/

---

### Post by Sathallrin on 2009-12-30
Same thing here, can't get it to save any files? Anyone have a solution to this?

---

