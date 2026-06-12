---
title: "UFW Hamachi problem"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by shoofy on 2008-08-17
I have two laptops both running Ubuntu. Both are running Hamachi so that I should be able to remotely network them. The problem is that one is able to connect (ssh, vnc, etc.) to the other fine, but in the reverse case UFW is blocking everything coming over Hamachi. I know that UFW is causing the problems both because disabling UFW makes everything work and because /var/log/syslog shows:
```
[UFW BLOCK INPUT]: IN=ham1
```
for every attempt to connect from the other machine.

I can't tell if there is any difference in the UFW configurations between the two machines. ufw status shows the same thing for both of them:
```
Firewall loaded

To                         Action  From
--                         ------  ----
4444:tcp                   ALLOW   Anywhere
4444:udp                   ALLOW   Anywhere
```
Where else can I look to figure out why it's blocking everything? Is there a way to set it to allow everything coming over ham1?

---

