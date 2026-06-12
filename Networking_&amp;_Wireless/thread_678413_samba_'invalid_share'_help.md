---
title: "samba 'invalid share' help"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by stevieb on 2008-01-25
hello,

when i try to access a samba share, i get the following error on the client:

```
5181: tree connect failed:  ERRDOS - ERRnosuchshare (You specified an invalid share name
SMB connection failed
```

here's my smb.conf; any idea what the problem is?

```
# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2008/01/25 21:06:12

[global]
	workgroup = MSHOME
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	valid users = steve
	hosts allow = 192.168.1.

[/home/steve]
	path = /home/steve
	read list = steve
	write list = steve
	read only = No
	guest ok = Yes

```

---

### Post by benanzo on 2008-01-25
I'm not entirely sure, but don't think SMB shares can have / (slashes) in the name.  Just name it **home_steve** or similar and see if that works.

---

### Post by stevieb on 2008-01-26
you're going to have to be more specific.  rename /home/steve to /home_steve?  what about the linux filesystem hierarchy?   should i end up with /home_steve/steve or home/home_steve in my filesystem?

i don't think that's the correct way to solve this...  i'm going to try just sharing the /home directory and see where that takes this.  in the meantime, here's some more of the client side play-by-play:

```
steve@satch:~$ nmblookup -T "*"
querying * on 192.168.1.255
new-host.home, 192.168.1.6 *<00>
steve@satch:~$ nmblookup -SA 192.168.1.6
Looking up status of 192.168.1.6
        CANNONBALL      <00> -         B <ACTIVE> 
        CANNONBALL      <03> -         B <ACTIVE> 
        CANNONBALL      <20> -         B <ACTIVE> 
        MSHOME          <00> - <GROUP> B <ACTIVE> 
        MSHOME          <1e> - <GROUP> B <ACTIVE> 

        MAC Address = 00-00-00-00-00-00

steve@satch:~$ smbclient -L CANNONBALL
Password: 
Domain=[CANNONBALL] OS=[Unix] Server=[Samba 3.0.22]

        Sharename       Type      Comment
        ---------       ----      -------
        /home_steve     Disk      
        IPC$            IPC       IPC Service (cannonball server (Samba, Ubuntu))
        ADMIN$          IPC       IPC Service (cannonball server (Samba, Ubuntu))
Domain=[CANNONBALL] OS=[Unix] Server=[Samba 3.0.22]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        MSHOME               
steve@satch:~$ smbmount //192.168.1.6/home_steve/ Desktop/cannonball
Password: 
5529: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed
steve@satch:~$ smbclient //CANNONBALL/home_steve
Password: 
Domain=[CANNONBALL] OS=[Unix] Server=[Samba 3.0.22]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

```

---

### Post by stevieb on 2008-01-26
no luck:

```
steve@satch:~$ smbmount //192.168.1.6/home Desktop/cannonball
Password: 
5543: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

steve@satch:~$ smbclient //cannonball/home -U steve
Password: 
Domain=[CANNONBALL] OS=[Unix] Server=[Samba 3.0.22]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

```

here's my current smb.conf; i'm trying to keep it as simple as possible- hope i haven't left anythning out...

```
# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2008/01/26 08:59:46

[global]
	workgroup = MSHOME
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	valid users = steve
	hosts allow = 192.168.1.

[/home/steve]
	path = /home
	read only = No
	
```

---

### Post by stevieb on 2008-01-26
i think i may have solved this- the mount command needs to reference the appropriate section of the smb.conf file, and not the path to the  shared folder itself.

so, it should be 
```
 sudo mount -t smbfs //192.168.1.6/homes Desktop/cannonball/ -o username=steve
```

and not 
```
 sudo mount -t smbfs //192.168.1.6/home/steve Desktop/cannonball/ -o username=steve
```

i changed the relevant section in the smb.conf per benanzo's idea:
```

[homes]
	path = /home/steve
	read list = steve
	write list = steve
	read only = No
	guest ok = Yes

```

i'll play around a bit more, and see if i can access this through a windows box, too.  looks like benanzo may be right!

-steve

---

### Post by benanzo on 2008-01-26
You don't mount shares by pathname on the server, you mount them by share name.  For instance, if you had this in your smb.conf:

```

[home_steve]
	path = /home/steve
	read list = steve
	write list = steve
	read only = No
	guest ok = Yes

```

You would mount with:
```
 sudo mount -t smbfs //192.168.1.6/**/home_steve** Desktop/cannonball/ -o username=steve
```
Not:
```
 sudo mount -t smbfs //192.168.1.6**/home/steve** Desktop/cannonball/ -o username=steve
```

The SMB client doesn't know or care what the actual path to the dir you're mounting is, only the workgroup, server and share name.

Also, use *cifs* instead of *smbfs* since smbfs is deprecated and is no longer being maintained.

---

