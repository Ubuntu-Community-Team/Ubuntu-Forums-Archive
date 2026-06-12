---
title: "Ubuntu cannot connect to Samba but Windows can"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by nexist on 2008-08-05
I have a Samba Server running Ubuntu Server 8.04. My windows system can access the share for my home directory in read/write without any problems. Ubuntu cannot. The GUI does not work (password repeats) and the command line gives the following:

```
nexist@nexist-desktop:~$ smbclient \\\\obelisk\\nexist -U nexist
Password: 
Domain=[ARIYAS] OS=[Unix] Server=[Samba 3.0.28a]
Server not using user level security and no password supplied.
tree connect failed: NT_STATUS_WRONG_PASSWORD
nexist@nexist-desktop:~$ 
```

Thing is, the password is the same one I type in when I use ssh. It is also the same one on both the Windows system and the Ubuntu system.

```
nexist@obelisk:~$ cat /etc/samba/smb.conf
[global]
workgroup = ARIYAS
security = SHARE
printing = CUPS
printcap name = CUPS
show add printer wizard = No

[Plans]
path = /export
read only = Yes
guest ok = Yes

[homes]
comment = Home Directories
valid users = %S
read only = No
browseable = No

[printers]
comment = Print Temporary Spool Configuration
path = /var/spool/samba
printable = Yes
guest ok = Yes
use client driver = Yes
browseable = No
```

Anyone have any ideas?

---

### Post by dmizer on 2008-08-05
A couple of things.  First of all, your smb.conf does not include a server name for your computer.  Add this line to your smb.conf after the "workgroup" option:
```
netbios name = obelis
```
Your server name doesn't have to be "obelis", I just pulled it from your CLI prompt.

Second, you'll need to make sure that your ubuntu client is a member of the ARIYAS workgroup by going to: System -> Administration -> Shared Folders

If you're still having problems after that, you can take a look at the second link in my sig.

---

### Post by ktrnka on 2008-08-06
you can specify the workgroup adding the -W parameter.

Try this:

```
smbclient //oblisk/nexist -W ARIYAS -U nexist 

```

---

### Post by dmizer on 2008-08-06
> **ktrnka said:**
> you can specify the workgroup adding the -W parameter.

Try this:

```
smbclient //oblisk/nexist -W ARIYAS -U nexist 

```

In this case, workgroup is not the problem because it's properly configured in the smb.conf file.  The problem is that there is no Netbios name specified for the server.

---

### Post by ktrnka on 2008-08-06
It appears that his computer is already communicating with the server. So I don't think it's just a netbios issue.

Could it possibly be that he didn't create a samba user?

> sudo smbpasswd -a nexist 

---

### Post by dmizer on 2008-08-06
> **ktrnka said:**
> It appears that his computer is already communicating with the server. So I don't think it's just a netbios issue.
Unfortunately the NT_STATUS_WRONG_PASSWORD error is not very revealing.  This error appears if you don't have smbfs installed, it appears if you don't have proper netbios configuration, it appears with incorrect options, and various non-password related issues.

> **ktrnka said:**
> Could it possibly be that he didn't create a samba user?
If there was no samba user, then the XP machine would not have been able to log in.

---

### Post by ktrnka on 2008-08-06
> **dmizer said:**
> Unfortunately the NT_STATUS_WRONG_PASSWORD error is not very revealing.  This error appears if you don't have smbfs installed, it appears if you don't have proper netbios configuration, it appears with incorrect options, and various non-password related issues.


If there was no samba user, then the XP machine would not have been able to log in.

Very true. 

nexist: Try connecting via ip address

---

### Post by dentaku65 on 2008-08-06
I think there is something missing in your Global section of the smb.conf file; here I suggest some modifications:
```

[global]
workgroup = ARIYAS
preferred master = No
local master = No
domain master = No
;hosts allow = 192.168.1.0/255.255.255.0
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
passdb backend = tdbsam
null passwords = true
username map = /etc/samba/smbusers
name resolve order = lmhosts bcast wins host
wins support = no
printing = CUPS
printcap name = CUPS
syslog = 1
syslog only = yes


```

---

