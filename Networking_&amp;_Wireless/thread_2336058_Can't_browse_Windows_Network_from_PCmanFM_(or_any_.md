---
title: "Can't browse Windows Network from PCmanFM (or any other FileManager)"
date: 2016-09-04
forum: Networking &amp; Wireless
---

### Post by Oyvind_Overby on 2016-09-04
It really beats me why such a basic task should pose any problems at all...
I've installed Ubuntu 14.4 on a server, and all I want to do is to be able to open a file manager (any file manager) from my LXDE desktop and browse into other PC's and servers on my LAN.
I tried to install Gigolo - no avail...
I tried to install gvfs-backends - no avail....
I tried to install fuse and fuse-utils - no avail....
I tried to install gvfs-fuse - no avail....
Itried to install cifs-utils - no avail...
and on and on and on....

How difficult is it actually meant to be?
The I'v searched the internet up and down, back and forth for; "How to browse a Windows Network from Ubuntu?"  - no avail....

Am I the only person on this planet with this problem?

Please help

---

### Post by Bucky Ball on 2016-09-04
> **Oyvind_Overby said:**
> 
I tried to install Gigolo - no avail...
I tried to install gvfs-backends - no avail....
I tried to install fuse and fuse-utils - no avail....
I tried to install gvfs-fuse - no avail....
Itried to install cifs-utils - no avail...


... gives us nothing we can work with. You tried to install Gigolo and ... what happened? We can't help you if you don't provide more information than 'I tried something, didn't work'. How didn't it work and what, if anything, did you do to try and fix it?

Open a terminal and ping the machine on the network you are trying to connect with? If you can't ping it you are not going to get much further before you fix that problem. Say the machine you are after has an IP of 192.168.0.3, then in a terminal:

```
ping 192.168.0.3
```

If you get 'Host unreachable' then that is your issue and waste of time going any further until the network issue is fixed. Let us know what happens.

A note: It is MUCH better to set static IP addresses on the machines you are trying to get to communicate, depending on how you are trying to get them to communicate. Gigolo should see anything on your network if you _*give it the right IP address and connection type*_ of the machine you are trying to connect to and that machine is set up to deal with whatever connection type you've chosen.

---

### Post by cmcanulty on 2016-09-04
You didn't mention installing samba which I believe gigolo needs. Also make sure the directories in windows you want to access are shared in  windows explorer

---

### Post by Oyvind_Overby on 2016-09-04
Sorry for not being precise - I guess I'm just frustrated.
Here it is:
When I run Gigolo, there is no Network icon anywhere and the Protocol list only shows "Unix Device (file)"
I can successfully ping every machine on the LAN.
I have no LAN problems at all from any other machines. All my windows machines (Win XP, 7 & 10) can see everything, including 3 Linux servers and I can  copy files using WIndows network browsing or UNC Path or Rsync. NO problems.
But this is the first time I've tried to go the other way - trying to browse the LAN from an Ubuntu 14.4 with LXDE Desktop. But all I see is a black hole.
However, if I try *smbtree -d3* my entire network including all machine names are listed.
Any assistance is appreciated.

---

### Post by cmcanulty on 2016-09-05
another thing you didn't mention going into each windows one and go to services and check all the remote settings

---

### Post by bab1 on 2016-09-05
> **Oyvind_Overby said:**
> Sorry for not being precise - I guess I'm just frustrated.
--- if I try *smbtree -d3* my entire network including all machine names are listed.
Any assistance is appreciated.
How about posting the output here?  It's impossible to diagnose these problems without the feedback.  Without that you are just guessing.

---

### Post by Bucky Ball on 2016-09-06
> When I run Gigolo, there is no Network icon anywhere and the Protocol list only shows "Unix Device (file)"

Open Gigolo, click the 'Connect' button in the toolbar, insert the IP address of the machine you are trying to connect to, try to connect. What happens? Exactly? The error message, if there is one?

