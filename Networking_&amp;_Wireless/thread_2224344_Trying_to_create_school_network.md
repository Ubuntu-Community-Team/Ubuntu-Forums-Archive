---
title: "Trying to create school network"
date: 2014-05-15
forum: Networking &amp; Wireless
---

### Post by amaress on 2014-05-15
Hi!

I'm pretty much totally new to Ubuntu.  Our charter school received 11 donated computers with no operating system so we installed Ubuntu on 10 of them and Ubuntu server on one.  The goal is to create log in accounts for the students so they can log on any computer and have their setting and files available - with limited access to computer settings.  

I'm pretty sure I'm on the right track installing openLDAP and phpldapadmin.  If I go to the server's IP address on my computer it has the splash screen that says it works (yay!) but at the moment I can't access the /phpldapadmin web interface from my computer, it says 404 not found.  I can't figure out what I am doing wrong.  This is the guide I am following:  [https://www.digitalocean.com/community/articles/how-to-install-and-configure-a-basic-ldap-server-on-an-ubuntu-12-04-vps](https://www.digitalocean.com/community/articles/how-to-install-and-configure-a-basic-ldap-server-on-an-ubuntu-12-04-vps)

Am I going about this the right way, or should I be looking at a different solution?  

Thank you!

---

### Post by smss on 2014-05-16
Try with MAAS

---

### Post by spynappels on 2014-05-16
Are you planning to network them with Ethernet cable? If you are, and the server is beefy enough, you could also look at the LTSP project, which is essentially a Thin Client solution based on Linux and appears to fit your bill exactly.

---

