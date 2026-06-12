---
title: "curlftpfs connection issue"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by Jenga201 on 2008-12-02
Hello everybody,

I started using curlftpfs to mount an ftp server as a drive using ubuntu 8.10. I will eventually have a website get files off of that mounted drive if i can get everything working properly.

Currently i am able to mount the ftp server and i can access files from the mount point through my webserver.  The reason i am mounting the ftp share like this to get files using a website is because this particular ftp is restricted to only allowing connections from my server...i figure it's the easiest way to directly access those ftp files from the website.

Using 1 transfer like this works fine; curlftpfs connects and starts feeding the file to my webserver.  However, while using 2 transfers i get the welcome text for the ftp server many times.  It seems that curlftpfs is logging in to take some data for the first request, logging out, then logging in to take some data for the 2nd request, etc...

I mount the ftp server using this command:
```
sudo curlftpfs -d -v -o allow_other,umask=0000 ftp://username:password@hostname /home/site/archive/
```

Is there any way to make curlftpfs just open a new ftp connection to service each transfer?

Please help me with the curlftpfs stuff !! :)

Thank you

---

