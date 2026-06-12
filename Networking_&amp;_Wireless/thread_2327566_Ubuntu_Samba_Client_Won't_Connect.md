---
title: "Ubuntu Samba Client Won't Connect"
date: 2016-06-12
forum: Networking &amp; Wireless
---

### Post by bmather9 on 2016-06-12
I am running a fresh install of 16.04 and have previously connected it to a samba share at my home on the LAN.  Where I currently am located I have an ASUS router with a shared folder which I am able to connect to from Windows 10, and a few Mac clients without any problems.  

When I attempt to connect from Ubuntu by clicking 'Connect to Server' and using the ip address of the router, similarly as I've done from windows, I'm prompted for a username, password, and the Domain is filled in as 'WORKGROUP'.  I have the correct username and password, but every time, I get no connection and the dialog box for username/password keeps popping up.  Any ideas?

---

### Post by bab1 on 2016-06-12
> **bmather9 said:**
> I am running a fresh install of 16.04 and have previously connected it to a samba share at my home on the LAN.  Where I currently am located I have an ASUS router with a shared folder which I am able to connect to from Windows 10, and a few Mac clients without any problems.  

When I attempt to connect from Ubuntu by clicking 'Connect to Server' and using the ip address of the router, similarly as I've done from windows, I'm prompted for a username, password, and the Domain is filled in as 'WORKGROUP'.  I have the correct username and password, but every time, I get no connection and the dialog box for username/password keeps popping up.  Any ideas?

Run this terminal command and post the contents back here```
smbtree -d3
```

Please post the text output inside [noparse]```
  
```[/noparse] blocks.  The easiest way to do that is to click on the  **[SIZE=8]#[/SIZE]** ***icon*** at the top of the advanced editor that you use to respond to the forum.

---

### Post by bmather9 on 2016-06-13
```
bmather9@bmather9-ThinkPad-W530:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface wlp3s0 ip=192.168.1.231 bcast=192.168.1.255 netmask=255.255.255.0
Enter bmather9's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.1 ( 192.168.1.1 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.1.1 at port 445
Server does not support EXTENDED_SECURITY  but 'client use spnego = yes and 'client ntlmv2 auth = yes'
WORKGROUP
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.1 ( 192.168.1.1 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.1.1 at port 445
Server does not support EXTENDED_SECURITY  but 'client use spnego = yes and 'client ntlmv2 auth = yes'
    \\RT-AC87U-0490          RT-AC87U-0490
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name RT-AC87U-0490<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name RT-AC87U-0490<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name RT-AC87U-0490<0x20>
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.1.1 at port 445
Server does not support EXTENDED_SECURITY  but 'client use spnego = yes and 'client ntlmv2 auth = yes'
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
        \\RT-AC87U-0490\IPC$               IPC Service (RT-AC87U-0490)
        \\RT-AC87U-0490\Painkillers        PNY_16GB's Painkillers in USB Flash Memory
    \\ROBSURFACE             
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name ROBSURFACE<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name ROBSURFACE<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name ROBSURFACE<0x20>
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.1.158 at port 445
E2BIG: convert_string(UTF-8,CP850): srclen=23 destlen=16 - 'BMATHER9-THINKPAD-W530'
Connecting to 192.168.1.158 at port 139
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=277)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15



```

---

### Post by bab1 on 2016-06-13
The first problem is that the Samba server embedded in the ASUS router is a very early version that does not support modern security settings.  You can see that here: ```
[COLOR="#FF0000"]Server does not support EXTENDED_SECURITY[/COLOR] but 'client use spnego = yes and 'client ntlmv2 auth = yes'
```

The client needs to **degrade** security as we can't update the asus server.  So this might work
```
client use spnego = no
client ntlmv2 auth = no
```...You might also need to add this ```
client use spnego = No
```
These need to be added to the /etc/samba/smb.conf file in the [global] section.  You need to use sudo to edit this file.

After you edit the file please post the output again of this```
 smbtree -d3
```

---

### Post by bmather9 on 2016-06-16
Thanks; adding those 2 lines to samba.conf allows me to connect.  I assume if the better security is available from other samba servers, the client will still make use of them?  Either way, thanks a ton!

---

### Post by bab1 on 2016-06-16
> **bmather9 said:**
> Thanks; adding those 2 lines to samba.conf allows me to connect.  I assume if the better security is available from other samba servers, the client will still make use of them?  Either way, thanks a ton!
No it won't be correct for other servers.  The settings you have configured are for the samba client.  The configuration will always use these deprecated settings.   If you use a updated samba server you should comment out the lines with a leading #.

For now let's mark this solved please.

---

### Post by bmather9 on 2016-06-16
> **bab1 said:**
> No it won't be correct for other servers.  The settings you have configured are for the samba client.  The configuration will always use these deprecated settings.   If you use a updated samba server you should comment out the lines with a leading #.

For now let's mark this solved please.

It seems logical that there would be a way for the client to attempt using the updated security settings, and if that fails, then revert to the deprecated settings.  I'm happy with the solution, just pointing out what seems to be a bit of a flaw in the software in my opinion.  Thanks again!

---

