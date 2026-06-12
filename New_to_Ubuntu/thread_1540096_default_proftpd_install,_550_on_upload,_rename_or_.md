---
title: "default proftpd install, 550 on upload, rename or mkdir"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by luisindahouse on 2010-07-27
Hey there,
 
this is probably easy, but cant figure it out.
 
I just did a fresh install of proftpd using apt-get, now when i log in to the server with ANY user, I get a 550 error whenever I try to upload, rename a file or create a directory.
 
where should i look to change the permissions? is that a normal behavior for a brand new install?
 
thanks!

---

### Post by lkraemer on 2010-07-27
Google shows:


Question/Problem: 550 No such file or directory.

Answer/Solution:  This error message is coming from the FTP Server to which you are connected. 550 errors are always a permissions errors. The text that follows 550 varies from server to server. The 550 error means the user does not have access rights to the directory or file.

You probably need more permission on the FTP Server. Contact the people who run the FTP Server............

For most FTP servers, you need an account, and typically users are JAILED
to one directory where they have permission to Read/Write.  Sounds as if
you need to browse the manual for more specifics, along with:
```

man chmod
man chown

```

lk

---

### Post by luisindahouse on 2010-07-27
file permissions and groups are correct, ie.: if i log in with user LUIS, and try to modify a file with owner LUIS, i still get a 550 error.
 
same if i try to upload a file to a folder owned by LUIS
 
anyone?

---

### Post by luisindahouse on 2010-07-27
ok so I tried deinstalling, reinstalling. same problem. then I installed vsftpd and i get the SAME problem. so its not an issue with the ftpd.
 
next, i chmodded a file to 777 and i still cant rename it or overwrite it!!!
 
now, when I issue a LIST function from my FTP client, i get this:
 
drwxr-xr-x   11 1000     1000         4096 Jul 27 00:12 code
-rw-r--r--    1 1000     1000          179 May 29 08:54 examples.desktop
drwxr-xr-x    4 1000     1000         4096 Jun 06 15:27 qBT_dir
 
why is there 1000 instead of my username and group? when I do a `ls -l` from SSH i see my username instead of the 1000... could that be the problem? how to fix?
 
thanks

---

### Post by lkraemer on 2010-07-27
I assume you are using ssh to tunnel into the FTP Server, to look at the
permissions and owner.  You will find that they are incorrect or it would
be working.

With ssh, go to where you can see your FTP Download directory.  Check the
permissions and owner.  It should be something like youruserlogin:abc
where abc is either root, admin, or wheel depending on what you are using.

mine happens to be:
```

drwxr-xr-x   2 ldk78:wheel      512 Jul 27 19:33 ftptest

```

To find out what it needs to be, Open Filezilla, Create a new Directory (right hand menu/window)
that you will transfer a test file to and make the upload.  Then go back to your ssh window,
and check the permissions and owner of your test file.  (If you are just trying to xfer you don't
have the proper permissions to do that.)  That is why most users are jailed into their own directory
for FTP uploads/downloads.  Once you get the proper owner and permissions worked out change your
download directory to that.  Done!

Typically the FTP Download directory (using vsftp) is jailed to /home/ftp/loggedinuseraccount
and you will download your files there.  A second person would download to /home/ftp/nextloggedinuseraccount

Filezilla will create directories and transfer a test file so you can verify the permissions/owner.
   

lk

---

### Post by luisindahouse on 2010-07-28
> **lkraemer said:**
> I assume you are using ssh to tunnel into the FTP Server, to look at the
permissions and owner. You will find that they are incorrect or it would
be working.
 
With ssh, go to where you can see your FTP Download directory. Check the
permissions and owner. It should be something like youruserlogin:abc
where abc is either root, admin, or wheel depending on what you are using.
 
mine happens to be:
```

drwxr-xr-x   2 ldk78:wheel      512 Jul 27 19:33 ftptest

```
 
To find out what it needs to be, Open Filezilla, Create a new Directory (right hand menu/window)
that you will transfer a test file to and make the upload. Then go back to your ssh window,
and check the permissions and owner of your test file. (If you are just trying to xfer you don't
have the proper permissions to do that.) That is why most users are jailed into their own directory
for FTP uploads/downloads. Once you get the proper owner and permissions worked out change your
download directory to that. Done!
 
Typically the FTP Download directory (using vsftp) is jailed to /home/ftp/loggedinuseraccount
and you will download your files there. A second person would download to /home/ftp/nextloggedinuseraccount
 
Filezilla will create directories and transfer a test file so you can verify the permissions/owner.
 
 
lk
 
i cant use FileZilla and create a directory... I get a 550 error when i try to create a new directory!
 
i doubt it has anything to do with file ownerships and permissions... users are sent to their home directory when logging in to the FTP server... all the files they see are owned by them.
 
it must be some security settings or some packages that i installed recently that created that strange behavior!
 
any ideas??? im lost.

---

### Post by JKyleOKC on 2010-07-28
Proftpd's actions are controlled by the /etc/proftpd/proftpd.conf file. Specifically, there are portions of this file that establish permissions for various actions. These totally override the permissions that you set with chown and chmod, so far as the server is concerned.

Post your proftpd.conf file here and we can help you set it up so that you have the desired actions -- and also even eliminate the jailing action if you so desire. However be warned that opening it up is an invitation to be pwned: I get a few hundred invasion attempts every week on my private server (which is locked down rather tightly via the conf file, so they don't succeed)!

---

