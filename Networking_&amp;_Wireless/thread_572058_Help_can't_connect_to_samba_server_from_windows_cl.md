---
title: "Help: can't connect to samba server from windows client"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by mixersoft on 2007-10-10
I've set up a public samba share on my server, testparm shows this output:

```

[shared]
        comment = Shared folder (read only)
        path = /home/shared
        force user = editor
        force group = users
        create mask = 0777
        directory mask = 0777
        guest ok = Yes

```

From the shell on my ubuntu server, I can type 

```

> smbclient \\\\10.1.1.1\\shared -U editor  

```

 with no password and get "anonymous login successful", or I can use the correct password and also connect successfully.

But when I try to connect from a windows pc using the following:

```

>  net use Y: \\10.1.1.1\shared

```

I get an error 67,  can't find the network's name. What am I doing wrong? 

I can also try to map a network drive using the file explorer, but it keeps asking for the password, regardless of what I put in.  Also, I can check /var/log/samba but there are no entries when I try to connect from the Windows client

PS: I know I may have a samba//firewall problem, but I am trying use the ipaddress directly to avoid a wins lookup.

---

### Post by mixersoft on 2007-10-10
any ideas on this one?

---

