---
title: "Quick FTP Setup Questions"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by Nexusx6 on 2007-12-24
Hey everyone. I have two relativity simple questions about an FTP server I'm setting up using VsFTPd. 

What I'm trying to do is give each user Read Write eXecute permissions for their home directory, while having a folder in each of their home directories that points to a "shared" directory with Read permisions, but no W or X.  

Basically, what I want is to let people upload and download personal files from their directory, while letting them download things I've placed in shared directory but no to edit/upload to that directory. I know how to do this with owner and group permisions, so my question is as follows:

1) Where should I put this shared directory in the linux file system? Say I wanted to call this folder "Public", is /usr/shared/public an appropriate place? Or should I place it under the user 'ftp' that vsftpd made on install (/home/ftp/public)

2) How should I link to this directory? is
```
ln-s /usr/shared/public /home/[usrname]/public/
```
the correct code?

Don't know if it means anything, but I plan on putting this 'link' in the /etc/skel folder so that when I create the users I don't have to mkdir and link for every person I add.

Thanks for help :KS

---

