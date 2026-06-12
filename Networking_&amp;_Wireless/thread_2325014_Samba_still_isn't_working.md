---
title: "Samba still isn't working"
date: 2016-05-18
forum: Networking &amp; Wireless
---

### Post by Lloydb39 on 2016-05-18
They mucked up Samba a few weeks ago. Can't they get it fixed? I still can't access my Windows 7 machine files from Ubuntu. Still asking for a password that, as far as I know, doesn't exist. Not critical, but pretty annoying to have to revert to the sneaker net.

---

### Post by bab1 on 2016-05-19
> **Lloydb39 said:**
> They mucked up Samba a few weeks ago. Can't they get it fixed? I still can't access my Windows 7 machine files from Ubuntu. Still asking for a password that, as far as I know, doesn't exist. Not critical, but pretty annoying to have to revert to the sneaker net.
The problem you are referring to has been fixed for over a week now.  Your problem is most likely something else.  What have you done to diagnose the problem?

---

### Post by Lloydb39 on 2016-05-20
Don't know what to do, but I'm open for suggestions.
Here is what I have: ```
lloyd@linux:~$ sudo lshw -C network[sudo] password for lloyd: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: c8:60:00:da:62:07
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.65 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:77 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
lloyd@linux:~$
```

---

### Post by Lloydb39 on 2016-05-20
Also this:
```
lloyd@linux:~$ smbtree -d3lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface eth0 ip=2602:306:3ba3:f480:81d0:27ab:ec09:2602 bcast= netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=2602:306:3ba3:f480:a147:a0e9:eb10:6b5b bcast= netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=2602:306:3ba3:f480:ca60:ff:feda:6207 bcast= netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.65 bcast=192.168.1.255 netmask=255.255.255.0
Enter lloyd's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.65 ( 192.168.1.65 )
Connecting to 192.168.1.65 at port 445
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
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.65 ( 192.168.1.65 )
Connecting to 192.168.1.65 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
	\\PATTI-LAPTOP   		Patti's laptop
resolve_lmhosts: Attempting lmhosts lookup for name PATTI-LAPTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PATTI-LAPTOP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PATTI-LAPTOP<0x20>
Connecting to 192.168.1.81 at port 445
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
		\\PATTI-LAPTOP\Users          	
		\\PATTI-LAPTOP\Public         	
		\\PATTI-LAPTOP\Patti          	
		\\PATTI-LAPTOP\IPC$           	Remote IPC
		\\PATTI-LAPTOP\E$             	Default share
		\\PATTI-LAPTOP\Documents      	
		\\PATTI-LAPTOP\C$             	Default share
		\\PATTI-LAPTOP\ADMIN$         	Remote Admin
	\\LLOYD-PC2010   		
resolve_lmhosts: Attempting lmhosts lookup for name LLOYD-PC2010<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name LLOYD-PC2010<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name LLOYD-PC2010<0x20>
Connecting to 192.168.1.64 at port 445
Connecting to 192.168.1.64 at port 139
	\\LINUX          		linux server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name LINUX<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name LINUX<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name LINUX<0x20>
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
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
		\\LINUX\Videos         	
		\\LINUX\Pictures       	
		\\LINUX\Documents      	
		\\LINUX\Epson-9-Pin    	XP400
		\\LINUX\IPC$           	IPC Service (linux server (Samba, Ubuntu))
		\\LINUX\print$         	Printer Drivers
lloyd@linux:~$ 



```

---

