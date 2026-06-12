---
title: "Massive issue with File Sharing between Ubuntu 14.04 and Windows 7"
date: 2016-05-11
forum: Networking &amp; Wireless
---

### Post by The_Woodpecker on 2016-05-11
Hi all,

Recently I updated my laptop from Ubuntu 12.04 to 14.04 and ever since I can't for the life of me get file sharing to work. No matter if I use the file sharing option or Samba; nothing works at all. 

This is the error message I get from Windows 7 [ATTACH=CONFIG]268993[/ATTACH]

What can I do to make this work? Why doesn't it work now in 14.04?

---

### Post by bab1 on 2016-05-11
> **The_Woodpecker said:**
> Hi all,

Recently I updated my laptop from Ubuntu 12.04 to 14.04 and ever since I can't for the life of me get file sharing to work. No matter if I use the file sharing option or Samba; nothing works at all. 

This is the error message I get from Windows 7 [ATTACH=CONFIG]268993[/ATTACH]

What can I do to make this work? Why doesn't it work now in 14.04?
These days "file sharing" is a pretty vague  term.  Are you sharing files that reside on a Windows machine?  Or are you sharing files the reside on the Ubuntu machine?  Or both?  If we are talking about sharing files that are on the Ubuntu machine, how did you share them?  With the GUI (right click >> Share ) or by configuring the smb.conf file?

It is easier to diagnose the problem with more knowledge of your file sharing setup.

---

### Post by The_Woodpecker on 2016-05-12
> **bab1 said:**
> These days "file sharing" is a pretty vague  term.  Are you sharing files that reside on a Windows machine?  Or are you sharing files the reside on the Ubuntu machine?  Or both?  If we are talking about sharing files that are on the Ubuntu machine, how did you share them?  With the GUI (right click >> Share ) or by configuring the smb.conf file?

It is easier to diagnose the problem with more knowledge of your file sharing setup.

Hey I am trying to share files between my Ubuntu Laptop and my Windows Desktop. The laptop would be the 'server' so to speak, I have tried doing it both manually and through the GUI

---

