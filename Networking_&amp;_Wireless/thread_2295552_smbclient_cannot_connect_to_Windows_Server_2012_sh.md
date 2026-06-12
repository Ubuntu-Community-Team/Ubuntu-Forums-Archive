---
title: "smbclient cannot connect to Windows Server 2012 share"
date: 2015-09-19
forum: Networking &amp; Wireless
---

### Post by kyp42 on 2015-09-19
Hi all,

I'm running Ubuntu 14.04.3 LTS and I'm trying to connect via smbclient to a Windows Server 2012 share. I dual boot Windows 7 and I have no problem connecting to the share in Windows and I'm pretty certain it's an anonymous share because I do not require a username or password to read and write in the share in Windows. Moreover I recently changed my username and password in Windows and am still able to access the share without having changed anything on the Windows server side, so I'm pretty confident that the share does not care what user I am.

The command I'm running to connect is:
```
smbclient -d3 -L //10.5.4.25/Root -n FARADAY
```

I set my machine's name to FARADAY because that's my computer name in Windows 7 in case that had anything to do with it. The output I get from smbclient with debug level 3 is:
```

lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth1 ip=10.5.6.209 bcast=10.5.255.255 netmask=255.255.0.0
Client started (version 4.1.6-Ubuntu).
Enter kyp4's password: Connecting to 10.5.4.25 at port 445
Doing spnego session setup (blob length=120)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure

session setup failed: NT_STATUS_LOGON_FAILURE

```

I seem to get this NT_STATUS_LOGON_FAILURE error no matter what I do. I've read various threads here and elsewhere on the Internet but none of those suggestions have made it work. One thing I did was add the following lines to my smb.conf (which is apparently read in by smbclient even though some places say that smb.conf is only used for samba servers):
```

client ntlmv2 auth = yes
client ldap sasl wrapping = sign

```

Some threads have alluded to the fact that newer version of Windows require the use of signing and ntlmv2, though I don't entirely understand what those are. According to one thread ([http://ubuntuforums.org/showthread.php?t=2092435](http://ubuntuforums.org/showthread.php?t=2092435)) it sounds like samba may be a little buggy in the use of ntlmv2 but nothing suggested in that thread worked for me. For reference the version of smbclient I am using is the one out of the Ubuntu 14.04 repository and is version 4.1.6 so I'm not sure if it still has the bugs alluded to in the thread since the thread is a couple years old.

Note that this is at work so I don't have access to the Windows Server 2012 box to be able to make configuration changes to it. However, if I knew what changes needed to be made on that box I could probably find out who administers it and request that the changes be made. It just seems to me that since it works from my Windows 7 boot it ought to be able to work from Ubuntu without making changes to the Windows Server box.

Thanks in advance for any help, I am posting here as a last resort since other threads around the Internet have not gotten it working for me.

---

### Post by nlee2 on 2015-09-20
Did you try putting the server domain/workgroup and userid?

```
smbclient -d3 -L //10.5.4.25 -W workgroup -U userid
```

---

### Post by kyp42 on 2015-09-21
Thanks for the response! I tried adding the workgroup (which I set to be WORKGROUP, the same as it is set in my Windows 7 boot) and user (set to the same user I log in as in Windows) but it still isn't working. The new command I am running is:
```

smbclient -d3 -L //10.5.4.25/Root -n Faraday -W WORKGROUP -U kyp4

```

If I run it and enter the same password I use in Windows the output is:
```

lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth1 ip=10.5.6.209 bcast=10.5.255.255 netmask=255.255.0.0
Client started (version 4.1.6-Ubuntu).
Enter kyp4's password:
Connecting to 10.5.4.25 at port 445
Doing spnego session setup (blob length=120)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure

session setup failed: NT_STATUS_LOGON_FAILURE

```

However if I run it with no password (just pressing enter at the prompt) it is apparently able to login anonymously but still can't connect to the drive. Here is the output for that case:
```

lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth1 ip=10.5.6.209 bcast=10.5.255.255 netmask=255.255.0.0
Client started (version 4.1.6-Ubuntu).
Enter kyp4's password:
Connecting to 10.5.4.25 at port 445
Doing spnego session setup (blob length=120)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
Domain=[LAB] OS=[Windows Server 2012 R2 Essentials 9600] Server=[Windows Server 2012 R2 Essentials 6.3]
Connecting to 10.5.4.25 at port 139
Connecting to 10.5.4.25 at port 139

Anonymous login successful

    Sharename       Type      Comment
    ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Connection to 10.5.4.25 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
NetBIOS over TCP disabled -- no workgroup available

```

Note that when I connect to the share with Windows (without any problems) it is not clear too me if it is connecting anonymously or if it is providing the Windows Server with my Windows username and password. Note that either way doesn't work in Ubuntu with smbclient though.

Any other ideas?

---

### Post by bab1 on 2015-09-21
It looks to me like you have 2 problems.  The first one is this```
Error returning browse list: NT_STATUS_ACCESS_DENIED
Connection to 10.5.4.25 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
**[COLOR="#FF0000"]NetBIOS over TCP disabled -- no workgroup available[/COLOR]**
```
...enable NBT (NetBIOS over TCP) on the Windows server and try again.

The second problem of no login might be cured, but we won't know until you fix the first problem.

---

### Post by kyp42 on 2015-09-23
Well I've got bad news and good news. The bad news is that changing the  NetBIOS over TCP did not fix the issue but the good news is that I did get it solved. The pertinent error was:
```
Error returning browse list: NT_STATUS_ACCESS_DENIED
```

I spoke with the fellow who administers the Windows server and it turns out that I wasn't connecting with the correct username and password. Once I used these credentials instead of connecting anonymously everything worked perfectly and I could connect and mount the share. It wasn't clear at all though that Windows was using these credentials on the Windows boot even after I deleted the permanent share in Windows and re-created it (it never asked me for credentials and the username/password I needed were not those used to log into my Windows boot). I don't know if it was stored in the registry somewhere or what but that kind of opaqueness is one of the reasons I dislike Windows.

Thanks for your help though.

---

### Post by bab1 on 2015-09-23
How about you mark this solved then.  ;-)

---