### Post by bab1 on 2016-05-20
> **Lloydb39 said:**
> Also this:
```
lloyd@linux:~$ smbtree -d3
[B]	[COLOR="#800080"]\\PATTI-LAPTOP   		Patti's laptop
		\\PATTI-LAPTOP\Users          	
		\\PATTI-LAPTOP\Public         	
		\\PATTI-LAPTOP\Patti          	
		\\PATTI-LAPTOP\IPC$           	Remote IPC
		\\PATTI-LAPTOP\E$             	Default share
		\\PATTI-LAPTOP\Documents      	
		\\PATTI-LAPTOP\C$             	Default share
		\\PATTI-LAPTOP\ADMIN$         	Remote Admin[/COLOR]
	
[COLOR="#009900"]        \\LLOYD-PC2010   		[/COLOR]

	[COLOR="#0000FF"]\\LINUX          		linux server (Samba, Ubuntu)
		\\LINUX\Videos         	
		\\LINUX\Pictures       	
		\\LINUX\Documents      	
		\\LINUX\Epson-9-Pin    	XP400
		\\LINUX\IPC$           	IPC Service (linux server (Samba, Ubuntu))
		\\LINUX\print$         	Printer Drivers[/COLOR]
lloyd@linux:~$ [/B]

```
I see 3 hosts in this network (PATTI-LAPTOP, LLOYD-PC2010 and LINUX).  Except that the host LLOYD-PC2010 shows no shares, I don't see any problems.  Which machine are we dealing with?

---

### Post by Lloydb39 on 2016-05-21
The problem is that I cannot access the Windows machines, Lloyd-PC2010 (Windows 7) and Patti-Laptop (Vista) from the Linux machine (Ubuntu 14.04), although it now works fine in reverse. Linux demands a Workgroup password, which it never has done before. I don't have a password and the Windows machines are set to not require a password. Before the Samba update I could access and exchange files between the three machines easily. (Linux and Lloyd-PC2010 are connected via Ethernet, the laptop by wireless.) Thanks for your help.

---

### Post by X-RED_Tech on 2016-05-21
The Windows users passwords have nothing to do with the network sharing settings.
And the Windows session settings also have password regardless of requiring it at start or not. Anyway it's unrelated.
And "workgroup" is the typical default "domain" name in Windows machines and mostly used for Microsoft networking. There's no password there. Users have passwords, not domains.
From the start you have been complaining about the client (Ubuntu) which, by the way, isn't "demanding" anything that isn't being "demanded" by the server (Windows) in the first place, and you're barking at the wrong tree. Again, check the settings in those Windows machines. I mean, the network sharing settings, obviously. If you must, please consult Windows specialized forums because here, you know, we deal with Ubuntu/Linux.

---

### Post by Lloydb39 on 2016-05-21
That's fine and dandy but nothing has changed in Windows since it was working, while Samba was updated and that's when the problem started. Not complaining about Ubuntu, only this particular problem, which is what I thought these forums were for. I'll try to use another word if "demanding" upsets you, but the fact is that it won't let me see the Windows files unless I give it a password.

---

### Post by X-RED_Tech on 2016-05-21
Wrong tree again...
At the same time you noticed those samba updates in Ubuntu there were a LOT of updates in Windows as well, and many directly related to networking, namely enforcing stricter rules for Windows network shares.
You would better be checking those settings at the servers (Windows) and assuring it allows guests and whatever (I'm definitely NOT an expert in Windows networking) instead of argue with me. I'm not upset with words, "demanding" or any other, I'm just trying to steer you towards a solution because I'm pretty sure you won't find any at the client's side.

---

### Post by bab1 on 2016-05-21
> **Lloydb39 said:**
> That's fine and dandy but nothing has changed in Windows since it was working, while Samba was updated and that's when the problem started. Not complaining about Ubuntu, only this particular problem, which is what I thought these forums were for. I'll try to use another word if "demanding" upsets you, but the fact is that it won't let me see the Windows files unless I give it a password.
You guys are talking past each other. The Windows Sharing machine is asking for the password.  The Ubuntu Samba Client is just responding by providing the dialog box for your user.

In any case the updates to Samba have finally eliminated share only security (file permissions).  The most basic share security is now user based. I suppose that Windows Sharing has done the same.  This means the user needs to be authenticated unless explicitly configured to allow guest (anonymous) no login access.  This is why your setup "broken" .  It means you have to reset the configuration settings on the "server side" (Windows) as the "client side" only responds to what the server will ask for.

As has been pointed out earlier there is no such thing as a "workgroup" password or a "domain" password.  The the username and password authenticate (who are you) the user and the permissions authorize (you can do that) the access to the files and directories.  As a rule of thumb on networks that have no central user management I always use the same username and password on each machine in the network.  On Linux hosts I also have the same UID/GID for the user on each machine.

I would say that you need to at least check the configuration of the Windows machine to see if it is set to accept "guest" access first.

---