As suggested previously, sounds like you may not have a lot of stuff installed you need for networking, which is why you don't have any options for the protocol. Do you have any openssh stuff installed? If you are not communicating with a Win box, and even if you are if you don't intend to use it, you do not need samba as suggested earlier. As far as I know, it is not required by Gigolo (else it would drag it in when you install Gigolo I'd say). Don't quote me on that. I avoid samba personally. From memory, it may be installed by default with Ubuntu in any case.

---

### Post by Oyvind_Overby on 2016-09-06
> **Bucky Ball said:**
> Open Gigolo, click the 'Connect' button in the toolbar, insert the IP address of the machine you are trying to connect to, try to connect. What happens? Exactly? The error message, if there is one?
The error message from Gigolo is: [B]You must enter a valid URI for the connection

[/B]If I type *smb://192.168.0.18* the error from Gigolo is: [B]Connecting to "smb://192.168.0.18/" failed - Volume doesn't implement mount
[/B]
The output from [I]smbtree -d3 :

[/I]```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (4096) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface br0 ip=192.168.0.8 bcast=192.168.0.255 netmask=255.255.255.0
added interface lxcbr0 ip=10.0.3.1 bcast=10.0.3.255 netmask=255.255.255.0
Enter GUEST's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.18 ( 192.168.0.18 )
Connecting to 192.168.0.18 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
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
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.18 ( 192.168.0.18 )
Connecting to 192.168.0.18 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
    \\T42                    
resolve_lmhosts: Attempting lmhosts lookup for name T42<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name T42<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name T42<0x20>
        \\T42\Users              
        \\T42\print$             Printer Drivers
        \\T42\IPC$               Remote IPC
        \\T42\HP OfficeJet G85 - Parallel    HP OfficeJet G85
        \\T42\C$                 Default share
        \\T42\ADMIN$             Remote Admin
    \\NASF06152              NAS Server
        \\NASF06152\Web                System default share
        \\NASF06152\Public             System default share
        \\NASF06152\homes              System default share
        \\NASF06152\Plex_Music         
        \\NASF06152\USBDisk1           USB storage share
        \\NASF06152\home               Home
        \\NASF06152\IPC$               IPC Service (NAS Server)
    \\NASE84248              NAS Server
        \\NASE84248\Multimedia         System default share
        \\NASE84248\Download           System default share
        \\NASE84248\Recordings         System default share
        \\NASE84248\Web                System default share
        \\NASE84248\Public             System default share
        \\NASE84248\homes              System default share
        \\NASE84248\home               Home
        \\NASE84248\IPC$               IPC Service (NAS Server)
    \\NAS8C7D37              NAS Server
        \\NAS8C7D37\IPC$               IPC Service (NAS Server)
        \\NAS8C7D37\home               Home
        \\NAS8C7D37\homes              System default share
        \\NAS8C7D37\Public             System default share
        \\NAS8C7D37\Web                System default share
        \\NAS8C7D37\Recordings         System default share
        \\NAS8C7D37\Download           System default share
        \\NAS8C7D37\Multimedia         System default share
    \\LENOVOX200S            
    \\DESKTOP-8JIU7H1    

```

I am a simple soul trying to migrate from windows to Linux (Debian) one step at a time. Nobody told me that even the most basic tasks were virtually impossible to achieve...  :(

---

### Post by bab1 on 2016-09-06
> **Oyvind_Overby said:**
> The error message from Gigolo is: [B]You must enter a valid URI for the connection

[/B]If I type *smb://192.168.0.18* the error from Gigolo is: [B]Connecting to "smb://192.168.0.18/" failed - Volume doesn't implement mount
[/B] 
Both messages say basically the same thing.  The URI is incomplete.  The format is *smb://ip address/share_name*.> 
The output from [I]smbtree -d3: 

[/I]```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (4096) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface br0 ip=192.168.0.8 bcast=192.168.0.255 netmask=255.255.255.0
added interface lxcbr0 ip=10.0.3.1 bcast=10.0.3.255 netmask=255.255.255.0
Enter GUEST's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.18 ( 192.168.0.18 )
Connecting to 192.168.0.18 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
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
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.18 ( 192.168.0.18 )
Connecting to 192.168.0.18 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
    \\T42                    
resolve_lmhosts: Attempting lmhosts lookup for name T42<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name T42<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name T42<0x20>
        \\T42\Users              
        \\T42\print$             Printer Drivers
        \\T42\IPC$               Remote IPC
        \\T42\HP OfficeJet G85 - Parallel    HP OfficeJet G85
        \\T42\C$                 Default share
        \\T42\ADMIN$             Remote Admin
 
[COLOR="#FF0000"]## Where are the logins for the //server/share listings below?[/COLOR]
   \\NASF06152              NAS Server
        \\NASF06152\Web                System default share
        \\NASF06152\Public             System default share
        \\NASF06152\homes              System default share
        \\NASF06152\Plex_Music         
        \\NASF06152\USBDisk1           USB storage share
        \\NASF06152\home               Home
        \\NASF06152\IPC$               IPC Service (NAS Server)
    \\NASE84248              NAS Server
        \\NASE84248\Multimedia         System default share
        \\NASE84248\Download           System default share
        \\NASE84248\Recordings         System default share
        \\NASE84248\Web                System default share
        \\NASE84248\Public             System default share
        \\NASE84248\homes              System default share
        \\NASE84248\home               Home
        \\NASE84248\IPC$               IPC Service (NAS Server)
    \\NAS8C7D37              NAS Server
        \\NAS8C7D37\IPC$               IPC Service (NAS Server)
        \\NAS8C7D37\home               Home
        \\NAS8C7D37\homes              System default share
        \\NAS8C7D37\Public             System default share
        \\NAS8C7D37\Web                System default share
        \\NAS8C7D37\Recordings         System default share
        \\NAS8C7D37\Download           System default share
        \\NAS8C7D37\Multimedia         System default share
    \\LENOVOX200S            
    \\DESKTOP-8JIU7H1    

```

The above is missing information (see my comment in red).  Post the output of *smbtree -**d4*** for increased debug info. 
> 

I am a simple soul trying to migrate from windows to Linux (Debian) one step at a time. Nobody told me that even the most basic tasks were virtually impossible to achieve...  :(
Who was supposed to tell you about how Linux works?  It's pretty well known that Windows hides the ugly underpinnings while Linux is there for you to configure any way you wish.  

What are the bridged interfaces for?  Are your Samba servers virtual?  SMB/CIFS does not work like some TCP/IP tools such as ICMP.  The ability to ping the various hosts is nice, but it does not tell the whole story.

---

### Post by Oyvind_Overby on 2016-09-06
> **bab1 said:**
> Both messages say basically the same thing.  The URI is incomplete.  The format is *smb://ip address/share_name*.
I tried *smb://192.168.0.18/Users *but the error message was the same.

> **bab1 said:**
> The above is missing information (see my comment in red).  Post the output of *smbtree -**d4*** for increased debug info.
I do not understand what you mean by that red comment, but for now, neglect all the servers below. They are three Linux servers and two Win 10 PC's I do not need to reach those right now.

> **bab1 said:**
> What are the bridged interfaces for?  Are your Samba servers virtual?
The bridges interface is because this server runs in a container, but in host mode.

Here's the output from [I]smbtree -d4:
[/I]
```
lp_load_ex: refreshing parametersInitialising global parameters
rlimit_max: increasing rlimit_max (4096) to minimum Windows limit (16384)
Processing section "[global]"
doing parameter workgroup = WORKGROUP
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
WARNING: The "syslog" option is deprecated
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter server role = standalone server
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
pm_process() returned Yes
added interface br0 ip=192.168.0.8 bcast=192.168.0.255 netmask=255.255.255.0
added interface lxcbr0 ip=10.0.3.1 bcast=10.0.3.255 netmask=255.255.255.0
Enter GUEST's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
nmb packet from 192.168.0.15(35072) header: id=13835 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WORKGROUP<1d> rr_type=32 rr_class=1 ttl=300000
    answers   0 char ......   hex 0000C0A8000F
Got a positive name query response from 192.168.0.15 ( 192.168.0.15 )
Connecting to 192.168.0.15 at port 445
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
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
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_TARGET_TYPE_SERVER
  NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Account disabled
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_TARGET_TYPE_SERVER
  NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_ANONYMOUS
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_ANONYMOUS
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_ANONYMOUS
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
nmb packet from 192.168.0.15(35072) header: id=17566 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WORKGROUP<1d> rr_type=32 rr_class=1 ttl=300000
    answers   0 char ......   hex 0000C0A8000F
Got a positive name query response from 192.168.0.15 ( 192.168.0.15 )
Connecting to 192.168.0.15 at port 445
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_TARGET_TYPE_SERVER
  NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Account disabled
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_TARGET_TYPE_SERVER
  NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_ANONYMOUS
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_ANONYMOUS
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_ANONYMOUS
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
    \\T42                    
resolve_lmhosts: Attempting lmhosts lookup for name T42<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name T42<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name T42<0x20>
        \\T42\Users              
        \\T42\print$             Printer Drivers
        \\T42\IPC$               Remote IPC
        \\T42\HP OfficeJet G85 - Parallel    HP OfficeJet G85
        \\T42\C$                 Default share
        \\T42\ADMIN$             Remote Admin
    \\NASF06152              NAS Server
        \\NASF06152\Web                System default share
        \\NASF06152\Public             System default share
        \\NASF06152\homes              System default share
        \\NASF06152\Plex_Music         
        \\NASF06152\USBDisk1           USB storage share
        \\NASF06152\home               Home
        \\NASF06152\IPC$               IPC Service (NAS Server)
    \\NASE84248              NAS Server
        \\NASE84248\Multimedia         System default share
        \\NASE84248\Download           System default share
        \\NASE84248\Recordings         System default share
        \\NASE84248\Web                System default share
        \\NASE84248\Public             System default share
        \\NASE84248\homes              System default share
        \\NASE84248\home               Home
        \\NASE84248\IPC$               IPC Service (NAS Server)
    \\NAS8C7D37              NAS Server
        \\NAS8C7D37\IPC$               IPC Service (NAS Server)
        \\NAS8C7D37\home               Home
        \\NAS8C7D37\homes              System default share
        \\NAS8C7D37\Public             System default share
        \\NAS8C7D37\Web                System default share
        \\NAS8C7D37\Recordings         System default share
        \\NAS8C7D37\Download           System default share
        \\NAS8C7D37\Multimedia         System default share
    \\LENOVOX200S            
    \\DESKTOP-8JIU7H1    
```

---

### Post by bab1 on 2016-09-06
Let's simplify this.  What are the host names and IP addresses of the client and server you are working with? Identify the server for us.

---

### Post by Oyvind_Overby on 2016-09-07
> **bab1 said:**
> Let's simplify this.  What are the host names and IP addresses of the client and server you are working with? Identify the server for us.
Ubuntu is running on: [COLOR=#000000][FONT=&quot]NASF06152 with IP 192.168.0.8[/FONT][/COLOR]
From this Server I am trying to browse my LAN using Gigolo (But I'm happy to use any other file manager suggested).

As a start, I'm trying to reach: [COLOR=#000000][FONT=&quot] smb://T42/User with IP 192.168.0.18

[/FONT][/COLOR]Going the other way works just fine. From T42 (which a Windows 7 PC), I can open network neighborhood and browse all shares on NASF06152

---

### Post by bab1 on 2016-09-09
> **Oyvind_Overby said:**
> Ubuntu is running on: [COLOR=#000000][FONT=&quot]NASF06152 with IP 192.168.0.8[/FONT][/COLOR]
From this Server I am trying to browse my LAN using Gigolo (But I'm happy to use any other file manager suggested).

As a start, I'm trying to reach: [COLOR=#000000][FONT=&quot] smb://T42/User with IP 192.168.0.18

[/FONT][/COLOR]Going the other way works just fine. From T42 (which a Windows 7 PC), I can open network neighborhood and browse all shares on NASF06152

Sorry for the delay, sometimes life takes me elsewhere.

It's helpfull to undertand that a Samba server and a Samba client can live on the same host.  The problem you have has to do with Samba's client side or the Windows Share server not listening for the Samba client requests.

So, from the host NASF06152 post the output of this command ```
smbclient -d3 -L T42 
```  This should show the information for just the Windows SMB server (and all the relevent diagnostic info.

Please also list the output of these commands from the host NASF06152
```

cat /etc/hosts

cat /etc/samba/smb.conf

sudo pdbedit -L


```

---

### Post by Oyvind_Overby on 2016-09-10
> **bab1 said:**
> So, from the host NASF06152 post the output of this command ```
smbclient -d3 -L T42 
``` 
Here it is:
```
lp_load_ex: refreshing parametersInitialising global parameters
rlimit_max: increasing rlimit_max (4096) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface br0 ip=192.168.0.8 bcast=192.168.0.255 netmask=255.255.255.0
added interface lxcbr0 ip=10.0.3.1 bcast=10.0.3.255 netmask=255.255.255.0
Client started (version 4.3.9-Ubuntu).
Enter GUEST's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name T42<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name T42<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name T42<0x20>
Domain=[T42] OS=[Windows 7 Ultimate 7601 Service Pack 1] Server=[Windows 7 Ultimate 6.1]


    Sharename       Type      Comment
    ---------       ----      -------
    ADMIN$          Disk      Remote Admin
    C$              Disk      Default share
    HP OfficeJet G85 - Parallel Printer   HP OfficeJet G85
    IPC$            IPC       Remote IPC
    print$          Disk      Printer Drivers
    Users           Disk      
Domain=[T42] OS=[Windows 7 Ultimate 7601 Service Pack 1] Server=[Windows 7 Ultimate 6.1]


    Server               Comment
    ---------            -------


    Workgroup            Master
    ---------            -------

```

> **bab1 said:**
> Please also list the output of these commands from the host NASF06152
```

cat /etc/hosts

cat /etc/samba/smb.conf

sudo pdbedit -L


```

And here:
```
127.0.0.1  localhost  localhost192.168.0.8  NASF06152  NASF06152
10.0.3.1  NASF06152  NASF06152
```

```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 


#======================= Global Settings =======================


[global]


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP


# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no


#### Networking ####


# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0


# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes






#### Debugging/Accounting ####


# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m


# Cap the size of the individual log files (in KiB).
   max log size = 1000


# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no


# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0


# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d




####### Authentication #######


# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam


   obey pam restrictions = yes


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes


# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes


# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user


########## Domains ###########


#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#


# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile


# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U


# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd


# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u


# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u


# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g


############ Misc ############


# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m


# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


# Setup usershare options to enable non-root users to share folders
# with the net usershare command.


# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes


#======================= Share Definitions =======================


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes


# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700


# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700


# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S


# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes


# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin
```

```
sudo pdbedit -L
``` did'n't do anything..... (?)

---

### Post by bab1 on 2016-09-14
> **Oyvind_Overby said:**
> Here it is:
```
lp_load_ex: refreshing parametersInitialising global parameters
rlimit_max: increasing rlimit_max (4096) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface br0 ip=192.168.0.8 bcast=192.168.0.255 netmask=255.255.255.0
added interface lxcbr0 ip=10.0.3.1 bcast=10.0.3.255 netmask=255.255.255.0
Client started (version 4.3.9-Ubuntu).
Enter GUEST's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name T42<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name T42<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name T42<0x20>
Domain=[T42] OS=[Windows 7 Ultimate 7601 Service Pack 1] Server=[Windows 7 Ultimate 6.1]


    Sharename       Type      Comment
    ---------       ----      -------
    ADMIN$          Disk      Remote Admin
    C$              Disk      Default share
    HP OfficeJet G85 - Parallel Printer   HP OfficeJet G85
    IPC$            IPC       Remote IPC
    print$          Disk      Printer Drivers
    Users           Disk      
Domain=[T42] OS=[Windows 7 Ultimate 7601 Service Pack 1] Server=[Windows 7 Ultimate 6.1]


    Server               Comment
    ---------            -------


    Workgroup            Master
    ---------            -------

```
This shows that the basic Samba client is working.> 


And here:
```
127.0.0.1  localhost  localhost
192.168.0.8  NASF06152  NASF06152
10.0.3.1  NASF06152  NASF06152
```
This doesn't look correct. Why map the hostname to multiple IP addresses?> 

```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 


#======================= Global Settings =======================


[global]


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP


# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no


#### Networking ####


# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0


# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes






#### Debugging/Accounting ####


# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m


# Cap the size of the individual log files (in KiB).
   max log size = 1000


# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no


# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0


# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d




####### Authentication #######


# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam


   obey pam restrictions = yes


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes


# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes


# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user


########## Domains ###########


#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#


# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile


# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U


# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd


# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u


# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u


# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g


############ Misc ############


# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m


# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


# Setup usershare options to enable non-root users to share folders
# with the net usershare command.


# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes


#======================= Share Definitions =======================


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes


# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700


# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700


# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S


# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes


# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin
```

This looks good.> 

```
sudo pdbedit -L
``` did'n't do anything..... (?)
You should add the network users to this data base (using smbpasswd -a <username>).  The Linux user and Samba user should match the Windows usernames.  The default guest user for Samba is the user "nobody". Windows doesn't recognize this user.

---

### Post by Oyvind_Overby on 2016-09-14
First of all, let me thank you so much for taking the time :KS
> **bab1 said:**
> ```

[COLOR=#000000][FONT=&amp]127.0.0.1  localhost  localhost
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]192.168.0.8  NASF06152  NASF06152 [/FONT][/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]10.0.3.1  NASF06152  NASF06152
[/FONT][/COLOR]
```This doesn't look correct. Why map the hostname to multiple IP addresses?
I guess localhost is ok.
192.168.0.8 is the physical IP of the NAS on my LAN
10.0.3.1 is the logical IP of the container inside Docker, and not visible from the LAN.

That's all I know.

> **bab1 said:**
> You should add the network users to this data base (using smbpasswd -a <username>).  The Linux user and Samba user should match the Windows usernames.  The default guest user for Samba is the user "nobody". Windows doesn't recognize this user.
```
$ sudo smbpasswd -a Bestefar
New SMB password:
Retype new SMB password:
Failed to add entry for user Bestefar.

```
(?) beats me.... !

---

### Post by bab1 on 2016-09-14
Beats me too.  :-(

Docker containers have their limitations.  This looks like one of those situations.  I suggest you learn Samba on a host before you attempt to run it in a LXC style container.  The command smbpasswd is essential for the correct operation of the latest versions of Samba.

Unless you are using FQDN naming such as _name.domain.tld_ you only need the hostname alone.  Example ```
127.0.0.1. localhost.domain.com. localhost
192.168.0.1. nas.domain.com. nas
```

The bridge IP address is all you need to connect to the container.

---

### Post by Morbius1 on 2016-09-16
I am honestly and truly sorry for the interruption but based on your description of Gigolo alone I have to ask a question: Are you running as root?

If I run gigolo as root I can verify the symptoms you posted above:

There is no "Network" tab or icon.
If I try to connect explicitly to a Win10 share I will get the "Volume does not implement mount" error message.

If I try to run pcmanfm as root there is no "Network" there either and if I try to access a share explicitly I will get an "Operation not permitted"

There's a reason for both results. Run PCManFM or Gigolo as a regular user and see if you have the same problem.

---

### Post by Oyvind_Overby on 2016-09-21
> **Morbius1 said:**
> I have to ask a question: Are you running as root?
Run PCManFM or Gigolo as a regular user and see if you have the same problem.
My UID=1000 so I guess I'm not running as root.

I have tried all possible ways to mount a share on a Windows PC (both Win7 and Win10) using both *sudo mount *and *mount.cifs* but to no avail.  It always returns **permission denied**
I've tried using the guest account as well as the administrator account on both windows PC's - but the result is always the same.

I'm beginning to wonder if it is at all possible to "reach out" from a container?

---

### Post by bab1 on 2016-09-21
> **Oyvind_Overby said:**
> My UID=1000 so I guess I'm not running as root.

I have tried all possible ways to mount a share on a Windows PC (both Win7 and Win10) using both *sudo mount *and *mount.cifs* but to no avail.  It always returns **permission denied**
I've tried using the guest account as well as the administrator account on both windows PC's - but the result is always the same.

I'm beginning to wonder if it is at all possible to "reach out" from a container?
Have you tried to view the packet flow in and out of the container?  Do you know what the capabilities of the container are?  LXC by default sets up a bridge that is not capable of communicating outside of a LAN. You can use Wireshark to inspect the packet flows in and out of the container to see this. 

My guess is the container won't allow you to do what you want with the current LXC configuration.

---

