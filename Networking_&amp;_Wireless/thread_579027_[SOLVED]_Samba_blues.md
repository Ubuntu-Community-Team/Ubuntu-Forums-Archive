---
title: "[SOLVED] Samba blues"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by nowhere@cox.net on 2007-10-17
Hi,

I can't seem to get my machine to appear on the network. I have several XP boxes and they cannot see this samba server.  I can ping, ssh in, view web pages on the same server.

My smb.conf file is pathetically simple, in attempts to get this working:
```
[global]
	workgroup = MIDDLEEARTH
	security = share
	netbios name = mythbox
[mythdata]
	comment = MythTV
	path = /mythdata
	read only = Yes
	guest ok = Yes
```

when I run testparm I get
```
testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[mythdata]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MIDDLEEARTH
        security = SHARE

[mythdata]
        comment = MythTV
        path = /mythdata
        guest ok = Yes

```

You will notice that the netbios line is not echoed there. Hmmmm... This bad? In all the examples I see of the output of testparm, netbios line is present....

Here is output of smbclient -L localhost -U%
```

Domain=[MIDDLEEARTH] OS=[Unix] Server=[Samba 3.0.26a-0.fc7]

        Sharename       Type      Comment
        ---------       ----      -------
        mythdata        Disk      MythTV
        IPC$            IPC       IPC Service 
Domain=[MIDDLEEARTH] OS=[Unix]

        Server               Comment
        ---------            -------
        GALADRIEL            H's Laptop
        MYTHBOX              

        Workgroup            Master
        ---------            -------
        MIDDLEEARTH          GALADRIEL
```

My samba box see's everyone else but no one sees it. The other 

Also, with every guide/howto I have read, it is still confusing with all the usernames. There's you linux login, there is the samba client user name, there is also the windows username. Which one are they talking about where?

Any ideas?
Thanks,
Eric

---

### Post by scrooge_74 on 2007-10-17
[http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138](http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138)
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by nowhere@cox.net on 2007-10-17
Thanks for trying to help but listing general howto's isn't very helpful. I'm not trying to be rude or anything but:

> [http://www.ubuntuforums.org/showthre...=open+port+138](http://www.ubuntuforums.org/showthre...=open+port+138)
Im not running a firewall.

> [http://www.ubuntuforums.org/showthre...=open+port+138](http://www.ubuntuforums.org/showthre...=open+port+138)
I started here. My conf file is way stripped down compared to the one the author wants me to "paste" in.

> [https://help.ubuntu.com/community/Ac...ryWinbindHowto](https://help.ubuntu.com/community/Ac...ryWinbindHowto)
I just want to connect as guest to my shared folder. In Fedora, I used a very simple conf file like this and a guest user and it worked fine.

Can someone have a look at the info I posted and see if there is an error I am missing please?

Thanks,
Eric

---

### Post by scrooge_74 on 2007-10-17
Sorry mate, that is the way I learn how to do things, by reading. In some cases what applies to one PC is not exactly the same for another so you need to know the basic procedure.

Most likely you need to check on winbind it tends to resolve some issues with XP.  Sorry If cant be more helpfull it has been a while since I last needed samba

---

### Post by nowhere@cox.net on 2007-10-17
OK no problem. Thanks for trying. I will keep pluggin at it as I get time. In the meantime I will drag the external drive down to move file. Will probably be faster anyway...

Thanks :)

Eric

---

