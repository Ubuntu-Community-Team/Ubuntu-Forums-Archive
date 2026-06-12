---
title: "How to use thin client and ubuntu server"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by donaldd on 2006-09-13
I've been using ubuntu since breezy came out, it's been a little painful at times but I toasted my xp install and never looked back. Need to use works laptop which runs xp, it's not allowed to install anything on it so i'm happily using simplymepis live cd. I've installed dapper server on an pc with the intention of using works laptop and live cd as a thin client because boot cd's are limited.
Managed to ssh into the server but cannot run X remotely because it's not running on the server or configure a firewall, only know how to do it using a gui and firestarter. Someone recommended webmin to configure the server but I do not know a live cd that contains it, and do not know enough to create my own. 
Appreciate if someone could point me in the right direction, feels like I've been relegated to noobie again :(

---

### Post by tbonius on 2006-09-13
What exactly do you want to do to the server.. just configure a firewall?  Like IPtables?

-Shameless plug-

[http://www.section6.net/wiki/index.php/Setting_up_a_Firewall_NAT_using_IPTables](http://www.section6.net/wiki/index.php/Setting_up_a_Firewall_NAT_using_IPTables)

If your Ubuntu server has the X libraries installed.. and a Window Manager (such as Gnome).. you can also install tightvncserver and then connect to the vnc session from ANY client and use an X based desktop.

I would recommend learning to do everything via SSH in a shell.. as it will teach you a lot about Unix in general.. and will help to make a leaner, faster, and hopefully more secure server system.

T

---

### Post by donaldd on 2006-09-13
Thanks for the reply, my problem is work's xp laptop cannot boot from usb so I thought I'd take the opportunity to learn about about client - server setups. 
It's not possible to install any "non corporate" software so was thinking of using a live cd in the xp laptop as a thin client running apps via ssh?? off the server on a internal lan.
I'm okay with gnome, know little about servers and command line.
What apps to install, mail, music, office suite, maybe mythtv, open to suggestions as I'm looking at this as a learning phase exercise, when I understand what I'm doing better will do it again properly.

---

### Post by tbonius on 2006-09-13
Youre question makes no sense.  If you can run the live cd as a client to connect to your Linux server via SSH then do so.  What services are you trying to manage?

T

---

### Post by donaldd on 2006-09-13
Aah sorry see my mistake, can forward X but it also runs on server, I thought as long as application ie openoffice is runnning on server you didn't need to install desktop as well, wanted to keep it lean.

---