### Post by bab1 on 2016-05-12
> **The_Woodpecker said:**
> Hey I am trying to share files between my Ubuntu Laptop and my Windows Desktop. The laptop would be the 'server' so to speak, I have tried doing it both manually and through the GUI
Post the output of these Ubuntu terminal commands (# lines are my *[COLOR="#0000CD"]comments[/COLOR]* only)```

# list the samba processes
pgrep -l mbd

# display all shares in the network
smbtree -d3

# display the Samba server conf file
cat /etc/samba/smb.conf

# display the samba usershares
net usershare info --long

``` 

Please post the text output using [noparse]```
  
```[/noparse] code blocks.  This preserves the text formatting and makes the output easier to read.  The easiest way to do the is to click on the [SIZE=5]**#**[/SIZE] icon and pasting the text between the blocks.

---

### Post by The_Woodpecker on 2016-05-13
> **bab1 said:**
> Post the output of these Ubuntu terminal commands (# lines are my *[COLOR=#0000CD]comments[/COLOR]* only)```

# list the samba processes
pgrep -l mbd

# display all shares in the network
smbtree -d3

# display the Samba server conf file
cat /etc/samba/smb.conf

# display the samba usershares
net usershare info --long

``` 

Please post the text output using [noparse]```
  
```[/noparse] code blocks.  This preserves the text formatting and makes the output easier to read.  The easiest way to do the is to click on the [SIZE=5]**#**[/SIZE] icon and pasting the text between the blocks.

```
 
luke@luke-HP-Ubuntu:~$ pgrep -l mbd
659 smbd
1077 smbd
1128 smbd
1368 nmbd 
```

```

luke@luke-HP-Ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface eth2 ip=192.168.1.20 bcast=192.168.1.255 netmask=255.255.255.0
Enter luke's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.20 ( 192.168.1.20 )
Connecting to 192.168.1.20 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'spnego' registered
GENSEC backend 'schannel' registered
GENSEC backend 'naclrpc_as_system' registered
GENSEC backend 'sasl-EXTERNAL' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'ntlmssp_resume_ccache' registered
GENSEC backend 'http_basic' registered
GENSEC backend 'http_ntlm' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.20 ( 192.168.1.20 )
Connecting to 192.168.1.20 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
    \\LUKE-HP-UBUNTU         luke-HP-Ubuntu server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name LUKE-HP-UBUNTU<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name LUKE-HP-UBUNTU<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name LUKE-HP-UBUNTU<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
        \\LUKE-HP-UBUNTU\Upload             
        \\LUKE-HP-UBUNTU\Deskjet_F2200      Downstairs Family Inkjet
        \\LUKE-HP-UBUNTU\Canon-BJC-250      Canon BJC-250
        \\LUKE-HP-UBUNTU\IPC$               IPC Service (luke-HP-Ubuntu server (Samba, Ubuntu))
        \\LUKE-HP-UBUNTU\Uploads            
        \\LUKE-HP-UBUNTU\Desktop            
        \\LUKE-HP-UBUNTU\print$             Printer Drivers

```

```

luke@luke-HP-Ubuntu:~$ net usershare info --long
[Upload]
path=/home/luke/Videos/Videos for upload
comment=
usershare_acl=Everyone:R,Unix User\luke:F,
guest_ok=n

[Desktop]
path=/home/luke/Desktop
comment=
usershare_acl=Everyone:R,Unix User\luke:F,
guest_ok=n

```

---

### Post by bab1 on 2016-05-13
> **The_Woodpecker said:**
> ```
 
luke@luke-HP-Ubuntu:~$ pgrep -l mbd
659 smbd
1077 smbd
1128 smbd
1368 nmbd 
```

```

luke@luke-HP-Ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface eth2 ip=192.168.1.20 bcast=192.168.1.255 netmask=255.255.255.0
Enter luke's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.20 ( 192.168.1.20 )
Connecting to 192.168.1.20 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'spnego' registered
GENSEC backend 'schannel' registered
GENSEC backend 'naclrpc_as_system' registered
GENSEC backend 'sasl-EXTERNAL' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'ntlmssp_resume_ccache' registered
GENSEC backend 'http_basic' registered
GENSEC backend 'http_ntlm' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.20 ( 192.168.1.20 )
Connecting to 192.168.1.20 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
    \\LUKE-HP-UBUNTU         luke-HP-Ubuntu server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name LUKE-HP-UBUNTU<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name LUKE-HP-UBUNTU<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name LUKE-HP-UBUNTU<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
        \\LUKE-HP-UBUNTU\Upload             
        \\LUKE-HP-UBUNTU\Deskjet_F2200      Downstairs Family Inkjet
        \\LUKE-HP-UBUNTU\Canon-BJC-250      Canon BJC-250
        \\LUKE-HP-UBUNTU\IPC$               IPC Service (luke-HP-Ubuntu server (Samba, Ubuntu))
        \\LUKE-HP-UBUNTU\Uploads            
        \\LUKE-HP-UBUNTU\Desktop            
        \\LUKE-HP-UBUNTU\print$             Printer Drivers

```

```

luke@luke-HP-Ubuntu:~$ net usershare info --long
[Upload]
path=/home/luke/Videos/Videos for upload
comment=
usershare_acl=Everyone:R,Unix User\luke:F,
guest_ok=n

[Desktop]
path=/home/luke/Desktop
comment=
usershare_acl=Everyone:R,Unix User\luke:F,
guest_ok=n

```
The server looks to be up.  It can see itself and all the shares.  My guess it that the usershares are not allowing the Windows user access.  You have limited Everyone to read only and the Unix User\Luke to full access.

I would try less restrictive sharing (at least temporarily).  If that doesn't work I would delete these shares and recreate them in the /etc/samba/smb.conf file.  If you add the shares to the  /etc/samba/smb.conf file, you need to reboot the server with this command```
sudo service smbd restart
```

---

### Post by The_Woodpecker on 2016-05-15
> **bab1 said:**
> The server looks to be up.  It can see itself and all the shares.  My guess it that the usershares are not allowing the Windows user access.  You have limited Everyone to read only and the Unix User\Luke to full access.

I would try less restrictive sharing (at least temporarily).  If that doesn't work I would delete these shares and recreate them in the /etc/samba/smb.conf file.  If you add the shares to the  /etc/samba/smb.conf file, you need to reboot the server with this command```
sudo service smbd restart
```

How do I remove the shares from it?

---

### Post by bab1 on 2016-05-15
> **The_Woodpecker said:**
> How do I remove the shares from it?
The easiest way is to right click on the folder >>Properties>> Sharing and un-tick all the boxes.

---

