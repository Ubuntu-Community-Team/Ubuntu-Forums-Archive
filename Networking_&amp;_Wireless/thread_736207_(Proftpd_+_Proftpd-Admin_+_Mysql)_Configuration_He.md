---
title: "(Proftpd + Proftpd-Admin + Mysql) Configuration Help"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by SoloLane on 2008-03-26
Hi this is my first post on Ubuntu forums so take it easy on me...

Here are the environment details:
[LIST]
[*]Ubuntu 7.10
[*]Proftpd w/ Mysql mods
[*]Proftpd Admin using PHP on Apache
[/LIST]

I have configured the FTP server and everything is working just fine. I want to now configure my proftpd.conf with some specific folder actions. Does anyone know a good guide or have some advice on how to limit access to certain Directories? Also how to hide certain Directories... 

I have tried the traditional proftpd.conf syntax and it does not seem to be working. I have a feeling this is due to the MYSQL backend. Any advice would be greatly appreciated.


Thanks Again

---

### Post by superprash2003 on 2008-03-26
are you using the ubuntu server version or desktop version?

---

### Post by SoloLane on 2008-03-26
I am using Ubuntu Desktop. Thanks for the reply.

---

### Post by superprash2003 on 2008-03-27
i would recommend you to install gproftpd . you can install it via synaptic.. its the GUI for proftpd. so its easier to setup.

---

### Post by SoloLane on 2008-03-27
I appreciate the suggestion. I have already used gproftpd in the past is is a good tool. However, I think proftpd-admin with the mysql authentication and the provided schema is a little bit more robust. It works great... I just want to tweek it a little bit. If you have anyother suggestions related to my original question it would be appreciated.  Thanks Again.

---

