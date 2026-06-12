---
title: "nsswitch.conf WINS Configuration Conflicts with Samba"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by korbeeck on 2008-10-27
[FONT="Courier New"]Smbclient[/FONT] worked fluently to create tar compatible backups of all files on an SMB/CIFS share. For which I used an *Ubuntu 8.04 LTS Server Edition* configuration with LAMP, *OpenSSH*, *Samba* and *BackupPC* packages installed.

 Testing with [FONT="Courier New"]smbclient \\\\win-pc\\share -U administrator -d 3[/FONT] (debugging level 3) returns:

```
(...)
name_resolve_bcast: Attempting broadcast lookup for name win-pc<0x20>
Got a positive name query response from 192.168.1.61 ( 192.168.80.1 192.168.40.1 192.168.1.61 )
Connecting to 192.168.1.61 at port 445
Password: ******
Doing spnego session setup (blob length=111)
(...)
Domain=[***] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
dos_clean_name []
unix_clean_name []
smb: \> 
```

 Although, and here comes the problem, when I add WINS hostname resolution to the native methods used by the UNIX system, controlled by [FONT="Courier New"]/etc/nsswitch.conf[/FONT] (e.g. [FONT="Courier New"]hosts: files wins dns[/FONT]), *BackupPC* encounters errors ("Got fatal error during xfer (No files dumped for share share)") during tar backups of *Samba* shares.

 I added [FONT="Courier New"]wins[/FONT] to [FONT="Courier New"]/etc/nsswitch.conf[/FONT] in the first place to make commands like [FONT="Courier New"]ping win-pc[/FONT] and [FONT="Courier New"]ssh ubuntu-pc[/FONT] work.

 Testing with [FONT="Courier New"]smbclient \\\\win-pc\\share -U administrator -d 3[/FONT] now _only_ returns:

```
(...)
resolve_hosts: Attempting host lookup for name win-pc<0x20>
Password: ******
smb: \> 
```

 **Workaround:** removing [FONT="Courier New"]hosts[/FONT] from *Samba*'s [FONT="Courier New"]name resolution order[/FONT] setting in [FONT="Courier New"]/etc/samba/smb.conf[/FONT] seems to solve the problem, but is in my opinion not _the right_ solution.

---

