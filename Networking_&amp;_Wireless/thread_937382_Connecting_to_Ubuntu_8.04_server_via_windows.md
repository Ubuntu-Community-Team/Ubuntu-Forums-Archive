---
title: "Connecting to Ubuntu 8.04 server via windows"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by rhcm123 on 2008-10-03
I have recently built a server from scratch. It has 4 250 gb hdd's in a RAID 5 configuration, and is running ubuntu 8.04 server, hardwired into my home network. It works great, I installed it as a LAMP of the install prompt and added Apache, PHP, and Samba. It is going to be a file server.

My problem is, no matter what I try, I cannot connect my family's windows computers to the server. I want to configure it as a network drive, but no windows machine can see it, and the few that can cannot connect to it. 

In addition, when booting, i get 2 messages from apache.
1: apache2: apr_sockaddr_info_get() failed for USSR-SERVER
2: apache2: could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

I am able to connect to this machine via telnet and ssh, but I am not able to get to my shared folder (aka /home/shared/)
How do I configure this system so that my machines (as well as my ubuntu machines, as they cannot see the server as well) to connect to the drives.

---

### Post by r m h on 2008-10-04
I'll take a stab at this, but since your description is too vague, I may be answering a different problem than you really have.

I think you need to fix your samba configuration:
did you modify /etc/samba/smb.conf for what and how you want to share?
is your workgroup set properly in smb.conf
did you setup a new share [<share name>]?
did you set up the new share with:
        path = /home/shared
        browseable = yes
        read only = no
        valid users = user1 user2 ...
did you set up your /etc/samba/smbusers file?
did you set your users' samba passwords via smbpasswd?
did you give the list of valid users permissions to the share?
and finally after all of the above, did you start/restart samba (/etc/init.d/samba start | restart)?

When you do the above, you will be asked for a username and password when you connect to the samba share, providing you use user security (always a good idea).

---

### Post by rhcm123 on 2008-11-01
Aargh... stupid stupid mistake!
I forogot to to smbpasswd!
thanks for reminding me of that
(i feel like such an idiot now... goes and cries in corner, next to now-working file server)
:lolflag:

---

