---
title: "Help with Samba"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by everythingelsewastaken on 2011-04-26
Hi

I am new to Ubuntu, having sparingly used OpenSUSE with KDE before. I am now running Ubuntu Server edition, 10.10 32 bit.

Currently, I can SSH into this machine and I have managed to give it a static ip within my LAN network. However I have run into trouble with setting up Samba. My Windows computer cannot see the share and smbclient -L on the computer itself fails (error message is below in the post)

My smb.conf file looks like this (everything else is commented):
> 
[global]
   workgroup = MYCASTLE
log file = /var/log/samba/log.%m
 max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
security = share
unix password sync = yes
passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
 map to guest = bad user
usershare allow guests = yes

[share]
        comment = Troll's AV Directory
        path = /av
        force user = nobody
        force group = nogroup
        browsable = yes
        guest ok = yes
        read only = no



The file permissions on the /av folder are 777, with the owner as nobody and the group as nogroup.

Typing the computer's static IP on another computer within the LAN displays a default page from apache, so the computer is definitely connected to the network.

Using> sudo service nmbd restart
restart: Unknown instance:
gets the result above.

If I use smbtree, I get > MYCASTLE
        \\WRAITH
        \\GHOUL


Which is what I would expect.

Attempting to do this gets the following result: (I'm not sure what it is, but it was recommended http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/problems.html" here.

>  smbclient -L BIGCLIENT
Connection to BIGCLIENT failed (Error NT_STATUS_BAD_NETWORK_NAME)


Or:

> smbclient -L 127.0.0.1
Domain=[MYCASTLE] OS=[Unix] Server=[Samba 3.5.4]
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: NT_STATUS_ACCESS_DENIED



I am sorry if the solution is plain obvious or I have missed something with my googling. But help would be much appreciated :(

Thankyou.

---

### Post by everythingelsewastaken on 2011-07-03
Just because I called my computer Troll, does not mean that what was what I was trying to do to this forum.

Anyway, I ended up wiping and starting again and I've got it working now.

---

