---
title: "ADSL with Network Manager"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by Irid on 2007-03-07
Hi,
I have an ADSL Internet with a variable IP address. In a fresh install there was no Network Manager, so I simply ran pppoeconf and got things to work, although I had to run this every time after starting up. Now I got Network Manger and it's supposed to do the conf for me. OK, I have it saying "Wired Network Connection" which looks like working. If I plug out the wire, it turns down. I plug it in - it connects after a while.
Now the PROBLEM is, I can't browse, use e-mail, ftp, etc. even if I have a wired network connection up and running. Although if I disable/enable it a few times, then run pon dsl-provider a few dozen times, I finally can browse. How do I fix this issue?

---

### Post by zvacet on 2007-03-07
If you have Dapper than 
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")
but if you run Edgy 
[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")
but you have to replace Exec=gksudo /opt/rp-pppoe-3.8/go-gui>Exec=gksudo tkpppoe and  restart.It is possible that you will not see GUI.In that case 
```
sudo -i
```
```
cd /opt/rp-pppoe3.8
```
```
localhost rp-pppoe3.8#./go
```

---

### Post by Irid on 2007-03-08
I followed the instructions but still no results. At the final step I got: "bash: localhost: command not found".

---

### Post by zvacet on 2007-03-09
Sorry,my mistake.Localhost is your name(if you are root than root@localhost).Just follow command 1and 2 and you will find yourself in rp-pppoe as root.Type ./go

---

### Post by Irid on 2007-03-10
Now this works, I set up my configuration, but when I type sudo pppoe-start, it doesn't connect and says TIMED OUT. Running Rp-pppoe application doesn't help either. I still must run pon dsl-provider numerous times until it works. It always says that rp-pppoe-something is loaded. I just can't figure out what's the problem, it works, but kind of a very stupid way to make it do so.

---

### Post by Irid on 2007-03-10
I just discovered that if I type
```
sudo poff -a
sudo pon dsl-provider
```
then it works and I think that rp-pppoe is unnecessary, since it doesn't do anything. I just don't understand what -a does there...

---

