---
title: "Samba on Ubuntu 13.10"
date: 2014-03-30
forum: Networking &amp; Wireless
---

### Post by ray_silva on 2014-03-30
Just recently installed Saucy Salamander on Pentium(R) Dual-Core CPU E5300 @ 2.60GHz × 2.
It's 32 bit with 2 Gig Ram.

I wanted to share files with my Windows 7 workgroup on my home network.

So, I installed Samba Server.

Now, here's the curious thing. From the Ubuntu machine I can browse the network. I cannot retrieve the share list from the Windows Workgroup that shows on the network in the Ubuntu machine, but the actual Windows 7 machines also show on the network and I CAN open them, provide the login passwords and get the shared files on the Windows machines. My first question and puzzlement is why can I get at the files that way but not able to retrieve the shares through the workgroup? But I have a more serious problem.

Although somehow Samba is connecting my Ubuntu machine with the Windows computers on the Windows network, although I have shared folders on the the Ubuntu machine it refuses connection through the Ubuntu network folder to itself. And, none of my Windows machines can see the Ubuntu machine on the network at all.

I saw something about using the Ubuntu machine's IP address from Windows 7 Search (//IP address), but that doesn't work at all. I've tried rebooting in various sequences, but nothing seems to work. All my Windows computers are seeing each other on the Windows workgroup without any problem. But none of at hem can see the Samba running Ubuntu machine. I've been battling with this all day with no success.

Someone please help.

---

### Post by ray_silva on 2014-04-01
Continued piddling...Windows 7 network computers show the name of the Ubuntu computer in their network but when I click on the name they cannot "find" the path??? I find it strange that Ubuntu computer (when I browse the network) sees itself and only one Windows computer plus the Windows Network. Clicking on the Windows Network shows the Windows Homegroup. And, clicking on that shows all the Windows networked computers AND the Ubuntu one. I can drill down into the Windows computers but trying to open the Ubuntu one (from the Ubuntu computer) immediately returns "Unable to access location. Failed to retrieve share list from server: connection timed out." Of course Samba is running - how else would I be able to reach the Windows networked computers?

Help, please.

---

### Post by bab1 on 2014-04-01
> **ray_silva said:**
> Continued piddling...Windows 7 network computers show the name of the Ubuntu computer in their network but when I click on the name they cannot "find" the path??? I find it strange that Ubuntu computer (when I browse the network) sees itself and only one Windows computer plus the Windows Network. Clicking on the Windows Network shows the Windows Homegroup. And, clicking on that shows all the Windows networked computers AND the Ubuntu one. I can drill down into the Windows computers but trying to open the Ubuntu one (from the Ubuntu computer) immediately returns "Unable to access location. Failed to retrieve share list from server: connection timed out." Of course Samba is running - how else would I be able to reach the Windows networked computers?

Help, please.

From the Ubuntu command line, post the output of these commands```
pgrep -l mbd

smbtree -d3
```

---

### Post by ray_silva on 2014-04-02
pgrep:
1602 nmbd
19570 smbd

smbtree:
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
WARNING: The "null passwords" option is deprecated
added interface ham0 ip=2620:9b::190c:bd2e bcast=2620:9b::ffff:ffff netmask=ffff:ffff:ffff:ffff:ffff:ffff::
added interface wlan0 ip=fe80::208:54ff:fe8d:99f%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface ham0 ip=fe80::7879:19ff:fe0c:bd2e%ham0 bcast=fe80::ffff:ffff:ffff:ffff%ham0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.0.194 bcast=192.168.0.255 netmask=255.255.255.0
added interface ham0 ip=25.12.189.46 bcast=25.255.255.255 netmask=255.0.0.0
Enter ray's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.199 ( 192.168.0.199 )
Connecting to host=192.168.0.199
Connecting to 192.168.0.199 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.0.199 ( 192.168.0.199 )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.199 ( 192.168.0.199 )
Connecting to host=192.168.0.199
Connecting to 192.168.0.199 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.199 ( 192.168.0.199 )
Connecting to host=192.168.0.199
Connecting to 192.168.0.199 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
	\\RAY2-PC        		
