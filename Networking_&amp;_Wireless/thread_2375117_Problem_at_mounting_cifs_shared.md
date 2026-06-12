---
title: "Problem at mounting cifs shared"
date: 2017-10-22
forum: Networking &amp; Wireless
---

### Post by luca-barazzuol on 2017-10-22
Hi,

I've just installed U17.10 and I'm experiencing a weird error at mounting a cifs shared hosted on a NSA325 NAS.

I had mounted these shared without problems since several years on previous Ubuntu version.

The weirdest thing is that via Nautilus I can mount the shared folders with no problem.

Here is my fastab:
```

...
//192.168.1.160/BACKUP    /mnt/BACKUP    cifs iocharset=utf8,credentials=/.smbcredentials,uid=1000,nofail 0 0 
...

```
When I mount (sudo mount -a) I got this error:
```
$ sudo mount -v -a
mount.cifs kernel mount options: ip=192.168.1.160,unc=\\192.168.1.160\BACKUP,iocharset=utf8,uid=1000,user=luke,pass=********
mount error(112): Host is down
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

Syslog:
```

CIFS VFS: cifs_mount failed w/return code = -112


```

the 445 port is open:

```
$ nmap -p 445 192.168.1.160 -P0
Starting Nmap 7.60 ( https://nmap.org ) at 2017-10-22 12:34 CEST
Nmap scan report for computer.station (192.168.1.160)
Host is up (0.00027s latency).

PORT    STATE SERVICE
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds
```


?

LK

---

### Post by Morbius1 on 2017-10-22
Just a guess at this point but I think it may be a Linux kernel issue.

By default cifs mounts use the SMB1 dialect to access a samba share. This changed with Linux kernel 4.13 and that is the kernel Ubuntu 17.10 uses. It changed the default to use SMB3. THe "host is down" error message is indicative of this SMB dialect difference.

Try changing your cifs mount to this:
```
//192.168.1.160/BACKUP    /mnt/BACKUP    cifs iocharset=utf8,credentials=/.smbcredentials,uid=1000,nofail,vers=1.0 0 0 
```
[COLOR=#0000cd]**vers=1.0**[/COLOR] changes it back to the old default.

---

### Post by luca-barazzuol on 2017-10-22
Yes...it works! 
I had tried with vers=2.0, but it didn't work.

Thanks so much!

LK

---

