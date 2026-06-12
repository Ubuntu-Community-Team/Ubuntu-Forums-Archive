---
title: "loosing adsl connection"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by Loki_4wd on 2007-06-08
Yesterday I've installed Ubuntu 7.04.
Used pppoeconfig to set up connection to my provider (Russian Stream). Connection works for about 30 seconds and then all the application stop getting access to the internet. I can revoke pon dsl-prover and work for 30 seconds more....
/var/log/messages says nothing about this connection loss
When trying to use pppoe-setup, I get error message that /etc/pppoe.conf is missing and that I should reinstall pppoe. But when trying to install it says I have the most recent version.

You'll be surprised, but I'm with Linux since RedHat 5.2, but since that time I haven't had any problems connecting to the Internet... I've always run some setup (wvdial, kppp, pppoe-setup) and have never had any problems. Seems like the "most friendly" Linux version is actually the most buggy one. 

Please help!!!

---

### Post by cptcrunch on 2007-06-10
try using the kernel, 2.6.20-15 and don't update to 2.6.20-16. The latest kernel update has affected countless users

---

### Post by Adam590 on 2007-06-10
Same thing was happening to me. The fix is:

run pppoeconf and get the connection, then:
$ sudo pkill -9 dhclient

Then, I think you need to enter this (not sure, but I do it, and it works):
$ pon dsl-provider

That results in a stable connection for me. Found it suggested [here]("http://ubuntuforums.org/showthread.php?t=187466").

---

