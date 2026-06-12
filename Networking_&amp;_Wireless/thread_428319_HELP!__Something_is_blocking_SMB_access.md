---
title: "HELP!  Something is blocking SMB access"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by jdunn on 2007-04-30
I installed SAMBA on a fresh install of Feisty and I have a Windows XP computer in my network.  I've shared files successfully in the past between the two machines when I ran previous versions of Kubuntu (dapper, edgy).  Now, no matter what I try, I can't share between the two machines.  I first tried gui samba config.  Then I tried manual changes to the smb.conf file.  I made changes per this bug report [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460).  I can ping both machines.  Its as though there is a firewall or something blocking smb file sharing but I checked both machines and no firewalls are running.  Is there something else in Feisty that's broken?  I wouldn't be surprised.

jdunn@faramir:/etc/samba$ smbclient -L localhost
Password:
session setup failed: NT_STATUS_LOGON_FAILURE
jdunn@faramir:/etc/samba$ smbclient -L boromir
Connection to boromir failed

---

### Post by agurk on 2007-04-30
Perhaps not really helpful...but I have found two threads that seem to cover some of the potential issues:
[http://forums.fedoraforum.org/archive/index.php/t-47624.html](http://forums.fedoraforum.org/archive/index.php/t-47624.html)
[http://www.linuxquestions.org/questions/showthread.php?threadid=67766](http://www.linuxquestions.org/questions/showthread.php?threadid=67766)

Hopefully something in there can give you an idea about what's going on.

---

### Post by flint_ on 2007-05-05
One thing that can really mess you up in samba-land is the dreaded /etc/samba/smb.conf.

By way of illustration, I had the following parameter set this way:

    valid users = %S

This locked up access to samba tighter than a cats ***... 
(no offense to the feline community that frequent this site :^)

The result is illustrated in the failure of the following test:

[INDENT]root@zeta:/var/lib/samba# smbclient -L zeta -U flint
Password: 
Domain=[ZETA] OS=[Unix] Server=[Samba 3.0.22]
tree connect failed: NT_STATUS_ACCESS_DENIED[/INDENT]

While perplexing, I started fooling with the variables after reading Andrews illuminating article:

[http://andrey.thedotcommune.com/samba.html](http://andrey.thedotcommune.com/samba.html)

...and while searching the file for "users" found the fault line and changed it back to the following:

#   valid users = %S

While one may argue the enhancement of security afforded by the former stanza, the later actually works.

Regards,

Flint

---

