---
title: "Cannot mount windows share"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by graceful1 on 2011-04-11
We have a home network with Mac, Windows, and Ubuntu computers. We also have a "slug" seen by the Windows and Mac computers, but for some reason the Ubuntu computers cannot see it. They could see it a few years ago, but when we updated to 10.10, none of the Ubuntu boxes could see it. When we try to connect using the bookmarks we originally made, for example, we get this error..."Could not open location smb://slug/platypus/  Failure to mount Windows share."  Not sure what do about his as I am still quite the neophyte. Would appreciate any help.

---

### Post by Morbius1 on 2011-04-11
This may be the wildest guess I've ever made in a forum.

First I had to figure out what a "slug" was - somehow a gastropod mollusc that lacks a shell didn't quite seem right.

Then I went to the source of all knowledge in the universe - Wikipedia - and saw this line:
> Along with most NASs, the device isn't out-of-the-box compatible with Windows Vista, as it runs an older version of [Samba]("http://en.wikipedia.org/wiki/Samba_%28software%29") that uses an authentication mechanism that is disabled by default in Vista.[[17]]("http://en.wikipedia.org/wiki/NSLU2#cite_note-16")What I would try is this:
Edit smb.conf on your Ubuntu machine as root:
```
gksu gedit /etc/samba/smb.conf
```Add these lines to the [global] section of smb.conf:
```
client lanman auth = Yes 
lanman auth = Yes 
```Save smb.conf, close gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```Wait a few minutes for the network to settle down a bit and see if it works.

Give it  a shot - what have you got to lose ;).

---

### Post by graceful1 on 2011-04-12
Sorry that I did not explain what a "slug" is -- a network-attached storge device called the Linksys NSLU2.

Thanks for your help. I did attempt the code, but when I entered the last bit to restart samba, I got an error: "smbd: unrecognized service". 

So this means I am not running Samba at all now? How did this happen? And how do I install Samba?

-g.

---

### Post by bab1 on 2011-04-12
> **graceful1 said:**
> Sorry that I did not explain what a "slug" is -- a network-attached storge device called the Linksys NSLU2.

Thanks for your help. I did attempt the code, but when I entered the last bit to restart samba, I got an error: "smbd: unrecognized service". 

So this means I am not running Samba at all now? How did this happen? And how do I install Samba?

-g.

What is the output of: ```
ps -ef | grep mbd
```

---

### Post by graceful1 on 2011-04-12
Well, while I was waiting for a reply, I went to synaptic package manager, and I saw that it was in fact installed. I selected a component, however, that wasn't installed, and I think that I reinstalled samba. 

Then I did the restart command got this:

```
smbd start/running, process 4234

```

The output of the code suggested by BAB1 is

```

root      3999     1  0 00:09 ?        00:00:00 nmbd -D
root      4234     1  0 00:26 ?        00:00:00 smbd -F
root      4236  4234  0 00:26 ?        00:00:00 smbd -F
root      4326  4234  0 00:31 ?        00:00:00 smbd -F
root      4332  4234  0 00:31 ?        00:00:00 smbd -F
root      4335  4234  0 00:31 ?        00:00:00 smbd -F
grace     4405  4386  0 00:38 pts/1    00:00:00 grep mbd

```

Okay, so samba is running. But to get back to the original problem, restarting samba has not allowed me to mount the Windows share. 

This is particularly frustrating because this worked five years ago without much trouble, and I cannot understand why after upgrading I cannot see these shares. I still have the bookmarks for them, but they are useless.

I still am quite inexperienced with this, and I would appreciate any help. There are lots of files on the slug that I need to access.

---

### Post by bab1 on 2011-04-12
> **graceful1 said:**
> Well, while I was waiting for a reply, I went to synaptic package manager, and I saw that it was in fact installed. I selected a component, however, that wasn't installed, and I think that I reinstalled samba. 

Then I did the restart command got this:

```
smbd start/running, process 4234

```

The output of the code suggested by BAB1 is

```

