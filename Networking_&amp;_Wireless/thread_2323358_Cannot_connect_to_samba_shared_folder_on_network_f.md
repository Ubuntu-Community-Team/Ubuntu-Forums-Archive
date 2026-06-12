---
title: "Cannot connect to samba shared folder on network from 16.04"
date: 2016-05-04
forum: Networking &amp; Wireless
---

### Post by davehenson on 2016-05-04
Hello all, 

I have a fresh install of 16.04 (with Unity desktop) and can no longer log into my samba shared folders on my network. I have an asus router with an external hard drive and it uses samba to share out the folders.  Prior to about 3 weeks ago all was fine with 15.10.  There was a samba update that rolled out right before the 16.04 release and broke the samba connectivity on several versions of Ubuntu. At the time I thought it might just be on 15.10 so I did a fresh 16.04 install and still found the issue. Today there was an update ([http://www.ubuntu.com/usn/usn-2950-2/](http://www.ubuntu.com/usn/usn-2950-2/)) where it looks like to me they are back revving samba to fix the issue.  I ran update-manager and then rebooted. Still when I attempt to use the File manager to connect to my network share, I enter the username/password for the share and the window just blinks. Of note, my username for accessing the share is not a username that is on my Linux box. This has never mattered before and I don't see why it ever would but I wanted to mention it. Once I enter my smb share username, the window greys out like its connecting and after a very long time, I get a window that states "Unable to access location, Timeout was reached".

Some steps I have taken so far:

[LIST]
[*]update-manager & reboot
[*]sudo apt-get upgrade & reboot
[*]ran [COLOR=#000000]dpkg -s samba-libs and it returned the Version 2:4.3.9+dfsg-0ubuntu0.16.04.1 so I believe I am at the correct version.
[/COLOR]
[/LIST]
[COLOR=#000000]

Here is the output of 
[/COLOR]```
dpkg-query -W -f='${Package} ${Version} ${Source} ${Status}\n' | grep samba
```


> libsmbclient 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
libwbclient0 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
python-samba 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
samba-common 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
samba-common-bin 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
samba-libs 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
smbclient 2:4.3.9+dfsg-0ubuntu0.16.04.1 samba install ok installed
vlc-plugin-samba 2.2.2-5 vlc install ok installed


Please let me know of any further troubleshooting ideas or commands that might help explain this.

---

### Post by bab1 on 2016-05-04
> **davehenson said:**
> Hello all, 

I have a fresh install of 16.04 (with Unity desktop) and can no longer log into my samba shared folders on my network. I have an asus router with an external hard drive and it uses samba to share out the folders.  
Unfortunately the asus router won't have the most up to date version of Samba.  The version can be as early as Samba v2 or maybe early v3.  For sure not Samba v4 (4.3..9).  This can cause incompatibilities that are not resolvable.  Is there a command line interface?  Maybe ssh login? 
> 
Prior to about 3 weeks ago all was fine with 15.10.  There was a samba update that rolled out right before the 16.04 release and broke the samba connectivity on several versions of Ubuntu. At the time I thought it might just be on 15.10 so I did a fresh 16.04 install and still found the issue... 
I just created a share that can be accessed with no login (a so called "guest" share).  This works perfectly Linux Samba client to Linux Samba server.  I have always had working user authenticated access to the shares I create.  both of these share types (guest or authenticated) are browse able.  I have a VM with Windows running and it works also.  It is XP so I can't say that recent versions of Windows are compatible, but that would be a Windows problem, right? 
> 
Of note, my username for accessing the share is not a username that is on my Linux box. This has never mattered before and I don't see why it ever would but I wanted to mention it. Once I enter my smb share username, the window greys out like its connecting and after a very long time, I get a window that states there was a timeout.

This is one of the things that Samba needed to change as it is a security hole.  Most likely the asus version of Samba allows **security = share**.  This parameter has been deprecated for a few years now and Samba has finally removed that option.  The security has to be set to **security = user** and you should have the same user on both the server and client.  If there are multiple users then you need to set the user-group to a group that all users are members of.

Once again; do you have command line access to the asus Samba server?  Can you get a remote command line to the asus router itself?

From the Ubuntu command line what do you get from this command (use the login)```
smbtree -d3
```

---

### Post by davehenson on 2016-05-04
Thank you BAB.

Hopefully this helps. My router is a [COLOR=#6A6A6A][FONT=arial]**RT**[/FONT][/COLOR][COLOR=#545454][FONT=arial]-AC68U. Firmware 3[/FONT][/COLOR].0.0.4.380_1842-g7414eb9.  I know that doesn't say anything on its own but just in case anyone needs it. 

I can SSH into the router. Not sure what to do once there, but I'm in. :D   

As for the smbtree command, I run it on the 16.04 client and get

> 
davehenson@ubnotebook:~$ smbtree -d3 lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface wlp3s0 ip=192.168.1.121 bcast=192.168.1.255 netmask=255.255.255.0
Enter davehenson's password: 
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
[U]Server does not support EXTENDED_SECURITY  but 'client use spnego = yes and 'client ntlmv2 auth = yes'
    \\NAS                    nas[/U]
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name NAS<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name NAS<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name NAS<0x20>
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
        \\NAS\IPC$               IPC Service (nas)
        \\NAS\Spare folder        J4's Spare folder in Seagate BUP BK
        \\NAS\documents            J4's documents in Seagate BUP BK
        \\NAS\ISOS                 J4's ISOS in Seagate BUP BK
    \\JANOTEBOOK            
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name JANOTEBOOK<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name JANOTEBOOK<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name JANOTEBOOK<0x20>
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.1.185 at port 445
Connecting to 192.168.1.185 at port 139
Doing spnego session setup (blob length=320)
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
Doing spnego session setup (blob length=320)
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
davehenson@ubnotebook:~$





I did take the liberty of underlining something that I noticed in the output.  In Launchpad bug [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572876](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1572876), someone mentioned a workaround where they > [COLOR=#333333][FONT=monospace]In smb.conf [global] section put following lines:[/FONT][/COLOR][COLOR=#333333][FONT=monospace]   client use spnego = no
   client ntlmv2 auth = no
[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]   client ipc max protocol = NT1[/FONT][/COLOR]

Do you think that maybe if I update my smb.conf to state "yes" that would work?

---

### Post by bab1 on 2016-05-04
You caught the part that appears to be the problem.  You don't want to say yes to those items.  The error shows```
[COLOR="#FF0000"]Server does not support EXTENDED_SECURITY[/COLOR] but 'client use spnego = yes and 'client ntlmv2 auth = yes'
```
The client needs to **degrade** security as we can't update the asus server.  So this might work
```
client use spnego = no
client ntlmv2 auth = no
```
These need to be added to the /etc/samba/smb.conf file in the [global] section.  You need to use sudo to edit this file.

After you edit the file post the output again of this```
 smbtree -d3
```

[COLOR="#0000FF"]Edit: You might also need to add this ```
client use spnego = No
```[/COLOR]

---

### Post by davehenson on 2016-05-04
smh. that makes total sense about the security.  Frustrating that I read it but it clicked in my mind backwards. 


Bingo!  I degraded the security on the client using 
> [COLOR=#000000][FONT=Ubuntu Mono]client use spnego = no
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]client ntlmv2 auth = no[/FONT][/COLOR]

and it all works now. I can log in using any username that is defined on the router, even if that username is not on the client. 

I CANNOT thank you enough!!!!

---

### Post by bab1 on 2016-05-04
> **davehenson said:**
> smh. that makes total sense about the security.  Frustrating that I read it but it clicked in my mind backwards. 


Bingo!  I degraded the security on the client using 


and it all works now. I can log in using any username that is defined on the router, even if that username is not on the client. 

I CANNOT thank you enough!!!!

As you can see the problem is because the asus version of Samba is "baked in" and Samba itself has moved on.  ;-)

Please use the "thread tools" menu at the top of the editor to mark this thread solved.

---

