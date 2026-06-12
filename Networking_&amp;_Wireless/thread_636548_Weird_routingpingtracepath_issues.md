---
title: "Weird routing/ping/tracepath issues"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by CRCarl on 2007-12-09
All - 
   I've got an issue that has stumped me. 7.10 running with no problems for about 3 months now, my primary desktop. Starting about three days ago access to random bits of the internet became impossible. DNS resolution is working, ```
dig google.com
``` gets the expected results, but ```
telnet google.com 80
``` never connects. I can't ping or tracepath to any sites; even sites I can access with firefox. I have three other machines using the same DD-WRT router, no problems. ```
route -n
``` looks fine, so does```
 cat /etc/hosts
```
 
   I ran wireshark then tried```
 tracepath google.com
``` I got a single A record lookup and a response to that lookup then absolutely no additional traffic. I  re-installed net-base```
 sudo aptitude reinstall netbase
``` that did not help. 

  Any ideas???

---

### Post by Lostincyberspace on 2007-12-09
Google must be refusing telnet since it happens to me too.
I wouldn't worry if I were you though.

---

### Post by CRCarl on 2007-12-09
Adding the 80 after the telnet command is a way to test access to a site without using a browser. Try this -```
 telnet ubuntuforums.org 80
``` You connect, then type ```
get
``` and press enter. See?

---

### Post by kevdog on 2007-12-09
Sounds like a IPv6 issue!

---

### Post by CRCarl on 2007-12-10
Really? I'll disable it, but how do you figure that is the problem?

C

---

### Post by kevdog on 2007-12-10
Report back if it works.  When you are describing weird, unexplainable behaivor --  I think of Ipv6.

---