root      3999     1  0 00:09 ?        00:00:00 nmbd -D
root      4234     1  0 00:26 ?        00:00:00 smbd -F
root      4236  4234  0 00:26 ?        00:00:00 smbd -F
root      4326  4234  0 00:31 ?        00:00:00 smbd -F
root      4332  4234  0 00:31 ?        00:00:00 smbd -F
root      4335  4234  0 00:31 ?        00:00:00 smbd -F
grace     4405  4386  0 00:38 pts/1    00:00:00 grep mbd

```

Okay, so samba is running. But to get back to the original problem, restarting samba has not allowed me to mount the Windows share. 

This is particularly frustrating because this worked five years ago without much trouble, and I cannot understand why after upgrading I cannot see these shares. I still have the bookmarks for them, but they are useless.

I still am quite inexperienced with this, and I would appreciate any help. There are lots of files on the slug that I need to access.

Can you ping all the hosts on the LAN that share files?

Edit:  Try these commands:```
findsmb
smbtree
```

---

### Post by graceful1 on 2011-04-12
> **bab1 said:**
> Can you ping all the hosts on the LAN that share files?

Try these commands:```
findsmb
smbtree
```

Okay, here is the output:

```

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.64    HOPE          +[MOONBASE] [Unix] [Samba 3.5.4]
192.168.1.77    SLUG          +[	MOONBASE      ]

```

Those two hosts are probably the only ones active at this hour. HOPE is my PC running Ubuntu, and SLUG is the network-attached storage device that has the share called platypus (and other shares). Well, actually, my MacBook Pro is also up, CLIO, but I turned off Windows sharing for that one. However, you can see it when you use the pulldown menu Places-->Network.

And here is the output for smbtree
```

WORKGROUP
	\\HOPE           		hope server (Samba, Ubuntu)
		\\HOPE\mimosa         	Brother MFC-440CN
		\\HOPE\print$         	Printer Drivers
		\\HOPE\IPC$           	IPC Service (hope server (Samba, Ubuntu))
MOONBASE
	\\SLUG           		
cli_start_connection: failed to connect to SLUG<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED


```

I could turn Windows sharing back on for CLIO if necessary.

Thanks,
G.

---

### Post by bab1 on 2011-04-12
> **graceful1 said:**
> Okay, here is the output:

```

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.64    HOPE          +[MOONBASE] [Unix] [Samba 3.5.4]
192.168.1.77    SLUG          +[	MOONBASE      ]

```

Those two hosts are probably the only ones active at this hour. HOPE is my PC running Ubuntu, and SLUG is the network-attached storage device that has the share called platypus (and other shares). Well, actually, my MacBook Pro is also up, CLIO, but I turned off Windows sharing for that one. However, you can see it when you use the pulldown menu Places-->Network.

And here is the output for smbtree
```

WORKGROUP
	\\HOPE           		hope server (Samba, Ubuntu)
		\\HOPE\mimosa         	Brother MFC-440CN
		\\HOPE\print$         	Printer Drivers
		\\HOPE\IPC$           	IPC Service (hope server (Samba, Ubuntu))
MOONBASE
	\\SLUG           		
cli_start_connection: failed to connect to SLUG<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED


```

I could turn Windows sharing back on for CLIO if necessary.

Thanks,
G.

It looks like HOPE has no shares defined and you can't connect to SLUG.

I would run smbtree in debug mode.  Post the output of this:```
smbtree -d3
```

---

### Post by graceful1 on 2011-04-12
The output was huge. Here it is:

```

