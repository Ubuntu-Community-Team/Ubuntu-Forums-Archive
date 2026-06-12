---
title: "Trouble accessing Samba share over PPTP VPN"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by jtizzle on 2007-09-28
I have been searching for an answer for a while now and don't know where else to turn.  Anway, I am running a Ubuntu 6.06 Server with the latest version of Samba and VPN.    I mapped a drive from my XP machine to the file share and connect just fine on my home network.  However when connecting remotely to the VPN I cannot get to my Samba share drive.  The server asks  me to enter a username and password but when I do its says incorrect login.  

After researching a bit I found that Samba will not except encrypted password, only clear text.  So I changed the setting in XP on the local security policy for plain passwords to be sent to third party VPN.  Still didn't work.  I am at a dead end here, can someone help?

---

