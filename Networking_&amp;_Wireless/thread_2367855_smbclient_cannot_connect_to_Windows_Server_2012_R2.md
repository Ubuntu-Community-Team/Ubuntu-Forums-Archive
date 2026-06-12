---
title: "smbclient cannot connect to Windows Server 2012 R2"
date: 2017-08-04
forum: Networking &amp; Wireless
---

### Post by mikimotoh on 2017-08-04
[LIST]
[*]SAMBA Client: Ubuntu 14.04.5 LTS 
[*]SAMBA Server: Windows Server 2012 R2 Standard 
[/LIST]

I ran the following command ```

smbclient -d3 -L //10.2.3.111/Files -A /home/acteam/.smbcredentials
``` 
and got error **NT_STATUS_RESOURCE_NAME_NOT_FOUND** . Below is detail error message:
```

[acteam@irv-guen] - [~] - [2017-08-03 21:32:12]
[0] smbclient -d3 -L //10.2.3.111/Files -A /home/acteam/.smbcredentials     lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
WARNING: The "syslog" option is deprecated
added interface eth0 ip=10.2.3.127 bcast=10.2.3.255 netmask=255.255.255.0
Client started (version 4.3.11-Ubuntu).
Connecting to 10.2.3.111 at port 445
Doing spnego session setup (blob length=120)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
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
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
Domain=[TMGRID] OS=[Windows Server 2012 R2 Standard 9600] Server=[Windows Server 2012 R2 Standard 6.3]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        Files           Disk
        IPC$            IPC       Remote IPC
        MappedDrive     Disk
Connecting to 10.2.3.111 at port 139
Connecting to 10.2.3.111 at port 139
Connection to 10.2.3.111 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
NetBIOS over TCP disabled -- no workgroup available
```


On Windows Server side, NetBios is enabled:
 [https://i.stack.imgur.com/9hB18.gif](https://i.stack.imgur.com/9hB18.gif)

This Windows Server doesn't join any WORKGROUP. It uses Domain "tmgrid.local"
[https://i.stack.imgur.com/fXA1s.gif](https://i.stack.imgur.com/fXA1s.gif)


I've referred to the [https://ubuntuforums.org/showthread.php?t=2295552&p=13360352#post13360352](https://ubuntuforums.org/showthread.php?t=2295552&p=13360352#post13360352) , but that thread is also not resolved.

---

### Post by wildmanne39 on 2017-08-04
Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them, also people access the forum via mobile devices as well and won't want to use up their bandwidth on huge images. Use the forum's attachment facility which is accessed by clicking on the paperclip icon above the text box. If you don't see the paperclip icon, click on Go Advanced below the text box.

---

### Post by mikimotoh on 2017-08-04
I have resolved the issue by fixing **~/.smbcredentials** file.
Before, **~/.smbcredentials** file content is:
```

username=TMGRID/AppControlTeam
password=************

```
I ran `sudo mount` will cause error message
```

[acteam@irv-guen] - [~] - [2017-08-04 00:54:59]
[32] sudo mount -vvv -t cifs -o credentials=/home/acteam/.smbcredentials,sec=ntlm //10.2.3.111/Files /media/IRV-GUEN-WINF_Files
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: spec:  "//10.2.3.111/Files"
mount: node:  "/media/IRV-GUEN-WINF_Files"
mount: types: "cifs"
mount: opts:  "credentials=/home/acteam/.smbcredentials,sec=ntlm"
mount: external mount: argv[0] = "/sbin/mount.cifs"
mount: external mount: argv[1] = "//10.2.3.111/Files"
mount: external mount: argv[2] = "/media/IRV-GUEN-WINF_Files"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,credentials=/home/acteam/.smbcredentials,sec=ntlm"
mount.cifs kernel mount options: ip=10.2.3.111,unc=\\10.2.3.111\Files,sec=ntlm,user=TMGRID/AppControlTeam,pass=********
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```
The `**/var/log/syslog**` is
```

Aug  4 00:59:03 irv-guen kernel: [50881.183164] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
Aug  4 00:59:03 irv-guen kernel: [50881.183171] CIFS VFS: Send error in SessSetup = -13
Aug  4 00:59:03 irv-guen kernel: [50881.183363] CIFS VFS: cifs_mount failed w/return code = -13

```

After I inserted domain into **~/.smbcredentials** file content:
```

username=AppControlTeam
password=***********
domain=tmgrid.local

```
and ran `sudo mount` the result is
```

[acteam@irv-guen] - [~] - [2017-08-04 00:59:03]
[32] sudo mount -vv -t cifs -o credentials=/home/acteam/.smbcredentials,sec=ntlm //10.2.3.111/Files /media/IRV-GUEN-WINF_Files
domain=tmgrid.local
mount.cifs kernel mount options: ip=10.2.3.111,unc=\\10.2.3.111\Files,sec=ntlm,user=AppControlTeam,,domain=tmgrid.local,pass=********

```
Now I can browse the mounted Windows Shared Folder
```

[acteam@irv-guen] - [~] - [2017-08-04 01:02:58]
[0] l /media/IRV-GUEN-WINF_Files
total 8.0K
drwxr-xr-x 2 root root 4.0K Aug  3 02:14 .
drwxr-xr-x 5 root root 4.0K Aug  4 00:53 ..
drwxr-xr-x 2 root root    0 Jul 10 02:11 Archive
drwxr-xr-x 2 root root    0 Jul 27 04:21 ExtractedDirectory
drwxr-xr-x 2 root root    0 Aug  3 02:14 GUEN_Linux
drwxr-xr-x 2 root root    0 Aug  2 06:58 GUEN_QA
drwxr-xr-x 2 root root    0 Jul 10 02:14 PackageDirectory
drwxr-xr-x 2 root root    0 Jul 31 01:46 SamplesForQATesting

```

---

### Post by mikimotoh on 2017-08-04
I found I don't have write permission on the mounted Windows Share Folder. I added the uid=<my_linux_id> into the options of `mount`
```

[0]  sudo mount -vv -t cifs -o  credentials=/home/acteam/.smbcredentials,sec=ntlm,file_mode=0777,dir_mode=0777,uid=acteam  //10.2.3.111/Files /media/IRV-GUEN-WINF_Files
domain=tmgrid.local
mount.cifs  kernel mount options:  ip=10.2.3.111,unc=\\10.2.3.111\Files,sec=ntlm,file_mode=0777,dir_mode=0777,uid=1000,user=AppControlTeam,,domain=tmgrid.local,pass=********

```

Then I have the write permission to the Windows Share Folder. :p

---

### Post by mikimotoh on 2017-08-04
My post using the URL to [https://i.stack.imgur.com/9hB18.gif](https://i.stack.imgur.com/9hB18.gif) . My browser (Desktop Firefox) doesn't show the images, it just shows the URL.

---

