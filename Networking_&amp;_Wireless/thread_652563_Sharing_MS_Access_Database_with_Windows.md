---
title: "Sharing MS Access Database with Windows"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by Gwaihirjp on 2007-12-28
Hello everyone, I'm new to Ubuntu and this is my first post here. I've installed Ubuntu server at my workplace, and it's working so well, I'm loving the experience! But I have just one problem that I can't seem to solve, and I'm hoping that someone here might have the answer.

You see, I installed Ubuntu server as the file server at my workplace, which has a network that consists of about 10 Windows Vista boxes on a wired LAN connection. What my boss wants me to do with the Ubuntu server is to share some Microsoft Word and Excel files through it, but most importantly to use it to share the company's Microsoft Access Database. The database is split: there's a shortcut file on each Windows box which connects to one Access file which contains the tables.

I've succeeded in starting up Samba, so Ubuntu and Windows can see and access each other. The Windows boxes can also open and edit the Word and Excel files (and almost everything else) on the shared Ubuntu folder perfectly well. 
But when the Windows boxes attempt to open the Access database, the problem starts. Only up to 2 or 3 users can access the database at any given time, even though Access is supposed to allow many concurrent users. When more people try to access the database, a popup comes up saying "file is already in use" or something like that. The lucky few who do get access to the database experience no problems in editing it.
I've allowed read/write access to all the Windows boxes, but that hasn't changed anything. This is a problem that we never had back when the database was on a Windows XP box so I really have no clue. 

I'm not sure if this occurs because of some Samba settings or because of the faulty Access Database itself. Maybe it would be better if I migrated the back-end table file from Access to MySQL?

Thank you in advance for any pointers. I really hope someone can help.

---

