---
title: "NFS Export File Setup"
date: 2014-01-23
forum: Networking &amp; Wireless
---

### Post by charles6 on 2014-01-23
[COLOR=#000000][FONT=Verdana]Hi guys,[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Currently I have to 2 media drives mounted on my Ubuntu server /media/Movies and /media/Music. I have my exports file setup to share these 2 locations. 

When I read the setup for NFS it mentioned to created a directory for your shared folders ex: /export/Movies. 

What is the purpose of creating a directory and sharing them that way instead of just sharing the drives? Is it security? If so, my export setup is set as read-only for these 2 locations.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Thanks.[/FONT][/COLOR]

---

### Post by cjhabs on 2014-01-24
If you share a folder within the drive it allows you to share different folders with different permissions, or to just share parts of the drive and keep parts not shared. It seems that for your needs sharing the whole drive is absolutely fine.

---

