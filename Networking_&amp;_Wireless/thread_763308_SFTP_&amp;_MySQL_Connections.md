---
title: "SFTP &amp; MySQL Connections"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by bml137 on 2008-04-22
I have been having an issue for a couple months now that I am just now asking for help on.  I have exhausted all my options...

I have two computers behind a router.  Computer A has a static IP: 192.168.13.21.  Computer B has a dynamic IP of 192.168.13.10x.  I have a computer C over the Internet located in a different state hosting my website.

ssh:
A to B/C: ok
B to A/C: ok
C to A/B: ok

sftp:
A to B: fails
A to C: ok
B to A: fails
B to C: ok
C to A: ok
C to B: ok

mysql:
A to C: ok
B to A: fails
B to C: ok
C to A: ok

sftp: fails = stalls on "debug2: channel 0: open confirm rwindow 0 rmax 32768"
mysql: fails = ERROR 2013 (HY000): Lost connection to MySQL server at 'reading authorization packet', system error: 0

Basically, I am having major issues getting A and B to talk to each other, but they are on the same network; behind the same router.  I have tried to use their local IPs and I have tried to use the router's global IP with the appropriate open ports and it B still can't connect to A.

I just now tried SFTP and found that it is having similar issues to MySQL.  I thought maybe this will be easier for others to figure out since it isn't application specific.

iptables -L has all chains ACCEPT.  I am running kubuntu/hardy on B and had the problem with mythbuntu/gutsy and mythbuntu/hardy on A.

Thanks,
Brian

---

### Post by bml137 on 2008-05-06
bump (still the exact same issue)

---

### Post by bml137 on 2008-06-17
I am still having this issue and have had it for several months now.  I don't have the slightest clue as to what is causing it.

---

### Post by superprash2003 on 2008-06-17
i remember i had a similar issue.. it required me to set permissions to access mysql from another pc.. i had done it using phpmyadmin [http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin) .Allow x.x.x.x to access mysql where x.x.x.x is the ip of computer B

---

