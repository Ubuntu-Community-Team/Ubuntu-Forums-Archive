---
title: "Preventing traffic limit to be reached"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by Frozen Forest on 2011-08-09
My ISP have set a limit on ~10GB per day on upload traffic, apart from this computer (ubuntu 11.04) is there also a server (ubuntu 10.04) on this LAN. My question is if there exist software that can communicate between the two computers so that there combined upload stay below 10GB. An other way to solve would be to restrict the server and desktop computer to 5GB each, then there would a software be needed that could limit traffic on a single computer. I guess something similar to netlimiter would do, or is there other ways to get around this problem?

---

### Post by MartyBuntu on 2011-08-09
File transfer and exchanges on your LAN do not count towards your ISP's allotment of bandwidth.

---

### Post by Frozen Forest on 2011-08-10
> **MartyBuntu said:**
> File transfer and exchanges on your LAN do not count towards your ISP's allotment of bandwidth.

True, but it's possible to access the server from the Internet. The server is used to share files with friends and family. Question is how to determine if traffic is local or not, could iptables solve this?

---

### Post by donkyhotay on 2011-08-10
double-post, someone beat me to it.

---

### Post by Frozen Forest on 2011-08-10
I found that the program tc can limit traffic, but it look very complicated and the guides I have found talk about limiting bandwidth (kbit/s) and not the amount. I did a small change to the iptables so that instead of jumping direct to ACCEPT when a package is accepted, will it now jump to either accept-in our accept-out. These chain then check if traffic is local or not and then accept it, by doing this will it be possible to determining how much traffic that have been sent and received, but is this an appropriate way to do things?

---

### Post by madjr on 2011-08-10
this might help for your internet cap:

[http://www.webupd8.org/2010/12/do-you-have-limited-internet-plan-use.html](http://www.webupd8.org/2010/12/do-you-have-limited-internet-plan-use.html)

---

