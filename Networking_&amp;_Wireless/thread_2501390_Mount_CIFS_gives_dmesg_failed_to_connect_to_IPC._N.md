---
title: "Mount CIFS gives dmesg failed to connect to IPC. Not able to mount"
date: 2024-10-05
forum: Networking &amp; Wireless
---

### Post by franknfurter2 on 2024-10-05
Hello,

I run flavour ubuntu studio 24.04.1 LTS with kernel  [FONT=monospace][COLOR=#000000]6.8.0-45-lowlatency on my client machine and an TrueNAS Server Version Dragonfish-24.04.2.2[/COLOR] and also an old QNAP NAS Server. With ubuntu studio I am not able to mount.cifs both NAS. With Dolphin on the Plasma GUI I am able to see the Servers and open the configured shares after entering the user credentials in a GUI popup. I am also able to save files in the shares. But when I try to mount these shares using standard options or trying with different sec and vers options, mounting does not work. Here is the dmesg output:
[/FONT]```
[FONT=monospace][COLOR=#18b218][ 2260.048886] [/COLOR][COLOR=#b26818]CIFS: [/COLOR][COLOR=#b21818]VFS: \\192.168.1.19 failed to connect to IPC (rc=-13)[/COLOR]
[COLOR=#18b218][ 2260.052792] [/COLOR][COLOR=#b26818]CIFS: [/COLOR][COLOR=#b21818]VFS: cifs_mount failed w/return code = -13[/COLOR][/FONT]
```[FONT=monospace]
I mounted using: [/FONT][FONT=monospace][COLOR=#000000] sudo mount -t cifs //192.168.1.19/Multimedia /media/cifs/Backup --verbose -o "user=<username_on_server>,password=<password_on_server>,uid=1000,gid=1000,nodfs"[/COLOR]
If I ommit the nodfs option the output is 
[/FONT]```
[FONT=monospace][COLOR=#18b218][ 3431.193992] [/COLOR][COLOR=#b26818]CIFS: [/COLOR][COLOR=#b21818]VFS: \\192.168.1.19 failed to connect to IPC (rc=-13)[/COLOR]
[COLOR=#18b218][ 3431.194002] [/COLOR][COLOR=#b26818]CIFS: [/COLOR][COLOR=#b21818]VFS: session 00000000b5ad0d70 has no tcon available for a dfs referral request[/COLOR]
[COLOR=#18b218][ 3431.198147] [/COLOR][COLOR=#b26818]CIFS: [/COLOR][COLOR=#b21818]VFS: cifs_mount failed w/return code = -13[/COLOR][/FONT]
```[FONT=monospace]

On the logs on the TrueNAS server I can see, that login has been tried as user nobody.

I also switched off Apparmor and ufw shortly at the client to test, but this does not work either.

Last I started an old Raspberry Pi just to see if Ubuntu is the problem and yes, with just given user and password option on the Raspberry I was able to mount.

So I get stuck here and so I am not able to backup my data to a NAS in an automated fashion. Can anyone help finding the reason for this and to fix?


[/FONT]

---

### Post by franknfurter2 on 2024-10-05
Hello,

after having breakfast and a good coffee I thought it is a good idea to strace the mount command to give you more details. So I did sudo strace mount ... and took a look at the output. There was a line:
```

statx(AT_FDCWD, "/sbin/mount.cifs", AT_STATX_DONT_SYNC|AT_NO_AUTOMOUNT, STATX_TYPE|STATX_MODE|STATX_INO, 0x7fff7cb46250) = -1 ENOENT (file or directory not found)
statx(AT_FDCWD, "/sbin/fs.d/mount.cifs", AT_STATX_DONT_SYNC|AT_NO_AUTOMOUNT, STATX_TYPE|STATX_MODE|STATX_INO, 0x7fff7cb46250) = -1 ENOENT (file or directory not found)
statx(AT_FDCWD, "/sbin/fs/mount.cifs", AT_STATX_DONT_SYNC|AT_NO_AUTOMOUNT, STATX_TYPE|STATX_MODE|STATX_INO, 0x7fff7cb46250) = -1 ENOENT (file or directory not found)

```

**I thought: "Is it that simple? The cifs module isn't just installed?**

So I tried to install cifs-utils via apt and was surprised, that it wasn't installed. So the main error text in dmesg was misleading. I have expected more critical messages when cifs isn't installed.

Now I am able to mount.

---

