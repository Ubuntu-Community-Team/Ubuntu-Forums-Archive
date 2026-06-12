---
title: "How to troubleshoot an intermittent connection"
date: 2022-02-12
forum: Networking &amp; Wireless
---

### Post by cweijden on 2022-02-12
Hi all,

I have Ubuntu 21.04 running on an Asus PN50 mini PC.  Since about 3 weeks I am experiencing an intermittent internet connection that especially annoying while browsing.  I was able to pinpoint the problem to the Ubuntu OS running bare metal on the mini PC as no other machine has this problem in my LAN, including virtual machines running on this PC (using Virtual Machine Manager on the Ubuntu OS).  I could therefore exclude a potential issue due to my internet provider, modem/router, cabling, WiFi or mini PC hardware itself.

The issue is most notable when running the ping command.  
[LIST]
[*]When I run it continuously in most cases there is packet loss for the first 5-20 seconds, but when it starts receiving there is no packet loss until the command is stopped. 
[*]When restarting a single piing (ping -c1 google.com) in only 22% of the cases I have ping success. 
[/LIST]

How best to troubleshoot this issue?

---

### Post by TheFu on 2022-02-13
Ubuntu 21.04 is EOL.  Move to a supported release.  That would be 21.10 for now, unless you want an LTS, then 20.04 is the answer.  21.10 support ends in July.  22.04 will be an LTS with 5 yrs of normal support.  It is important to pick the correct release. If you want stability, stay with LTS.

Start with that.

---

### Post by cweijden on 2022-02-15
Thanks for the advice.  However, due to the intermittent connection I can't get past apt update...

---

### Post by rsteinmetz70112 on 2022-02-15
Have you tried running a live session to see that eliminates the problem?

---

### Post by cweijden on 2022-02-26
Yup, tried a live session. No problem there.<br>Funny thing is: neither when pinging from a virtual machine inside the OS that is showing a intermittent connection itself.

---

