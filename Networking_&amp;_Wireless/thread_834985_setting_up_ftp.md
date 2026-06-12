---
title: "setting up ftp"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by Baconfatty on 2008-06-20
Hello ok so my web server has just been set up with the help of you guys.  but I still need help with one little aspect how do I set up my ubuntu box to with an FTP so I can send updates to the site with my Mac?  Also I do I set it up so I can have a user name and password to use to update?

---

### Post by dmizer on 2008-06-20
actually, i would suggest using ssh insead of ftp.  for one, ssh is encrypted and ftp is wide open.  second, mac comes with ssh by default: [http://www.nbcs.rutgers.edu/ssh/ssh_osx.php3](http://www.nbcs.rutgers.edu/ssh/ssh_osx.php3)

just install openssh-server on your webserver box, and you can access it with this command:
```
ssh username@serverip
```

then you can edit your web documents via cli like so:
```
sudo nano /var/www/index.php
```

you can transfer files from your mac to your ubuntu server with the following command:
```
scp -r filename.php username@serverip:/var/www/filename.php
```

if you're dead set on configuring an ftp server, you can take a look at the fourth third link in my sig.  it's quite a lot of work, and you'll have to change things quite a bit to get them set up to work properly with a web server.

ssh is ready to go immediately after install, but one word of caution.  do not allow external ssh access to your web server without enabling [secure keys](http://ubuntuforums.org/showthread.php?t=30709).

---

