---
title: "How to use SIFY Client ?"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by rams123 on 2008-10-20
I am using Sify (Internet Connection). So I had downloaded sify client (aka Cyberoam Client or 24 Online Client) and extracted .tar.gz file using ark. 

Then I had logged in through Konsole(Terminal). 
By using this command - cd /home/ram/desktop/crclient and ./crclient -u myusername .
I had also received you have succesfully logged into server ***.***.**.** (rough).

But the problem is still my internet is not working ? What to do ? 

Please i need your help !

---

### Post by davesher on 2009-10-11
[B]AT FIRST CONFIG YOUR ETHERNET CARD's IP ADDRESSES THEN FOLLOEW THESE STEPS.


1. go to [http://202.144.65.70:8090/linuxinstall.html](http://202.144.65.70:8090/linuxinstall.html)

   Download [Sify Broadband Client ]("http://202.144.65.70:8090/bbandclient_v30/sify_bbclient-3.0.tar.gz") for Linux OS NON RPM supported systems

2. tar -xvf sify_bbclient-3.0.tar
 
3 On terminal  cd sify_bbclient-3.0

4. As being root run command 
    ./install.sh

5. Now on terminal follow these commands
    
   # cd /usr/lib 
   # ln -s libcrypto.so.0.9.8 libcrypto.so.4 
   # ln -s libssl.so.0.9.8 libssl.so.4

6. now run command
   # sifyconnect

7. Sify dailer will com insert username & password Then connect n enjoy.[/B]


All these steps are for UBUNTU 9.04

---

### Post by BalaViknesh on 2009-11-20
Can u send me screenshots of configuring ethernet Plz.

---

