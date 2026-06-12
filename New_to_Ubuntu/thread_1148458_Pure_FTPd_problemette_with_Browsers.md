---
title: "Pure FTPd problemette with Browsers"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by birdm110167 on 2009-05-04
Hi there

I have installed PureFTPd and all seemed to go well.

It certainly allows me to log on and upload/download files.

However, I need to make it work with browsers like firefox and IE as the end users will be all Windows based and if I mentioned FTP clients thay would think I was from another world.

The issue I have is this:

If I try to get to the FTP server from Firefox or IE typing in [ftp://192.168.1.8](ftp://192.168.1.8) the screen goes blank.  When I tried this with PROFTPD I was prompted with a username and password window.

I can access the FTP server in Firefox/IE if I logon with [ftp://username@192.168.1.8](ftp://username@192.168.1.8) and it will ask me for my password. Or if I try [ftp://username:password@192.168.1.8](ftp://username:password@192.168.1.8) it will take me to my FTP home dir.

Anyone got any ideas, I know I have a working system but would like to be able to ask for the username and password with PureFTPd

---

### Post by astabeno on 2009-05-04
Sounds like your not seeing anything because you have not logged in.  So you can either pass the login in the URL, or I know IE has a login as in under the file menu.  I don't know if Firefox has that or not.

---

### Post by birdm110167 on 2009-05-04
Thanks Andrew,

Yeah I can see what you are getting at there. However, when I pass the username and/or password in the URL it works fine and I can see the directories and files on my FTP server.

My issue is that when I had PROTFTPD installed I could point my browser at the FTP server and then it asks me for a username and password, this is how I would like ti to work for my intended users.  I may have to go back to using PROFTPD.

Any more ideas as every tip appreciated muchly
Mark

---

