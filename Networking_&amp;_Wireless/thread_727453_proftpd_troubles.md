---
title: "proftpd troubles"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by n8dude on 2008-03-17
Hey, my server is running ubuntu server 7.10 and i've been fighting with proftpd for awhile now.I used to use proftpd all the time, but it seems that it has just "broke" for no good reason. I tried reinstalling it, making a new config file, but nothing seems to be working so I thought maybe one of you would know. his is the error it gives me when I try to start it or restart it:
iamroot@server1-clearbox:/$ sudo /etc/init.d/proftpd restart

 * Stopping ftp server proftpd                                           [ OK ] 
 * Starting ftp server proftpd                                                   
- IPv6 getaddrinfo 'server1-clearbox' error: Name or service not known
                                                                                           [ OK ] 

I think it is something to do with my networking gear, but I am not sure. I will post my config file if needed. 
Thanks in advance, n8dude

---

