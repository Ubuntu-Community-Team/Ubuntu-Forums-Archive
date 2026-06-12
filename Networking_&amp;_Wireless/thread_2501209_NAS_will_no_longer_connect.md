---
title: "NAS will no longer connect"
date: 2024-09-27
forum: Networking &amp; Wireless
---

### Post by srutx47 on 2024-09-27
Good Morning,

First I am running a Ubuntu 24.04.1 LTS distribution and went through the full OS upgrade.  Since then there are particular issues.  

1) I have no sound for particular applications.  For the most part it works but there are certain application.. the sound is dead.  I have reinstalled to no avail.
2) and probably my BIGGEST Issue is I can NO longer attach to my NAS Drive.  I was able to connect with easy prior to the update and the two patches after.

The command I have been using (that worked) is:

```
sudo mount -t cifs //$LSIP/$SHARE /mnt/NetShare -o username=$LSUSER,password=$LSPASS,uid=$USER,file_mode=0644,vers=1.0
```

I changed the actual information with variables of course.  but in the past it worked without a glitch... now I get the ```
mount error(13): Permission deniedRefer to the mount.cifs(8) manual page (e.g. man mount.cifs) and kernel log messages (dmesg)

```

The Log shows:  ```
3138.319836] r8169 0000:01:00.0:    [ 0] RxErr                  (First)[ 3138.708238] Use of the less secure dialect vers=1.0 is not recommended unless required for access to very old servers


[ 3138.708256] CIFS: VFS: Use of the less secure dialect vers=1.0 is not recommended unless required for access to very old servers
[ 3138.708265] CIFS: enabling forceuid mount option implicitly because uid= option is specified
[ 3138.708267] CIFS: Attempting to mount //192.168.1.195/wilshare
[ 3138.708994] pcieport 0000:00:1c.0: AER: Multiple Correctable error message received from 0000:01:00.0
[ 3138.709026] r8169 0000:01:00.0: PCIe Bus Error: severity=Correctable, type=Physical Layer, (Receiver ID)
[ 3138.709030] r8169 0000:01:00.0:   device [10ec:8136] error status/mask=00000001/00006000
[ 3138.709034] r8169 0000:01:00.0:    [ 0] RxErr                  (First)
[ 3138.726213] CIFS: Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
[ 3138.726225] CIFS: VFS: \\192.168.1.195 Send error in SessSetup = -13
[ 3138.726238] CIFS: VFS: cifs_mount failed w/return code = -13



```

The only changes from when it worked until now are the upgrade and updates.  I see the error message but I cannot see what is going on.  I have even taken off the vers=1.0 syntax.. to no avail.

Any ideas?

Thanks,
Texmansru47

---

### Post by TheFu on 2024-09-27
If your NAS supports NFS, using that would be best.  Assuming you are interested.  NFS is system-to-system, not user-to-system.

CIFS is a limited protocol and really should only be used when the client is MS-Windows.

If you want a user-to-system connection protocol, you can look into sshfs, but sshfs was deprecated due to lack of an upstream project providing support.  sshfs, like CIFS, has all the problems that allowing end-users to mount storage brings.

In the Unix-world, > The power to mount is the power to destroy.
Beware of any mount method that doesn't need an administrator to setup.

---

### Post by srutx47 on 2024-09-27
I am a fan of NFS, but I this particular Buffalo NAS does not support NFS (SMB/CFIS, FTP, HTTP/HTTPS/AFP are supported).

---

### Post by srutx47 on 2024-09-27
I got the mount to work... I had to use my REDHAT syntax.

---

### Post by TheFu on 2024-09-27
> **srutx47 said:**
> I got the mount to work... I had to use my REDHAT syntax.

a) Would you care to share what "REDHAT syntax" is so others can learn too?

b) If this is solved, please use the **Thread Tools** button at the top of the page and toggle _SOLVED_ so others can find the solution that worked for you easily. This helps the community.

---