Connecting to host=RAY2-PC
resolve_lmhosts: Attempting lmhosts lookup for name RAY2-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name RAY2-PC<0x20>
resolve_wins: Attempting wins lookup for name RAY2-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name RAY2-PC<0x20>
resolve_hosts: getaddrinfo failed for name RAY2-PC [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name RAY2-PC<0x20>
Got a positive name query response from 192.168.0.199 ( 192.168.0.199 )
Connecting to 192.168.0.199 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
	\\RAY-PC         		Desktop Windows 7 PC
Connecting to host=RAY-PC
resolve_lmhosts: Attempting lmhosts lookup for name RAY-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name RAY-PC<0x20>
resolve_wins: Attempting wins lookup for name RAY-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name RAY-PC<0x20>
resolve_hosts: getaddrinfo failed for name RAY-PC [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name RAY-PC<0x20>
cli_start_connection: failed to connect to RAY-PC<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\RAY-HP         		
Connecting to host=RAY-HP
resolve_lmhosts: Attempting lmhosts lookup for name RAY-HP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name RAY-HP<0x20>
resolve_wins: Attempting wins lookup for name RAY-HP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name RAY-HP<0x20>
resolve_hosts: getaddrinfo failed for name RAY-HP [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name RAY-HP<0x20>
cli_start_connection: failed to connect to RAY-HP<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\RAY-DESKTOP    		ray-desktop server (Samba, Ubuntu)
Connecting to host=RAY-DESKTOP
resolve_lmhosts: Attempting lmhosts lookup for name RAY-DESKTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name RAY-DESKTOP<0x20>
resolve_wins: Attempting wins lookup for name RAY-DESKTOP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name RAY-DESKTOP<0x20>
Connecting to 192.168.0.194 at port 445
Connecting to 192.168.0.194 at port 139
Error connecting to 192.168.0.194 (Connection refused)
cli_start_connection: failed to connect to RAY-DESKTOP<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
	\\BRW0022581B28B8		
Connecting to host=BRW0022581B28B8
resolve_lmhosts: Attempting lmhosts lookup for name BRW0022581B28B8<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name BRW0022581B28B8<0x20>
resolve_wins: Attempting wins lookup for name BRW0022581B28B8<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name BRW0022581B28B8<0x20>
resolve_hosts: getaddrinfo failed for name BRW0022581B28B8 [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name BRW0022581B28B8<0x20>
Got a positive name query response from 192.168.0.190 ( 192.168.0.190 )
Connecting to 192.168.0.190 at port 445
Connecting to 192.168.0.190 at port 139
Error connecting to 192.168.0.190 (Connection refused)
cli_start_connection: failed to connect to BRW0022581B28B8<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED

BTW, the BRW...is my cellphone
I just checked: all the computers on the Windows WORKGROUP network see each other and can access each other's files.
I can kind of see that only the Ubuntu computer "ray-desktop" and the one Windows 7 computer "Ray2-PC" are seeing each other.
Still, not even that one is able to see files in Ubuntu "ray-desktop." The Ubuntu machine can't see itself on the network even though its name shows up when you browse the network. But it can browse to all the Windows computers and access their shared files without any problem.

---

### Post by bab1 on 2014-04-02
> **ray_silva said:**
> pgrep:
```
1602 nmbd
19570 smbd

```

This doesn't look right.  There should be a minimum 2 smbd daemons running and 1 nmbd daemon running.  Also the PID of 19570 is pretty high.  It indicates to me that the daemon has been restarted many times.  On my machine it looks like this```
pgrep -l mbd
887 smbd
896 nmbd
898 smbd

```
> 
smbtree:
```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
[COLOR="#800080"]**WARNING: The "null passwords" option is deprecated**[/COLOR]
added interface ham0 ip=2620:9b::190c:bd2e bcast=2620:9b::ffff:ffff netmask=ffff:ffff:ffff:ffff:ffff:ffff::
added interface wlan0 ip=fe80::208:54ff:fe8d:99f%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface ham0 ip=fe80::7879:19ff:fe0c:bd2e%ham0 bcast=fe80::ffff:ffff:ffff:ffff%ham0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.0.194 bcast=192.168.0.255 netmask=255.255.255.0
added interface ham0 ip=25.12.189.46 bcast=25.255.255.255 netmask=255.0.0.0
Enter ray's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.199 ( 192.168.0.199 )
Connecting to host=192.168.0.199
Connecting to 192.168.0.199 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
[COLOR="#FF0000"]SPNEGO login failed: Logon failure
[/COLOR]name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.0.199 ( 192.168.0.199 )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.199 ( 192.168.0.199 )
Connecting to host=192.168.0.199
Connecting to 192.168.0.199 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
[COLOR="#FF0000"]SPNEGO login failed: Logon failure[/COLOR]
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.199 ( 192.168.0.199 )
Connecting to host=192.168.0.199
Connecting to 192.168.0.199 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
[COLOR="#FF0000"]SPNEGO login failed: Logon failure[/COLOR]
	\\RAY2-PC        		
Connecting to host=RAY2-PC
resolve_lmhosts: Attempting lmhosts lookup for name RAY2-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name RAY2-PC<0x20>
resolve_wins: Attempting wins lookup for name RAY2-PC<0x20>
[COLOR="#FF0000"]resolve_wins: WINS server resolution selected and no WINS servers listed.[/COLOR]
resolve_hosts: Attempting host lookup for name RAY2-PC<0x20>
[COLOR="#FF0000"]resolve_hosts: getaddrinfo failed for name RAY2-PC [Name or service not known][/COLOR]
name_resolve_bcast: Attempting broadcast lookup for name RAY2-PC<0x20>
Got a positive name query response from 192.168.0.199 ( 192.168.0.199 )
Connecting to 192.168.0.199 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
[COLOR="#FF0000"]SPNEGO login failed: Logon failure[/COLOR]
	\\RAY-PC         		Desktop Windows 7 PC
Connecting to host=RAY-PC
resolve_lmhosts: Attempting lmhosts lookup for name RAY-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name RAY-PC<0x20>
resolve_wins: Attempting wins lookup for name RAY-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name RAY-PC<0x20>
resolve_hosts: getaddrinfo failed for name RAY-PC [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name RAY-PC<0x20>
cli_start_connection: failed to connect to RAY-PC<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\RAY-HP         		
Connecting to host=RAY-HP
resolve_lmhosts: Attempting lmhosts lookup for name RAY-HP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name RAY-HP<0x20>
resolve_wins: Attempting wins lookup for name RAY-HP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name RAY-HP<0x20>
resolve_hosts: getaddrinfo failed for name RAY-HP [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name RAY-HP<0x20>
cli_start_connection: failed to connect to RAY-HP<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\RAY-DESKTOP    		ray-desktop server (Samba, Ubuntu)
Connecting to host=RAY-DESKTOP
resolve_lmhosts: Attempting lmhosts lookup for name RAY-DESKTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name RAY-DESKTOP<0x20>
resolve_wins: Attempting wins lookup for name RAY-DESKTOP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name RAY-DESKTOP<0x20>
Connecting to 192.168.0.194 at port 445
Connecting to 192.168.0.194 at port 139
[COLOR="#FF0000"]Error connecting to 192.168.0.194 (Connection refused)
cli_start_connection: failed to connect to RAY-DESKTOP<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED[/COLOR]
	\\BRW0022581B28B8		
Connecting to host=BRW0022581B28B8
resolve_lmhosts: Attempting lmhosts lookup for name BRW0022581B28B8<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name BRW0022581B28B8<0x20>
resolve_wins: Attempting wins lookup for name BRW0022581B28B8<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name BRW0022581B28B8<0x20>
[COLOR="#FF0000"]resolve_hosts: getaddrinfo failed for name BRW0022581B28B8 [Name or service not known][/COLOR]
name_resolve_bcast: Attempting broadcast lookup for name BRW0022581B28B8<0x20>
Got a positive name query response from 192.168.0.190 ( 192.168.0.190 )
Connecting to 192.168.0.190 at port 445
Connecting to 192.168.0.190 at port 139
Error connecting to 192.168.0.190 (Connection refused)
[COLOR="#FF0000"]cli_start_connection: failed to connect to BRW0022581B28B8<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED[/COLOR]

```
[QUOTE]BTW, the BRW...is my cellphone
I just checked: all the computers on the Windows WORKGROUP network see each other and can access each other's files.
I can kind of see that only the Ubuntu computer "ray-desktop" and the one Windows 7 computer "Ray2-PC" are seeing each other.
Still, not even that one is able to see files in Ubuntu "ray-desktop." The Ubuntu machine can't see itself on the network even though its name shows up when you browse the network. But it can browse to all the Windows computers and access their shared files without any problem.[/QUOTE]

I almost missed your response at the bottom.  You should put the data output between ```
 blocks so it is legible and separated from your comments..  you can do that by clicking on the [SIZE=4]**#**[/SIZE] icon at the top of the editor (advanced mode).  Look for the red highlights in the above.  These are login failures and one name not not known.

In addition you have used a deprecated parameter (see the purple highlight) in configuring the smb,conf file.  This must mean that you have modified the smb.conf [global] configuration section.

Post the output of these commands; using the [code] blocks ([SIZE=3]#[/SIZE][CODE]
sudo pdbedit -L

getent passwd |grep 1000

cat /etc/samba/smb.conf

```
I'm looking to see if the Ubuntu user is also a Samba user.  Every Samba user (including the guest user) must be in the Samba user database as well as being an Ubuntu user.  It's best of the Windows user name is the same as the Ubuntu and Samba user name.

The default smb.conf file should work perfectly.  The only addition needed is the share definitions.  So I want to see what you have modified.

The output shows that not all the hostnames are recognized.  Let's see the /etc/hosts file for the Ubuntu machine we are testing.  We should stick with one and then g t the second Ubuntu machine later.  Post the output of these```

hostname

cat /etc/hosts
```

---

### Post by ray_silva on 2014-04-04
First, RE: 
[COLOR=#000000]This doesn't look right. There should be a minimum 2 smbd daemons running and 1 nmbd daemon running. Also the PID of 19570 is pretty high. It indicates to me that the daemon has been restarted many times. On my machine it looks like this[/COLOR][COLOR=#000000]Code:
pgrep -l mbd
887 smbd
896 nmbd
898 smbd[/COLOR]
You're right, I did re-start it many times trying to get it to work. At no point did I have two smdb daemons running.

I'll reply to each of your comments in individual "quick replies."

---

### Post by ray_silva on 2014-04-04
Second, RE:

[COLOR=#000000]Look for the red highlights in the above. These are login failures and one name not not known.[/COLOR]

[COLOR=#000000]In addition you have used a deprecated parameter (see the purple highlight) in configuring the smb,conf file. This must mean that you have modified the smb.conf [global] configuration section.

You're right. The red highlights must be for the other Windows computers on the network, but remember this - the Ubuntu machine running Samba is having no problem browsing the Windows server and accessing files from all the Windows networked computers. Recall also that I mentioned the BRW... attempted connect is my cell phone. I would not be surprised that Samba does not know or connect to it since it has a hotspot shiled VPN.

About the purple highlighted "depracation;" yes, I did try to edit the config file, both from Webmin and directly. I did have problems because it was read-only and I figured a way to edit and replace the old one, but that must have caused the depracation error.
[/COLOR]

---

### Post by ray_silva on 2014-04-04
ray@ray-desktop:~$ sudo pdbedit -L
[sudo] password for ray: 

WARNING: The "null passwords" option is deprecated
No builtin backend found, trying to load plugin
Error loading module '/usr/lib/samba/pdb/xxxxxxx.so': /usr/lib/samba/pdb/xxxxxxx.so: cannot open shared object file: No such file or directory
No builtin nor plugin backend for xxxxxxx found
PANIC (pid 5975): pdb_get_methods_reload: failed to get pdb methods for backend xxxxxxx


BACKTRACE: 7 stack frames:
 #0 pdbedit(log_stack_trace+0x29) [0xb77081b9]
 #1 pdbedit(smb_panic+0x28) [0xb77082b8]
 #2 pdbedit(+0x5faa3) [0xb7692aa3]
 #3 pdbedit(initialize_password_db+0x23) [0xb7695913]
 #4 pdbedit(main+0x33f) [0xb7669c0f]
 #5 /lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf5) [0xb7388905]
 #6 pdbedit(+0x390d5) [0xb766c0d5]
smb_panic(): calling panic action [/usr/share/samba/panic-action 5975]
smb_panic(): action returned status 0
Can not dump core: corepath not set up
Please install an MTA on this system if you want to use sendmail!

COMMENT -- I changed the actual password in the results to xxxxxxx

---

### Post by ray_silva on 2014-04-04
ray@ray-desktop:~$ getent passwd |grep 1000
ray:x:1000:1000:ray,,,:/home/ray:/bin/bash

---

### Post by ray_silva on 2014-04-04
ray@ray-desktop:~$ cat /etc/samba/smb.conf
[global]
panic action = /usr/share/samba/panic-action %d
workgroup = WORKGROUP
netbios name = silvanet
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3 
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = xxxxxxx
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no


#Share Definitions


[homes]
        comment = Home Directories
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700


COMMENT - Again, I changed the actual password in the results above to xxxxxxx

---

### Post by ray_silva on 2014-04-04
ray@ray-desktop:~$ hostname
ray-desktop
 
ray@ray-desktop:~$ cat /etc/hosts
127.0.0.1	localhost
192.168.0.194	ray-desktop


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by ray_silva on 2014-04-04
By the way...

[COLOR=#000000]We should stick with one and then g t the second Ubuntu machine later.

There is no second Ubuntu machine - only one.

[/COLOR]

---

### Post by ray_silva on 2014-04-04
I thank you so much for taking the time to help me on this. I really appreciate it.

---

### Post by bab1 on 2014-04-04
There is no need to separate all of this out into individual posts.  More importantly though.  You should put the data output between [code] blocks so it is legible and separated from your comments.. [SIZE=4][COLOR="#FF0000"]you can do that by clicking on the [COLOR="#000000"]#[/COLOR] icon at the top of the editor (advanced mode)[/COLOR][/SIZE].

---

### Post by bab1 on 2014-04-04
> **ray_silva said:**
> Second, RE:

> Look for the red highlights in the above. These are login failures and one name not not known.  In addition you have used a deprecated parameter (see the purple highlight) in configuring the smb,conf file. This must mean that you have modified the smb.conf [global] configuration section.

You're right. The red highlights must be for the other Windows computers on the network, but remember this - the Ubuntu machine running Samba is having no problem browsing the Windows server and accessing files from all the Windows networked computers. Recall also that I mentioned the BRW... attempted connect is my cell phone. I would not be surprised that Samba does not know or connect to it since it has a hotspot shiled VPN.

Samba is a Client/Server application.  The Samba client is fully capable of requesting information from the Windows share servers (yes there is a smb/cifs server built into ever Window host).  So the Windows machines showing up when browsing with Ubuntu is not unusual. 
> 
About the purple highlighted "deprecation;" yes, I did try to edit the config file, both from Webmin and directly. I did have problems because it was read-only and I figured a way to edit and replace the old one, but that must have caused the deprecation error.

The files require you to use sudo (become root) to edit them.
> 
```
ray@ray-desktop:~$ sudo pdbedit -L
[sudo] password for ray:

WARNING: The "null passwords" option is deprecated
No builtin backend found, trying to load plugin
Error loading module '/usr/lib/samba/pdb/xxxxxxx.so': /usr/lib/samba/pdb/xxxxxxx.so: cannot open shared object file: No such file or directory
No builtin nor plugin backend for xxxxxxx found
PANIC (pid 5975): pdb_get_methods_reload: failed to get pdb methods for backend xxxxxxx

BACKTRACE: 7 stack frames:
#0 pdbedit(log_stack_trace+0x29) [0xb77081b9]
#1 pdbedit(smb_panic+0x28) [0xb77082b8]
#2 pdbedit(+0x5faa3) [0xb7692aa3]
#3 pdbedit(initialize_password_db+0x23) [0xb7695913]
#4 pdbedit(main+0x33f) [0xb7669c0f]
#5 /lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf5) [0xb7388905]
#6 pdbedit(+0x390d5) [0xb766c0d5]
smb_panic(): calling panic action [/usr/share/samba/panic-action 5975]
smb_panic(): action returned status 0
Can not dump core: corepath not set up
Please install an MTA on this system if you want to use sendmail!

```

COMMENT -- I changed the actual password in the results to xxxxxxx 

Did you allow Webmin to configure Samba?  It sure looks that way.  None of the above happens with the Samba page by default.

In the end this pretty much means there are no Samba users created.  You need to have a Linux user AND a Samba user for the Samba server towork correctly.  Even the guest user (the user *nobody*) has to be in the Samba user database.  I believe this is the root of your problem.

> 
```
ray@ray-desktop:~$ getent passwd |grep 1000
ray:1000:1000:ray,,,:/home/ray:/bin/bash 
```

I would have expected to see at least you listed as a Ubuntu user and a Samba user.

One of the nice things about using the ```
 blocks is the smilies don't show up.

> 
[CODE]ray@ray-desktop:~$ cat /etc/samba/smb.conf
[global]
panic action = /usr/share/samba/panic-action %d
workgroup = WORKGROUP
netbios name = silvanet
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = xxxxxxx
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no


#Share Definitions


[homes]
comment = Home Directories
browseable = yes
writable = yes
security mask = 0700
create mask = 0700

```

COMMENT - Again, I changed the actual password in the results above to xxxxxxx 

This is not going to work anyway, as long as there are no users available to authenticate (see pdbedit).

> 
```
ray@ray-desktop:~$ hostname
ray-desktop

ray@ray-desktop:~$ cat /etc/hosts
127.0.0.1 localhost
192.168.0.194 ray-desktop


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters 
```

This is fine.  I assume the 192.168.0.194 address is a fixed address.
> 
There is no second Ubuntu machine - only one.

Great.  That makes it easier.

This is all consistent with the ***Samba server ***being misconfigured or worse yet, damaged, while the **Samba client **is functioning okay.

Don't split your comments up into multiple posts.  It doesn't help.  In fact it makes it harder.  Do use the [SIZE=5]#[/SIZE] icon at the top of the advanced editor to post terminal output.  This helps preserve the formatting and makes it easier to read.

I suggest you purge the webmin and samba packages.  Then install only the samba packages themselves like this```

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install samba samba-common 
```

When this is done, using the [SIZE=4]#[/SIZE] icon to use the ```
 blocks, post the output of this command[CODE]smbtree -d3
```

---

### Post by ray_silva on 2014-04-05
OK, I finally figured out what you meant by the editor in advanced mode.

RE: "[COLOR=#000000]The files require you to use sudo (become root) to edit them."
[/COLOR]I was browsing to the files from the text editor. How do I do that by being in sudo?

Re: "[COLOR=#000000]Windows machines showing up when browsing with Ubuntu is not unusual"
[/COLOR]I was also able to access the files by just typing in the passwords for the Windows machines. I guess then that the Samba configuration credentials are really needed only for the Ubuntu machine?

Re: "[COLOR=#000000]Did you allow Webmin to configure Samba? It sure looks that way. None of the above happens with the Samba page by default."
[/COLOR]Yes, I think that's where I got myself in deeper and deeper trouble. I searched Interned for how to set up Windows 7 clients to work with an Ubuntu Samba server and got tons of "different" solutions. None of them worked for me and I kept trying others, including Webmin. I may have messed up more than was needed.

Re: "[COLOR=#000000]I assume the 192.168.0.194 address is a fixed address."
[/COLOR]If by "fixed" you mean that it is assigned by my router to the Ubuntu machine. However, the network addresses are assigned by DHCP.

re: "[COLOR=#000000]I suggest you purge the webmin and samba packages."
[/COLOR]while sudo apt-get --purge remove samba was running I got this (I was expecting full purge)
Removing gadmin-samba ... note this is not the full code result, only the relevant part:

```
Purging configuration files for gadmin-samba ...
dpkg: warning: while removing gadmin-samba, directory '/etc/gadmin-samba' not empty so not removed
dpkg: warning: while removing gadmin-samba, directory '/var/lib/samba/profiles' not empty so not removed
Removing system-config-samba ...

```

webmin purged completely, but said

```
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot

```

I went ahead and ran your suggested samba re-installation code before rebooting. I hope this didn't mess things up. I didn't see any strange messages or errors in the installation.

Here's the smbtree -d3 result

```
ray@ray-desktop:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
WARNING: The "null passwords" option is deprecated
added interface ham0 ip=2620:9b::190c:bd2e bcast=2620:9b::ffff:ffff netmask=ffff:ffff:ffff:ffff:ffff:ffff::
added interface wlan0 ip=fe80::208:54ff:fe8d:99f%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface ham0 ip=fe80::7879:19ff:fe0c:bd2e%ham0 bcast=fe80::ffff:ffff:ffff:ffff%ham0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.0.194 bcast=192.168.0.255 netmask=255.255.255.0
added interface ham0 ip=25.12.189.46 bcast=25.255.255.255 netmask=255.0.0.0
Enter ray's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>

```

Thanks.

---

### Post by bab1 on 2014-04-05
> **ray_silva said:**
> OK, I finally figured out what you meant by the editor in advanced mode.

RE: "[COLOR=#000000]The files require you to use sudo (become root) to edit them."
[/COLOR]I was browsing to the files from the text editor. How do I do that by being in sudo?

The command *sudo* allows you to execute commands as the root user.  There are no real limits as to what root can do.  This includes issuing a command that destroys the OS itself.  **Use with caution**.

From the command line you can use this```
sudo nano <some_file>
```...where <some file> is a file of your choice.  

If you want a GUI based text editor you would use this```
gksudo gedit <some_file>
``` 
> 

Re: "[COLOR=#000000]Windows machines showing up when browsing with Ubuntu is not unusual"
[/COLOR]I was also able to access the files by just typing in the passwords for the Windows machines. I guess then that the Samba configuration credentials are really needed only for the Ubuntu machine?

Yes the Ubuntu machine requires user accounts just like the Windows machine.  Samba maintains it's own user accounts.  I have the same username and password on all of my machines.  This keeps them coordinated.
> 
Re: "[COLOR=#000000]Did you allow Webmin to configure Samba? It sure looks that way. None of the above happens with the Samba page by default."
[/COLOR]Yes, I think that's where I got myself in deeper and deeper trouble. I searched Interned for how to set up Windows 7 clients to work with an Ubuntu Samba server and got tons of "different" solutions. None of them worked for me and I kept trying others, including Webmin. I may have messed up more than was needed.

I see you also installed *gadmin-samba*.  With that you are really off the beaten path.  None of these are needed for you to successfully share files on an Ubuntu host.
> 

Re: "[COLOR=#000000]I assume the 192.168.0.194 address is a fixed address."
[/COLOR]If by "fixed" you mean that it is assigned by my router to the Ubuntu machine. However, the network addresses are assigned by DHCP.

For your needs it means that the IP address does not change.
> 
re: "[COLOR=#000000]I suggest you purge the webmin and samba packages."
[/COLOR]while sudo apt-get --purge remove samba was running I got this (I was expecting full purge)
Removing gadmin-samba ... note this is not the full code result, only the relevant part:

```
Purging configuration files for gadmin-samba ...
dpkg: warning: while removing gamin-samba, directory '/etc/gadmin-samba' not empty so not removed
dpkg: warning: while removing gadmin-samba, directory '/var/lib/samba/profiles' not empty so not removed
Removing system-config-samba ...

```

I would also purge gadmin-samba like this```
sudo apt-get purge gadmin-samba
```
> 

webmin purged completely, but said

```
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot

```

That's normal.  It just means it will be reconfigured the next time you reboot.
> 

I went ahead and ran your suggested samba re-installation code before rebooting. I hope this didn't mess things up. I didn't see any strange messages or errors in the installation.

Here's the smbtree -d3 result

```
ray@ray-desktop:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
WARNING: The "null passwords" option is deprecated
added interface ham0 ip=2620:9b::190c:bd2e bcast=2620:9b::ffff:ffff netmask=ffff:ffff:ffff:ffff:ffff:ffff::
added interface wlan0 ip=fe80::208:54ff:fe8d:99f%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface ham0 ip=fe80::7879:19ff:fe0c:bd2e%ham0 bcast=fe80::ffff:ffff:ffff:ffff%ham0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.0.194 bcast=192.168.0.255 netmask=255.255.255.0
added interface ham0 ip=25.12.189.46 bcast=25.255.255.255 netmask=255.0.0.0
Enter ray's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>

```

Thanks.
I think you left off the last part of the terminal output.  Post the output of this```
smbtree
```...this is the non debug version.

Post the output of ```
sudo pdbedit -L
```

What version of Ubuntu are you using?  

Are you using Unity as the desktop environment?  

Do you need to share directories with user/password authentication?

---

### Post by ray_silva on 2014-04-05
gadmin-samba purged

Here's full terminal code from command to return of prompt

```

ray@ray-desktop:~$ sudo smbtree
WARNING: The "null passwords" option is deprecated
added interface ham0 ip=2620:9b::190c:bd2e bcast=2620:9b::ffff:ffff netmask=ffff:ffff:ffff:ffff:ffff:ffff::
added interface wlan0 ip=fe80::208:54ff:fe8d:99f%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface ham0 ip=fe80::7879:19ff:fe0c:bd2e%ham0 bcast=fe80::ffff:ffff:ffff:ffff%ham0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.0.194 bcast=192.168.0.255 netmask=255.255.255.0
added interface ham0 ip=25.12.189.46 bcast=25.255.255.255 netmask=255.0.0.0
Enter root's password: 
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
ray@ray-desktop:~$

```

re: "[COLOR=#000000]What version of Ubuntu are you using?"
[/COLOR]13.10

[COLOR=#000000]"Are you using Unity as the desktop environment?"
[/COLOR]Yes

[COLOR=#000000]"Do you need to share directories with user/password authentication?"
Not sure what you mean, but yes, I would like user/password authentication to be required and used in order to share directories.

And, the results of [/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo pdbedit -L

[/FONT][/COLOR]Again, I changed the actual password in the results to xxxxxxx
```
WARNING: The "null passwords" option is deprecated
No builtin backend found, trying to load plugin
Error loading module '/usr/lib/samba/pdb/xxxxxxx.so': /usr/lib/samba/pdb/xxxxxxx.so: cannot open shared object file: No such file or directory
No builtin nor plugin backend for xxxxxxx found
PANIC (pid 8795): pdb_get_methods_reload: failed to get pdb methods for backend xxxxxxx


BACKTRACE: 7 stack frames:
 #0 pdbedit(log_stack_trace+0x29) [0xb762c1b9]
 #1 pdbedit(smb_panic+0x28) [0xb762c2b8]
 #2 pdbedit(+0x5faa3) [0xb75b6aa3]
 #3 pdbedit(initialize_password_db+0x23) [0xb75b9913]
 #4 pdbedit(main+0x33f) [0xb758dc0f]
 #5 /lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf5) [0xb72ac905]
 #6 pdbedit(+0x390d5) [0xb75900d5]
smb_panic(): calling panic action [/usr/share/samba/panic-action 8795]
smb_panic(): action returned status 0
Can not dump core: corepath not set up
ray@ray-desktop:~$ Please install an MTA on this system if you want to use sendmail!

```

Thanks

---

### Post by bab1 on 2014-04-05
> **ray_silva said:**
> gadmin-samba purged

Here's full terminal code from command to return of prompt

```

ray@ray-desktop:~$ sudo smbtree
WARNING: The "null passwords" option is deprecated
added interface ham0 ip=2620:9b::190c:bd2e bcast=2620:9b::ffff:ffff netmask=ffff:ffff:ffff:ffff:ffff:ffff::
...
ray@ray-desktop:~$

```

There is no need to use *sudo* with *smbtree*.  Also the output is not right.  The command *smbtree* with no switches should just give you the shares.  It should look like something like this```

BEACHES
	\\MANILA         		manila server (Samba, Ubuntu)
		\\MANILA\HP-LaserJet-2200	HP LaserJet 2200 with Duplexer and 3rd tray
		\\MANILA\PDF            	PDF
		\\MANILA\IPC$           	IPC Service (manila server (Samba, Ubuntu))
		\\MANILA\print$         	Printer Drivers

```...that server has no shares yet.  It is a desktop machine.
> 
re: "[COLOR=#000000]What version of Ubuntu are you using?"
[/COLOR]13.10

[COLOR=#000000]"Are you using Unity as the desktop environment?"
[/COLOR]Yes

[COLOR=#000000]"Do you need to share directories with user/password authentication?"
Not sure what you mean, but yes, I would like user/password authentication to be required and used in order to share directories.

And, the results of [/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo pdbedit -L

[/FONT][/COLOR]Again, I changed the actual password in the results to xxxxxxx
```
WARNING: The "null passwords" option is deprecated
No builtin backend found, trying to load plugin
Error loading module '/usr/lib/samba/pdb/xxxxxxx.so': /usr/lib/samba/pdb/xxxxxxx.so: cannot open shared object file: No such file or directory
No builtin nor plugin backend for xxxxxxx found
PANIC (pid 8795): pdb_get_methods_reload: failed to get pdb methods for backend xxxxxxx


BACKTRACE: 7 stack frames:
 #0 pdbedit(log_stack_trace+0x29) [0xb762c1b9]
 #1 pdbedit(smb_panic+0x28) [0xb762c2b8]
 #2 pdbedit(+0x5faa3) [0xb75b6aa3]
 #3 pdbedit(initialize_password_db+0x23) [0xb75b9913]
 #4 pdbedit(main+0x33f) [0xb758dc0f]
 #5 /lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf5) [0xb72ac905]
 #6 pdbedit(+0x390d5) [0xb75900d5]
smb_panic(): calling panic action [/usr/share/samba/panic-action 8795]
smb_panic(): action returned status 0
Can not dump core: corepath not set up
ray@ray-desktop:~$ Please install an MTA on this system if you want to use sendmail!

```

This is definitely wrong.  At the very minimum it should look like this```

sudo pdbedit -L
[sudo] password for ray:
nobody:65534:nobody
ray:1000:Ray 

```
Typically the output you have means that a different database has been configured. 

Do you have a copy of the original smb.conf file?

What is the output of this```
ls -l /etc/samba
```

---

### Post by ray_silva on 2014-04-05
I guess I really messed it up. Yes, there appear to be old multiple copies of the samba config file.

```
ray@ray-desktop:~$ ls -l /etc/samba
total 32
-rw-r--r-- 1 root root     8 Nov 23  2012 gdbcommands
-rw-r--r-- 1 root root  3533 Mar 30 16:36 smb2.conf
-rw-r--r-- 1 ray  ray    694 Mar 30 17:06 smb.conf
-rw-r--r-- 1 root root 12599 Mar 30 15:47 smb.conf.old.gadmin-samba-0.3.2
-rw-r--r-- 1 root root    91 Mar 30 15:47 smbusers
-rw-r--r-- 1 root root     0 Mar 30 15:24 user.map

```

---

### Post by bab1 on 2014-04-05
> **ray_silva said:**
> I guess I really messed it up. Yes, there appear to be old multiple copies of the samba config file.

```
ray@ray-desktop:~$ ls -l /etc/samba
total 32
-rw-r--r-- 1 root root     8 Nov 23  2012 gdbcommands
-rw-r--r-- 1 root root  3533 Mar 30 16:36 smb2.conf
-rw-r--r-- 1 ray  ray    694 Mar 30 17:06 smb.conf
-rw-r--r-- 1 root root 12599 Mar 30 15:47 smb.conf.old.gadmin-samba-0.3.2
-rw-r--r-- 1 root root    91 Mar 30 15:47 smbusers
-rw-r--r-- 1 root root     0 Mar 30 15:24 user.map

```
All of those appear to be modified in some manner.  Post the **complete **output of this```
cat /etc/samba/smb.conf.old.gadmin-samba-0.3.2
```
This may be the original.  I will look at it and see if we can use it.

---

### Post by ray_silva on 2014-04-05
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
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#


#======================= Global Settings =======================


[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	username map = /etc/samba/user.map
	map to guest = bad user
	encrypt passwords = yes
	passwd program = /usr/bin/passwd %u
	dns proxy = no
	server string = %h server (Samba, Ubuntu)
	path = /home
	default = home
	unix password sync = yes
	remote announce = 192.168.0.194
	workgroup = WORKGROUP
	os level = 20
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	usershare allow guests = yes
	max log size = 1000
	pam password change = yes


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of


# server string is the equivalent of the NT Description field


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.


# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


#### Networking ####


# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 wlan0
# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes






#### Debugging/Accounting ####


# This tells Samba to use a separate log file for each machine
# that connects


# Cap the size of the individual log files (in KiB).


# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no


# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.


# Do something sensible when Samba crashes: mail the admin a backtrace




####### Authentication #######


# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user


# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam




# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.


# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).


# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.


# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections


########## Domains ###########


# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
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


########## Printing ##########


# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes


# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap


# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;	printing = cups
;   printcap name = cups


############ Misc ############


# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m


# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY


# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &


# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto


# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes


# Setup usershare options to enable non-root users to share folders
# with the net usershare command.


# Maximum number of usershare. 0 (default) means that usershare is disabled.
;	usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones


#======================= Share Definitions =======================


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
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
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
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
;	guest ok = no
;	read only = yes
	create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin


# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes


# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[home]
	path = /home
	writeable = yes
;	browseable = yes
	valid users = ray

```

I gotta admit I found this file totally confusing. I don't see anywhere in it where one would put the individual Windows machines on the network that would share - not iP addresses, not usernames, not passwords - nothing. That's why I tried Webmin. It was hardly any less confusing. I've been reading the Webmin manual to try to understand, but some entries that should be simple are nowhere simply explained.

Maybe you can figure if something in this is at least usable.

I have also been reading that it is harder to get Windows 7 machines to share because of something Windows did after XP (which was apparently an easy share).

I also saw that the firewall may be blocking (but it didn't before when I was at least able to see the Windows network & access files - I can't now). Anyway, I have turned it off just in case.

All this is because I wanted to set up my Ubuntu machine to operate as a file server to the Windows Networked machines where all files could be stored and retrieved from.

Again, Thanks.

---

### Post by bab1 on 2014-04-05
> **ray_silva said:**
> 
I gotta admit I found this file totally confusing. I don't see anywhere in it where one would put the individual Windows machines on the network that would share - not iP addresses, not usernames, not passwords - nothing. That's why I tried Webmin. It was hardly any less confusing. I've been reading the Webmin manual to try to understand, but some entries that should be simple are nowhere simply explained.

You have a completely erroneous idea of what the *smb.conf* file is for.  It's not to add Windows machines, IP addresses or passwords at all.  It's purpose is to configure the smbd and nmbd daemons (processes) so that the Samba server can serve files to clients that request them.  The only database exists outside of the *smb.conf* file.  The computer name recognition is all handled internally by the two processes via NETBIOS discovery.   
> 
Maybe you can figure if something in this is at least usable.

It's going to be easier to provide you a known (to me) good smb.conf file and have you copy it over.
> 
I have also been reading that it is harder to get Windows 7 machines to share because of something Windows did after XP (which was apparently an easy share).

The change was to using SMB2 instead of just SMB (CIFS).  This has now also includes SMB3.  The bottom line is that Samba has been updated and the original configuration file is still the same.
> 
I also saw that the firewall may be blocking (but it didn't before when I was at least able to see the Windows network & access files - I can't now). Anyway, I have turned it off just in case.

I'd rather diagnose what you have rather than guess at the problem.
> 
All this is because I wanted to set up my Ubuntu machine to operate as a file server to the Windows Networked machines where all files could be stored and retrieved from.

This is doable.  I have Samba servers running as we speak.

If you want to keep the file you are presently using you will need to rename it.  ```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.notworking
```

I am attaching a default smb.conf file (with the name smb.conf.txt).  Copy that file to your home directory. Then copy this file you downloaded from me to the /etc/samba directory.  Then change the ownership to root:root with this command```
sudo chown root:root /etc/samba/smb.conf.txt
```...Now you need to rename it using this command```
sudo mv /etc/samba/smb.conf.txt /etc/samba/smb.conf
```

Then reload Samba with this```
sudo service smbd restart
```

Then post the output of this again```
sudo pdbedit -L
```

After we get this running if you have questions I will either answer or direct you to the appropriate site.  For now just follow along.

---

### Post by ray_silva on 2014-04-06
OK, after doing that, upon reloading Samba with the sudo service smbd restart command from Terminal, my browser crashed. When I reopened it and ran the sudo pdbedit -L command. I got this.

```
ray:1000:ray
smbguest:1001:Samba guest account
root:0:root

```
But Ubuntu machine cannot now even see the Windows network computers as it was able to do before.

I restarted the Windows network computers. They all see each other fine, but do not see the Ubuntu computer at all.

I'm studying the new config file to see exactly what is different in it.

Now that you mention NETBIOS, I checked my router's DHCP settings. I have no WINS server configured. Is that necessary? I didn't think so because the router is having no problem assigning an IP address to the Ubuntu computer on the network. The DHCP server is always broadcasting.

---

### Post by ray_silva on 2014-04-06
After a little time now the Ubuntu machine running samba CAN see the Windows WORKGROUP on the Windows network.

So we are back to at least Ubuntu seeing and accessing the filed on the Windows network.

Now - what I need is for any of the Windows computers to see the Ubuntu machine and access its shared files.

---

### Post by bab1 on 2014-04-06
> **ray_silva said:**
> After a little time now the Ubuntu machine running samba CAN see the Windows WORKGROUP on the Windows network.

So we are back to at least Ubuntu seeing and accessing the filed on the Windows network.

Now - what I need is for any of the Windows computers to see the Ubuntu machine and access its shared files.

I want you to make a copy of the *smb.conf* file with this command```
sudo cp /etc/samba/smb.conf /etc/samba/original
```

Then I want you to edit your* smb.conf* file.  We need to add this line just under the [global] label.  It should look like this```

netbios name = ray_server
```[COLOR="#0000FF"]...Edit: you need to restart the samba daemon for this to take effect.  To do that you need to use this command[/COLOR]```
sudo service smbd restart
```

This will cause the server to broadcast it's name on the local network.

DO NOT change anything else.  We have made progress the samba data base is working correctly now,  To see this you can use this```
smbtree -d3
```...post the output fro me to see too.

---

### Post by ray_silva on 2014-04-06
smbtree -d3 results (after restarting smbd service)


```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface ham0 ip=2620:9b::190c:bd2e bcast=2620:9b::ffff:ffff netmask=ffff:ffff:ffff:ffff:ffff:ffff::
added interface wlan0 ip=fe80::208:54ff:fe8d:99f%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface ham0 ip=fe80::7879:19ff:fe0c:bd2e%ham0 bcast=fe80::ffff:ffff:ffff:ffff%ham0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.0.194 bcast=192.168.0.255 netmask=255.255.255.0
added interface ham0 ip=25.12.189.46 bcast=25.255.255.255 netmask=255.0.0.0
Enter ray's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>

```

I figure the ham0 interfaces are from hamachi for my mobile phone connectivity. I have no idea why genache.tdb is denying permission. Should I have run the smbtree command in sudo? Just in case so, here's the result running it in sudo

```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface ham0 ip=2620:9b::190c:bd2e bcast=2620:9b::ffff:ffff netmask=ffff:ffff:ffff:ffff:ffff:ffff::
added interface wlan0 ip=fe80::208:54ff:fe8d:99f%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface ham0 ip=fe80::7879:19ff:fe0c:bd2e%ham0 bcast=fe80::ffff:ffff:ffff:ffff%ham0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.0.194 bcast=192.168.0.255 netmask=255.255.255.0
added interface ham0 ip=25.12.189.46 bcast=25.255.255.255 netmask=255.0.0.0
Enter root's password: 
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>

```

---

### Post by bab1 on 2014-04-06
> **ray_silva said:**
> 
I figure the ham0 interfaces are from hamachi for my mobile phone connectivity. I have no idea why genache.tdb is denying permission. Should I have run the smbtree command in sudo? 

The hamachi interfaces are fine.  It's just ID'ing every interface available.  It's normal to not have permission to genache.tdb.  This is not a failure; just info.

I suggest we add a share to the configuration.  How many different users (accounts) will be accessing a typical share?  Do you really need a [homes] share or where you just trying to make something work.?  The conventional place to store data is at /srv.

---

### Post by ray_silva on 2014-04-06
[EDIT]
Woah. It was just a matter of time. Now all the computers are showing up. Is it common for files and folders normally hidden in Windows to show in the Ubuntu machine's viewing of the Windows folders?
[EDIT]

Yup. I was just trying to get it to work first.

Just before I read your last post I did some fiddling with the router settings and turned off the firewall, and voila, I was finally able to see "RAY_SERVER" in the Windows network, but there is still one slight little problem.

When I browse the network in the Ubuntu machine it sees a location called 'Windows Network." Inside that folder is my "WORKGROUP." But now none of the Windows computers show up in there as they did before. The only thing that shows up in there is "RAY_SERVER."

There are three different accounts for now that will be accessing the server share location. It is OK if it is at /srv as long as I can make organized folders under that. It would be best if each client (user) sharing has access to only its designated share area. On the other hand, I would like to be able to browse into each of the client's (user's) shared folders on the three clients from the Ubuntu machine. Each client Windows machine has essentially one major user (although I can go to the individual client stations and log in as administrator with full control).

---

### Post by bab1 on 2014-04-06
> **ray_silva said:**
> [EDIT]
Woah. It was just a matter of time. Now all the computers are showing up. Is it common for files and folders normally hidden in Windows to show in the Ubuntu machine's viewing of the Windows folders?
[EDIT]
The short answer is: YES.  All the computers are on the same LAN and will show up as they are discovered.  It takes between 5 and 15 minutes for that to happen.
> 
Yup. I was just trying to get it to work first.

Just before I read your last post I did some fiddling with the router settings and turned off the firewall, and voila, I was finally able to see "RAY_SERVER" in the Windows network, but there is still one slight little problem.
Does this mean that the entire local LAN is unprotected from the Internet troublemakers?  I have a firewall on my router that won't pass Windows browsing from the Internet.  The local LAN has no restrictions at all.
> 
When I browse the network in the Ubuntu machine it sees a location called 'Windows Network." Inside that folder is my "WORKGROUP." But now none of the Windows computers show up in there as they did before. The only thing that shows up in there is "RAY_SERVER."

That really should say "Windows TYPE Networks"  Both Samba and Windows hosts will show up.  The workgroups are only for visual separation.  They have no other use.
> 
There are three different accounts for now that will be accessing the server share location. It is OK if it is at /srv as long as I can make organized folders under that. It would be best if each client (user) sharing has access to only its designated share area. On the other hand, I would like to be able to browse into each of the client's (user's) shared folders on the three clients from the Ubuntu machine. Each client Windows machine has essentially one major user (although I can go to the individual client stations and log in as administrator with full control).
You as the administrator (via sudo) directly on the Ubuntu host can always see what is in all of the files on the entire machine.

You can set up the shares as:
[LIST]
[*]Public (all can create files and directories read and write to the files) 
[*]Private (only an authorized user can create files and directories read and write to the files)
[*]Semi-Private ( only an authorized group can create files and directories read and write to the files)
[*]
[/LIST]

If you have different users on each windows machine you need to create the same named user account on Ubuntu and the same named Samba user account.  In other words each user in the LAN needs a Windows, Ubuntu and Samba account, all with the same name.  Once that infrastructure is set up we can begin.  There is a specific method to add users to Ubuntu that you should use```
sudo adduser <user_name> 
```...where <user_name> is by your choice.  To add users to the Samba database you use this```
sudo smbpasswd -a <user_name>
```..always use the same individual  password for both the Windows, Ubuntu and Samba user account.

Is that enough info for you to add the users?  

Questions or concerns?

---

### Post by ray_silva on 2014-04-07
Thank you so much for your patience and help. You really are Super Penguin.

I have a router enabled firewall and each Windows computer on the LAN also has it's own firewall. The firewall I disabled was the Ubuntu one. Does that have to remain off? I wanted as much security as possible on the server.

If I understand you correctly, each existing individual Windows user account must also be created as a Ubuntu user and as a Samba user account, keeping the same Windows usernames and passwords in Ubuntu and Samba. Two of the Windows computers have the same username and password (one is a desktop and the other is a laptop) and are only distinguished on the network by their computer names. Is that going to be a problem?

---

### Post by bab1 on 2014-04-07
> **ray_silva said:**
> Thank you so much for your patience and help. You really are Super Penguin.

I have a router enabled firewall and each Windows computer on the LAN also has it's own firewall. The firewall I disabled was the Ubuntu one. Does that have to remain off? I wanted as much security as possible on the server.

No it does not have to stay off.  You just need to configure it correctly.
> 
If I understand you correctly, each existing individual Windows user account must also be created as a Ubuntu user and as a Samba user account, keeping the same Windows usernames and passwords in Ubuntu and Samba. Two of the Windows computers have the same username and password (one is a desktop and the other is a laptop) and are only distinguished on the network by their computer names. Is that going to be a problem?
The user names are what is unique to each machine  If you have 2 windows machines and they both have an account with the same user name then you only need 1 account on the Ubuntu host with that name.

---

### Post by ray_silva on 2014-04-07
Can you suggest ufw configuration?

If the network is working and I can get to all the server shared directories from any of the Windows computers on the network, what are those Ubuntu and Samba user names used for? I can also get to any of the Windows shared directories on the network computers from the Ubuntu server.

---

### Post by bab1 on 2014-04-07
> **ray_silva said:**
> Can you suggest ufw configuration?

If the network is working and I can get to all the server shared directories from any of the Windows computers on the network, what are those Ubuntu and Samba user names used for? I can also get to any of the Windows shared directories on the network computers from the Ubuntu server.

The all of this file "sharing" stuff is really just the user mounting the remotely available share to the local system.  If you are logged into a Windows machine as Ray and request access to a portion of the of the remote machine's file to mount to your local machine you: A) have to be authenticated (who are you) and B) authorized (can you do that).  The Samba user on Ubuntu is the part that is authenticated and the Ubuntu user is what is authorized.  They are both needed.  On a windows machine it is the same, but that is all done in the background using the same user.  Samba is not a part of Linux.  It is a project that was created using Linux as the OS, so it is not as integrated.  Your configuration is the integration.

Have you added the users?  After you do add them, what do you get with these commands?  ```
sudo pdbedit -L

sudo getent passwd|grep 100

```

[COLOR="#0000FF"]Edit:  I don't use UFW on my Samba servers.  I don't use any host based firewalls at all.  If you are authenticated to a machine in my network then you are known to me and I don't need to protect myself internally on my LAN.  I'm not saying you can't or even that you should or shouldn't use UFW.  I'm saying I don't so I have no experience in that area. [/COLOR]

---

### Post by ray_silva on 2014-04-18
Sorry that I haven't gotten back to you. Everything is working great thanks to your help. I am currently limiting to one user but will add as per your last message as needed and if I have any trouble with that (but I don't expect so), I'll get back to you for help. You're great and this has been an excellent learning experience for me.

I'm a little paranoid about protecting data since I come from Windows environment experience. My intention was to give the server only local network access and have it not connect to the Internet. I have a firewall set on my router and also use port forwarding and specific mac address filters for the authorized network machines. Since the individual Windows machines do have Internet access, each of them have both firewalls and anti-virus software installed. I also have them using encrypted htpps, and use other security measures as well. Is Linux as "bullet proof" as I've heard? I have a couple of older notebooks that were running Windows XP and I'm thinking about installing Ubuntu on them.

Again - thanks - you're SUPER.

---

### Post by bab1 on 2014-04-18
> **ray_silva said:**
> Sorry that I haven't gotten back to you. Everything is working great thanks to your help. I am currently limiting to one user but will add as per your last message as needed and if I have any trouble with that (but I don't expect so), I'll get back to you for help. You're great and this has been an excellent learning experience for me.

I'm a little paranoid about protecting data since I come from Windows environment experience. My intention was to give the server only local network access and have it not connect to the Internet. I have a firewall set on my router and also use port forwarding and specific mac address filters for the authorized network machines. Since the individual Windows machines do have Internet access, each of them have both firewalls and anti-virus software installed. I also have them using encrypted htpps, and use other security measures as well. Is Linux as "bullet proof" as I've heard? I have a couple of older notebooks that were running Windows XP and I'm thinking about installing Ubuntu on them.

Again - thanks - you're SUPER.

Since we have solved the Samba issue you should mark this thread solved.

The Samba server can be configured to only respond to your LAN requests if you want.  When you use the term "authorized network machines", do you mean: Internet authorized network machines?  It's helpful to understand client/server network connectivity works.  If the Ubuntu OS has nothing but Samba listening for requests (the server) and you restrict it's listening to the local LAN.  In addition, NETBIOS broadcasts don't pass routers.  You don't need to do anything more and you will still have Internet access (WAN).

Linux is more robust by design that Windows is.  Windows viruses are irrelevant.  If you are going to use the laptops as clients only then you only need to worry about Web based malware.  At home I use NoScript and AdBlock on my all my machines web browsers.  No AV at all.  No firewall on these machines either.  The one Windows host I have does have AV, but doesn't have a host based firewall.  The only firewall I use is at the edge of my LAN (just after the router).  On the other hand I don't have any public facing servers to worry about either.  :-)

You should not attempt to use Samba via the Internet without using a VPN.  That VPN will have to use bridging so you can have access to the NETBIOS broadcasts.  Samba performs as if the Internet machine is part of the local LAN.

But we are really OT now aren't we?

---

### Post by ray_silva on 2014-04-30
Thanks so much. I marked it as [SIOLVED]. The "authorized network machines" are those on the local network controlled by my router. That local network is NOT wired. It is completely WiFi. I use MAC address filtering and my router firewall is enabled. Since the network is wireless I'm assuming the communication between the networked machines is going across Internet channels (open ports?). The Ubuntu (Samba) server right now has Internet access, but my intention is that it will not (as you say) fact public. All the Windows (Samba clients) do have Internet access and will. They all have firewalls and AV. On all of them I force https unless absolutely necessary not to do so. I also use AdBlock. On Firefox I use NoScript, too. I don't know why it's not available for Chrome, but I use an alternative if using Chrome. In some cases I use Tor. I never use IE at all. Do I still need a VPN? Is Hamachi tunnel useful?

Yes, I realize we're OT, but you are a gold-mine of information. Thanks again. Many beans and coffee cups to you...

---

### Post by bab1 on 2014-04-30
> **ray_silva said:**
> Thanks so much. I marked it as [SIOLVED]... Since the network is wireless I'm assuming the communication between the networked machines is going across Internet channels (open ports?). 

Wireless is not Internet based.  Wireless in this case refers to how the bitstream flows between hosts (computers) on a LAN.  In a sense it is the functional equivalent of the physical wiring only.  No Internet and no TCP/UDP ports.
> 
The Ubuntu (Samba) server right now has Internet access, but my intention is that it will not (as you say) face public. All the Windows (Samba clients) do have Internet access and will. They all have firewalls and AV. On all of them I force https unless absolutely necessary not to do so. I also use AdBlock. On Firefox I use NoScript, too. I don't know why it's not available for Chrome, but I use an alternative if using Chrome. In some cases I use Tor. I never use IE at all.   Do I still need a VPN? Is Hamachi tunnel useful?
A VPN is one method used to encrypt the data you send across the public internet.  SSL is another way.  If you used SSL then you accept others certificates of authority.  If you use Hamachi for your VPN needs then you accept thme to be trust worthy as they maintain the VPN server in the middle of your connections.  If you feel you need to control everything in the VPN then you need to implement the entire VPN (I.E OpenVPN). 
Yes, I realize we're OT, but you are a gold-mine of information. Thanks again. Many beans and coffee cups to you...
Chek out the *Stickies * at the top of the Security Discussions section of the forum.

---

### Post by ray_silva on 2014-05-03
Hey bab1,

I don't know if you'll get this but I have a question.

I added users but I notice one thing that I can't explain.

All the current users have the accesses I want right now.

The strange thing is that from the Ubuntu machine with the samba server when I browse the network from the file manager I see all the computers (and my cellphone using the local wifi connection) EXCEPT one.

If I click on the Windows Network icon I can see the Windows Homegroup WORKGROUP.

Inside it, as I'd expect, I can see all the computers, including the Ubuntu samba server and the cellphone - nothing is missing.

I can browse into all the computers as per the permissions.

Why is one of my Windows computers missing from the Network browse but not from the WORKGROUP?

I suspect I have done one minor mistake in the configuration but I can't figure out what it is. I've rebooted every machine and still that persists.

Do you have any idea?

Oh, by the way, I upgraded my installation from Ubuntu 13.10 to 14.04; but I don't think that's the reason. I made sure to keep the samba configuration that you helped me establish.

---

### Post by bab1 on 2014-05-03
> **ray_silva said:**
> Hey bab1,
...  strange thing is that from the Ubuntu machine with the samba server when I browse the network from the file manager I see all the computers (and my cellphone using the local wifi connection) EXCEPT one.

If I click on the Windows Network icon I can see the Windows Homegroup WORKGROUP.  Inside it, as I'd expect, I can see all the computers, including the Ubuntu samba server and the cellphone - nothing is missing.  I can browse into all the computers as per the permissions.

Why is one of my Windows computers missing from the Network browse but not from the WORKGROUP?  I suspect I have done one minor mistake in the configuration but I can't figure out what it is. I've rebooted every machine and still that persists.

Do you have any idea?

If I understand you correctly, you have 2 workgroups (WORKGROUP and Homegroup).  Workgroups are intended as a way to visually separate servers so that users could find the group they needed (i.e. sales or engineering or accounting).  There is no security difference or functional difference of one workgroup or another.  Only visual grouping.

In Samba the workgroup that is declared in the smb.conf file is listed outside of the "Windows Networks" for your convenience on that machine.  If you change the Homegroup name of the one machine to WORKGROUP then it will show up with the rest of the machines.  It will also still be listed inside of the "Windows Networks".  In Samba the workgroup is changed by the **workgroup =**  statement.  In windows I believe it is available in the control panel.  I don't have a Windows machine here at home so I can't tell you exactly.
> 
Oh, by the way, I upgraded my installation from Ubuntu 13.10 to 14.04; but I don't think that's the reason. I made sure to keep the samba configuration that you helped me establish.
This is a serious upgrade.  Samba goes from v3.6 to v4.1.  But the file sharing is exactly the same as you can tell already.  Some of the error messages may be different but so far that's all I can see.  I have 14.04 but I'm going to wait awhile before I upgrade my production servers.  In a sense you and others are my guinea pigs.  I help you and learn the new stuff at the same time.  A nice trade off.  :-)

---