grace@hope:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::21f:1fff:fe14:5b5f%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.64 bcast=192.168.1.255 netmask=255.255.255.0
Enter grace's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name MOONBASE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MOONBASE<0x1d>
Got a positive name query response from 192.168.1.77 ( 192.168.1.77 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
Connecting to host=192.168.1.77
Connecting to 192.168.1.77 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608b8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.64 ( 192.168.1.64 )
Got a positive name query response from 192.168.1.77 ( 192.168.1.77 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.64 ( 192.168.1.64 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
Connecting to host=192.168.1.64
Connecting to 192.168.1.64 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
WORKGROUP
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.64 ( 192.168.1.64 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
Connecting to host=192.168.1.64
Connecting to 192.168.1.64 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
	\\HOPE           		hope server (Samba, Ubuntu)
Connecting to host=HOPE
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name HOPE<0x20>
resolve_wins: Attempting wins lookup for name HOPE<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name HOPE<0x20>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
Connecting to 127.0.0.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
		\\HOPE\mimosa         	Brother MFC-440CN
		\\HOPE\print$         	Printer Drivers
		\\HOPE\IPC$           	IPC Service (hope server (Samba, Ubuntu))
MOONBASE
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name MOONBASE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MOONBASE<0x1d>
Got a positive name query response from 192.168.1.77 ( 192.168.1.77 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
Connecting to host=192.168.1.77
Connecting to 192.168.1.77 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608b8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
	\\SLUG           		
Connecting to host=SLUG
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name SLUG<0x20>
resolve_wins: Attempting wins lookup for name SLUG<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SLUG<0x20>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
Connecting to 8.15.7.117 at port 445
Connecting to 8.15.7.117 at port 139
Error connecting to 8.15.7.117 (Connection refused)
Connecting to 63.251.179.13 at port 445
Connecting to 63.251.179.13 at port 139
Error connecting to 63.251.179.13 (Connection refused)
cli_start_connection: failed to connect to SLUG<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
	\\CLIO           		Clio
Connecting to host=CLIO
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name CLIO<0x20>
resolve_wins: Attempting wins lookup for name CLIO<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name CLIO<0x20>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
Connecting to 8.15.7.117 at port 445
Connecting to 8.15.7.117 at port 139
Error connecting to 8.15.7.117 (Connection refused)
Connecting to 63.251.179.13 at port 445
Connecting to 63.251.179.13 at port 139
Error connecting to 63.251.179.13 (Connection refused)
cli_start_connection: failed to connect to CLIO<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED

```

---

### Post by graceful1 on 2011-04-12
> **bab1 said:**
> It looks like HOPE has no shares defined and you can't connect to SLUG.


As to your first comment, yes, HOPE has no shares defined, but SLUG does... one named "ben" and one named "platypus". There may be another named "admin". My Mac is able to see them.

---

### Post by tysonh80 on 2011-04-12
> **graceful1 said:**
> Sorry that I did not explain what a "slug" is -- a network-attached storge device called the Linksys NSLU2.

Thanks for your help. I did attempt the code, but when I entered the last bit to restart samba, I got an error: "smbd: unrecognized service". 

So this means I am not running Samba at all now? How did this happen? And how do I install Samba?

-g.

I get the same error when i attempt to stop samba from what I've read its fairly normal and you can just reboot to restart samba.  Check out this[ howto]("http://ubuntuforums.org/showthread.php?t=1169149") for windows shares. It   fixed mine.  Hope it helps

---

### Post by Morbius1 on 2011-04-12
Your system is leaving your lan and attempting to find SLUG from what I believe to be your ISP's DNS server ( 63.251.179.13 ).

 Change the order of netbios name resolution:

Add a line to the global section again:
```
name resolve order = bcast host lmhosts wins
```Then restart samba again.

You know, this whole machine name-to-ipaddress problem you seem to be having can be remedied by going to the NAS device directly by ip address. It's likely that you have a static ip address on the device anyway ( or you can give it one ) so I would try this:

In a terminal enter:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of the NAS.*[/COLOR]

Once Nautilus opens up to that ip address bookmark it: Bookmarks > Add bookmark. It will then show up under "Places" on the left panel of Nautilus - sort of like a "mapped drive" does in Windows. It will save with the title "Windows shares on 192.168.0.100" which you can then rename to SLUG.

---

### Post by bab1 on 2011-04-12
> **graceful1 said:**
> The output was huge. Here it is:

```

grace@hope:~$ smbtree -d3
...

Connecting to 8.15.7.117 at port 445
Connecting to 8.15.7.117 at port 139
Error connecting to 8.15.7.117 (Connection refused)
Connecting to 63.251.179.13 at port 445
Connecting to 63.251.179.13 at port 139
Error connecting to 63.251.179.13 (Connection refused)


```

As Morbius1 pointed out you have a problem with DNS resolution (see above).  Samba uses DNS resolution to Map *hostname* to *netbios name* to *IP address*.  I does this in the order again pointed out Morbius1.  

I'll bet you are not providing DNS resolution at the LAN level.  In your case the DNS resolver is the ISP's and it is working incorrectly (by DNS protocol standards).

I personally don't like to modify the system any more than needed.  I think you  only need to add the SLUG IP to hostname mapping to the /etc/hosts file and see if you can browse the shares.

---

### Post by graceful1 on 2011-04-12
> **Morbius1 said:**
> Your system is leaving your lan and attempting to find SLUG from what I believe to be your ISP's DNS server ( 63.251.179.13 ).

 Change the order of netbios name resolution:

Add a line to the global section again:
```
name resolve order = bcast host lmhosts wins
```Then restart samba again.



There is a similar line in my smb.conf file already:

```

; name resolve order = lmhosts host wins bcast

```

But as you see there is a semicolon in front of it. I presume that should that be removed?

> 
You know, this whole machine name-to-ipaddress problem you seem to be having can be remedied by going to the NAS device directly by ip address. It's likely that you have a static ip address on the device anyway ( or you can give it one ) so I would try this:

In a terminal enter:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of the NAS.*[/COLOR]

Once Nautilus opens up to that ip address bookmark it: Bookmarks > Add bookmark. It will then show up under "Places" on the left panel of Nautilus - sort of like a "mapped drive" does in Windows. It will save with the title "Windows shares on 192.168.0.100" which you can then rename to SLUG.

Yes, there is a static IP address assigned -- 192.168.1.77
So I don't quite understand what this step is doing -- Are we giving the NAS a new static IP address, different from the one the router is assigning it?

---

### Post by Morbius1 on 2011-04-12
Open a terminal and type:
```
nautilus smb://192.168.1.77
```Nautilus should open up to your NAS device. When it does bookmark it.

It will appear under "Places" on the left panel as "Windows shares on 192.168.1.77".

---

### Post by Morbius1 on 2011-04-12
Sorry missed your other question.
> There is a similar line in my smb.conf file already
; name resolve order = lmhosts host wins bcast 
But as you see there is a semicolon in front of it. I presume that should that be removed?
Similar is not the same. That line dictates the order in which different methods of converting a machine name to an ip address are to be used. The only method that works by default is bcast and it's listed last. Put it first:
```
name resolve order = bcast host lmhosts wins
```
Then restart samba.

---

### Post by graceful1 on 2011-04-12
> **Morbius1 said:**
> Sorry missed your other question.
Similar is not the same. That line dictates the order in which different methods of converting a machine name to an ip address are to be used. The only method that works by default is bcast and it's listed last. Put it first:
```
name resolve order = bcast host lmhosts wins
```
Then restart samba.

Here is the error message that resulted when I tried to open my old bookmark:

```

Could not open location 'smb://slug/platypus/'

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

```

I got the same error earlier tonight when I tried doing what BAB1 said -- putting 192.168.1.77 in the hosts file.

---

### Post by bab1 on 2011-04-12
> **graceful1 said:**
> But do I leave the semicolon in? I notice semicolons in front of other lines.

The semicolon marks the line to be ignored when the smbd starts (e.g. a comment).  When you remove the semicolon it is read as a parameter when the smbd starts.

> I got the same error earlier tonight when I tried doing what BAB1 said -- putting 192.168.1.77 in the hosts file.

Can you ping SLUG?    As in > ping slug

---

### Post by bab1 on 2011-04-12
FYI -- If you do as Morbius1 asked you to do you will never reach the host SLUG by hostname (/etc/hosts) using samba.  The bcast comes first and this is netbios names.

Either way will work, but at times they conflict.  You don't need my way if you are following Morbius1.  He knows how the system works.  He is not just guessing here.

---

### Post by graceful1 on 2011-04-12
> **bab1 said:**
> 
Can you ping SLUG?    

I could not ping SLUG at first. Then someone pointed out to me that there was a problem with the way the router was set up. I had to enable DNSMasque and Local DNS and enter the router's IP address as the primary DNS, 

So I fixed those problems, and now I can ping SLUG.

But we are still left with my original problem -- bookmarks to smb://slug/platypus/ and smb://slug/ben/ that are still broken. (These are called 'ben on slug' and 'platypus on slug').

Correction: I just tried smb://slug/ben/ and it worked. But smb://slug/platypus/ does not work and produces the DBus error described in an earlier post. Why????? :confused:

One more thing: I unmounted ben by pressing the "eject" button, in the Places list (I am not sure I am using the right words here). I got this error:
```

Unable to unmount ben on slug

DBus error org.freedesktop.DBus.Error.UnknownMethod: Method "Unmount" with signature "sou" on interface "org.gtk.vfs.Mount" doesn't exist

```

Despite this alert, ben did disappear.

---

### Post by bab1 on 2011-04-12
> **graceful1 said:**
> I could not ping SLUG at first. Then someone pointed out to me that there was a problem with the way the router was set up. I had to enable DNSMasque and Local DNS and enter the router's IP address as the primary DNS, 

So I fixed those problems, and now I can ping SLUG.


But we are still left with my original problem -- bookmarks to smb://slug/platypus/ and smb://slug/ben/ that are still broken. (These are called 'ben on slug' and 'platypus on slug').

Correction: I just tried smb://slug/ben/ and it worked. But smb://slug/platypus/ does not work and produces the DBus error described in an earlier post. Why????? :confused:

Does the share called platypus sill exist?> 

One more thing: I unmounted ben by pressing the "eject" button, in the Places list (I am not sure I am using the right words here). I got this error:
```

Unable to unmount ben on slug

DBus error org.freedesktop.DBus.Error.UnknownMethod: Method "Unmount" with signature "sou" on interface "org.gtk.vfs.Mount" doesn't exist

```

Despite this alert, ben did disappear.

Are you now able to browse the shares? (Places > Network> etc)

I would put the semicolon back on the line that Morbius1 was talking about.  This is the easiest way to return to the default behavior for that parameter.  Do this (see in red)
```
[COLOR="Red"]**;**[/COLOR]name resolve order = bcast host lmhosts wins
```

Restart Samba (this is important).

Check to see if all is well.

---

### Post by graceful1 on 2011-04-12
> **bab1 said:**
> Does the share called platypus sill exist?


Yes. I am able to reach it on my MacBook Pro.

> 
Are you now able to browse the shares? (Places > Network> etc)


Yes. Places > Network > Windows Network > MOONBASE > SLUG
This reveals four shares: ADMIN 1, ben, DISK 1, and platypus.

Here's the curious thing. Double-clicking on ADMIN 1 & ben works; double-clicking on DISK 1 and platypus does not and returns the DBus error described in an earlier post.

I am able to reach platypus (and the other three shares) using my Mac.

> 
I would put the semicolon back on the line that Morbius1 was talking about.  This is the easiest way to return to the default behavior for that parameter.  Do this (see in red)
```
[COLOR="Red"]**;**[/COLOR]name resolve order = bcast host lmhosts wins
```

Restart Samba (this is important).

Check to see if all is well.

Actually, I had already replaced the semicolon on the advice of the friend who was helping me configure my router (so that I could ping SLUG).

---

### Post by graceful1 on 2011-04-12
New outputs for findsmb and findtree, in case it may be of any use...

```

grace@hope:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.64    HOPE          +[MOONBASE] [Unix] [Samba 3.5.4]
192.168.1.68    CLIO           [MOONBASE] [Unix] [Samba 3.0.10]
192.168.1.77    SLUG          +[MOONBASE] [Unix] [Samba 3.0.11]
grace@hope:~$

```

(CLIO is the Mac)

and

```

grace@hope:~$ smbtree
Enter grace's password: 
WORKGROUP
	\\HOPE           		hope server (Samba, Ubuntu)
		\\HOPE\mimosa         	Brother MFC-440CN
		\\HOPE\IPC$           	IPC Service (hope server (Samba, Ubuntu))
		\\HOPE\print$         	Printer Drivers
MOONBASE
	\\SLUG           		
		\\SLUG\ADMIN$         	IPC Service ()
		\\SLUG\IPC$           	IPC Service ()
		\\SLUG\ben            	Share for Ben
		\\SLUG\platypus       	Share for Grace
		\\SLUG\DISK 1         	For everyone
		\\SLUG\ADMIN 1        	
	\\CLIO           		Clio
		\\CLIO\Pharos Color Printers	Xerox Phaser 6300N
		\\CLIO\Pharos B&W Printers	Lexmark T632
		\\CLIO\Brother MFC-440CN	Brother MFC-440CN CUPS v1.1
		\\CLIO\Ben’s Printer	Epson Stylus Photo R260 - CUPS+Gutenprint v5.2.3
		\\CLIO\ADMIN$         	IPC Service (Clio)
		\\CLIO\IPC$           	IPC Service (Clio)
grace@hope:~$ 

```

---

### Post by bab1 on 2011-04-12
> **graceful1 said:**
> Yes. I am able to reach it on my MacBook Pro.



Yes. Places > Network > Windows Network > MOONBASE > SLUG
This reveals four shares: ADMIN 1, ben, DISK 1, and platypus.

Here's the curious thing. Double-clicking on ADMIN 1 & ben works; double-clicking on DISK 1 and platypus does not and returns the DBus error described in an earlier post.

I am able to reach platypus (and the other three shares) using my Mac.


Actually, I had already replaced the semicolon on the advice of the friend who was helping me configure my router (so that I could ping SLUG).

I think it has to do with how you made the shares.  If you can see the shares then we have cured your initial problem.  It was a DNS problem and not a Samba problem.

How did you make the share platypus?  What restrictions does it have?

---

### Post by graceful1 on 2011-04-12
> **bab1 said:**
> I think it has to do with how you made the shares.  If you can see the shares then we have cured your initial problem.  It was a DNS problem and not a Samba problem.

Ahhh, I see. 8-)

> 
How did you make the share platypus?  What restrictions does it have?

Hmmm... Since we set all this up 5 years ago, I will have to ask Ben, who has gone to bed. In an earlier post I put the output of another smbtree command. Maybe that will tell you something?

But now, here's another funny thing. On a whim I removed the semicolon from this line in my smb.conf file (with the protocols in the order dictated by Morbius1)
```
name resolve order = bcast host lmhosts wins
```

I restarted samba. Couldn't open platypus. Could open ben. Closed ben. Tried platypus again. It didn't work. Out of frustration, tried it a second time. It worked!!! Problem solved??

Hmmm... So I closed platypus again and restarted samba. Opened ben and closed it. Tried platypus again, three times, couldn't open it this time. So it is very inconsistent and intermittent here, but I don't know what is going on.

---

### Post by Morbius1 on 2011-04-13
Does the "ben" share prompt for a user name and passwrd?

Does the "platypus" share prompt for a username and password?

Please post the output of the following command so we can see how your Ubuntu machine is currently set up:
```
testparm -s
```It's possible ( although it would also affect guest accessible shares too ) that you have your password unencrypted. If "testparm -s" lists the following in it's output:
> encrypt passwords = No [COLOR=Blue]*It could also say "false"*[/COLOR]

Change it to Yes.

And restart samba. Please note that after restarting samba wait a few minutes for the network to settle down a bit before trying to access the remote share.

---

### Post by graceful1 on 2011-04-13
Here is the output for testparm -s

```

grace@hope:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = MOONBASE
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	lanman auth = Yes
	client lanman auth = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
grace@hope:~$ 


```

I don't see the line that you are talking about.

I went into the slug, and I can see that the shares are set up with usernames and passwords, but for some reason it doesn't seem to prompt for them when I use the bookmarks. (It does ask for them when I connect with my Mac, however.)

---

### Post by Morbius1 on 2011-04-14
> **graceful1 said:**
> I went into the slug, and I can see that the shares are set up with usernames and passwords, [COLOR=Blue]but for some reason it doesn't seem to prompt for them when I use the bookmarks[/COLOR]. (It does ask for them when I connect with my Mac, however.)

I'll be darned - I remember this problem. There is a very old bug - like Karmic vintage - that should have been fixed long ago. It has to do with passwords saved when you access remote shares. This wasn't a samba problem it was a Nautilus problem as I recall.

Is it possible that somewhere along the line when accessing the NAS share and prompted for credentials that you selected "Remember Forever". If so this may be the problem. The bug will cause the connection to fail with this error message:
> DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)That's the error message you received.

Like I said this should have been fixed already as the only workaround was to delete the saved password:
System > Preferences > Passwords and Encryption Keys > You should see something in there related to the NAS. Delete that password and try your bookmark again and see if you can connect.

I will try to find the original bug report on this.

[COLOR=Blue]EDIT[/COLOR]: found it: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/463267](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/463267)

I should note that this didn't happen to everyone - it never happened to me for example - so there's probably a confluence of events necessary for this to show up.

---

### Post by iiiears on 2011-04-14
I have been following along. - you fixed two for the price of one!

Thank You!
Thank You!
Thank You!

---

### Post by Morbius1 on 2011-04-14
> **iiiears said:**
> I have been following along. - you fixed two for the price of one!

Thank You!
Thank You!
Thank You!
Are you referring to what I just posted? If so what version of Ubuntu are you using?

---

### Post by graceful1 on 2011-04-15
> **Morbius1 said:**
> This may be the wildest guess I've ever made in a forum.

[...]
Add these lines to the [global] section of smb.conf:
```
client lanman auth = Yes 
lanman auth = Yes 
```
[...]
Give it  a shot - what have you got to lose ;).

I want to tell you that yes, those lines are necessary. Meant to say this earlier. Without it, samba does not work in our network. So, thanks and good guess!! ;)

This didn't completely solve the problem, as you can see from the rest of this thread, but it turned out to be essential.

---

### Post by graceful1 on 2011-04-15
> **Morbius1 said:**
> I'll be darned - I remember this problem. There is a very old bug - like Karmic vintage - that should have been fixed long ago. It has to do with passwords saved when you access remote shares. This wasn't a samba problem it was a Nautilus problem as I recall.

Is it possible that somewhere along the line when accessing the NAS share and prompted for credentials that you selected "Remember Forever". If so this may be the problem. The bug will cause the connection to fail with this error message:
That's the error message you received.

Ahhh!!! :o
I think we might have been using Intrepid Ibex or even Hardy Heron when we set up this network some 4 or 5 years ago.

> 
Like I said this should have been fixed already as the only workaround was to delete the saved password:
System > Preferences > Passwords and Encryption Keys > You should see something in there related to the NAS. Delete that password and try your bookmark again and see if you can connect.


Yes!! Hallelujah!!! It works consistently (so far)! THANK YOU!!!
\\:D/ \\:D/

So... this bug has never been fixed yet? So, I should not ask it to remember the password forever?

---

### Post by cejack on 2011-04-16
Thanks for the information.  

The part about typing in the IP address into Nautilus works for me without all the file editing crap.  

Really a pain.  

You would think that an NSLU2 running SAMBA would be seamless with Ubuntu SAMBA.  

Alas, in this case, my Win 7 machines are more adept and less hassle at hooking up to NSLU2 than my Ubuntu boxes...

BTW, I get an error of something like "Unable to Mount Location - Failed to retrieve Share List from the Server".  Using 10.10.  

Still happens when I go to "Network" in Nautilus file manager.  This has got to be an easy fix.  Weird thing was I know this worked when I originally installed 10.04 and 10.10 and then all of a sudden one day it just quit working.  I'll try to the SMB.conf edit when I have a chance.

---

### Post by Morbius1 on 2011-04-16
@cejack > You would think that an NSLU2 running SAMBA would be seamless with Ubuntu SAMBA. The problem is the NSLU2 is using a very old version of Samba and was created to be backward compatible to Windows98. Prior to the WinNT branch of Windows ( i.e., WinNT, Win2K, WinXP, Vista, ... ) passwords were handled by "lanman" on Windows. The modern samba client doesn't expect to be in a network that relies on lanman to encrypt passwords so it's disabled by default. But Samba never throws anything out so it's always available as an option:
```
client lanman auth = Yes 
lanman auth = Yes
```> The part about typing in the IP address into Nautilus works for me without all the file editing crap. 
BTW, I get an error of something like "Unable to Mount Location - Failed to retrieve Share List from the Server". Using 10.10. 
All of that is related to the inability of the network itself to translate a host name to an ip address. It's really not a Samba issue it's a network ( local DNS ) issue. There's a whole bunch of Howto's with some pretty questionable fixes for this and mine may be just as questionable but changing the order of netbios resolution seems to work in a surprising number of cases. 

By default samba will use the following mechanism to convert names to ip addresses:
> name resolve order = lmhosts host wins bcast Samba will go through each one in succession to try to resolve the name - lmhost fails it goes to host, host fails it goes to wins, that fails it goes to bcast. lmhost and host are not configured or are empty by default so those are passed through quickly. The problem appears to be "wins". What should happen is that it will look for a WINS server in the network and if it can't find one it moves to bcast. This is where it seems to get stuck. Perhaps it's related to something the ISP does called "DNS redirection" but in order to find a WINS server it will attempt to go outside the LAN to try to find one and stall.

What I have been suggesting is that you change the order to put bcast first - or at least before wins because bcast ( broadcast ) is the only mechanism that is functional by default:
```
name resolve order = bcast host lmhosts wins
```@graceful1, The thing with "remember forever" I don't quite understand. It's not clear to me if this problem is with Samba, Gnome, gvfs, Nautilus, or Keyring. The only workaround at the moment is to delete the password.

---

### Post by graceful1 on 2011-04-17
> **Morbius1 said:**
> @cejack The problem is the NSLU2 is using a very old version of Samba and was created to be backward compatible to Windows98. Prior to the WinNT branch of Windows ( i.e., WinNT, Win2K, WinXP, Vista, ... ) passwords were handled by "lanman" on Windows. The modern samba client doesn't expect to be in a network that relies on lanman to encrypt passwords so it's disabled by default. But Samba never throws anything out so it's always available as an option:
```
client lanman auth = Yes 
lanman auth = Yes
```All of that is related to the inability of the network itself to translate a host name to an ip address. It's really not a Samba issue it's a network ( local DNS ) issue. There's a whole bunch of Howto's with some pretty questionable fixes for this and mine may be just as questionable but changing the order of netbios resolution seems to work in a surprising number of cases. 

The lanman lines were a necessity, as I've mentioned before, but the reordering did not work for me. As far as getting the LAN to translate host name to IP address (which was just one piece of my problem), that was solved (with Ben's and BAB1's help -- THANKS :D) by enabling the router to do DNS. We saw that it was trying to use my ISP's DNS to resolve the name SLUG. So, it could well be a matter of reconfiguring your router (which I suppose is beyond the scope of an Ubuntu forum).

> 
@graceful1, The thing with "remember forever" I don't quite understand. It's not clear to me if this problem is with Samba, Gnome, gvfs, Nautilus, or Keyring. The only workaround at the moment is to delete the password.
Wow, that is a number of possibilities. The bug report you linked us too earlier made it sound like it had been fixed, but evidently not.

---

