---
title: "Set up FTP in Ubuntu Server (Intrepid)"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by TMcKSmith on 2009-03-03
I've tried a couple of tutorials and resources with no luck.  What's the best way to set up an FTP on my Ubuntu Server?

What I'd like is to set a certain folder on my machine to be accessible for people to download files from to their own machines.  I don't want them to be able to delete or anything on my server though...but once they download said files to their own machine they can do whatever they please.

Any tips or resources would be appreciated.

---

### Post by Benic on 2009-03-03
Did you try lftp?

---

### Post by OffAxis on 2009-03-03
Do you really need it to be ftp?

I've always found the FTP system user login a bit annoying when running an FTP server by itself.

If you want to manage a plethora of logon credentials have a look at this article:
[http://howtoforge.com/vsftpd_mysql_debian_etch](http://howtoforge.com/vsftpd_mysql_debian_etch)


If it's just a few files you could always just go with http.

Here's some info if you want to password protect a directory:

[http://httpd.apache.org/docs/2.0/howto/htaccess.html](http://httpd.apache.org/docs/2.0/howto/htaccess.html)

---

