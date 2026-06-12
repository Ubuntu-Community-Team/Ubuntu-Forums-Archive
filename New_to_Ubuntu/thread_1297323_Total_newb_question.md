---
title: "Total newb question"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by uDavis on 2009-10-21
I'm just starting my Ubuntu exp. Have it installed and installed the vcftpf service. What has me stumped is how to create an FTP user that I can use to login with remotely. then use it to transfer files to the www document area.

I created a user with adduser  , have the vsftpd service started, but that is about as far as I can get. I've been reading manuals for two days but can't google well enough to find the right stuff I think.

---

### Post by elvisd on 2009-10-21
Hi.

have found:
[http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/](http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/)
and
[http://ubuntuforums.org/showthread.php?t=518293](http://ubuntuforums.org/showthread.php?t=518293)

hope this helps

kindly

elvisd

---

### Post by uDavis on 2009-10-21
Thanks Elvisd, that second link looks like what I need to try...

---

### Post by martrn on 2009-10-21
A secure ftp server is only part of a server installation and sometimes it is best to get a book and read it all the way through.  There are many books you can buy that explain how to set up a server.  You can set up a server to serve web pages and then maintain all the users via the /home directory or you can just set up an ftp server for public acsess.

See [https://help.ubuntu.com/8.04/serverguide/C/index.html]("https://help.ubuntu.com/8.04/serverguide/C/index.html") for the ubuntu server book.  It is best in anycase to read or skim-read the whole of the server book (even if you read it via pdf) so that you can get an overview of what you are doing when you are installing managing and administering servers.

OK you won't need all of it, but it helps to understand an overview of the different functions of a server includeing securing a server, or else the whole of your server/computer can become unsecured very quickly.

---

### Post by HarrisonNapper on 2009-10-21
> **martrn said:**
> A secure ftp server is only part of a server installation and sometimes it is best to get a book and read it all the way through.  There are many books you can buy that explain how to set up a server.  You can set up a server to serve web pages and then maintain all the users via the /home directory or you can just set up an ftp server for public acsess.

See [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html) for the ubuntu server book.  It is best in anycase to read or skim-read the whole of the server book (even if you read it via pdf) so that you can get an overview of what you are doing when you are installing managing and administering servers.

OK you won't need all of it, but it helps to understand an overview of the different functions of a server includeing securing a server, or else the whole of your server/computer can become unsecured very quickly.

I hate to take up space here, but this is VERY good advice. Also, check out the guides on the Linux Documentation Project at [http://www.tldp.org](http://www.tldp.org)

Cheers.

---

