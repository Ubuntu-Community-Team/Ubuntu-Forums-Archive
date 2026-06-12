---
title: "Network connections without passwords"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by ajskillet on 2008-01-08
Hi. I need some help. I'm a Linux newbie coming over from a Windows network admin. I finally got Ubuntu installed and have samba running. I can see all my Window servers and shares drom the Ubuntu server. And now I can dee my Ubuntu server from my Windows networks. 

Now all I want to do is let some users access this server without having to create logons for each and have them enter thier login each and every time. Is this possible? I have a share created. I would just like to map to it from thier XP machines and be done with it. What is the best way of doing this?

Currently a login box pops up, but I cannot connect with the user info I set up on installation.

-AJ

---

### Post by ajskillet on 2008-01-10
Nevermind. I changed security = share and commented out a few other things in the smb.conf file. And then changed the share permissions, I can access the folder from any Windows computer. 

It sure was a lot of work to get Ubuntu server up and running with a GUI ans folder shares across the network. Too many problems. My boss installed SUSE and had it up and running in a day.

Now if i could only get it to recognize my external SCSI tape drice I'd be set.

---

