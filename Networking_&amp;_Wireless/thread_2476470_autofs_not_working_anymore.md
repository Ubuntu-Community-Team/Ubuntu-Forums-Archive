---
title: "autofs not working anymore"
date: 2022-06-27
forum: Networking &amp; Wireless
---

### Post by alain.roger on 2022-06-27
Hi,

It's now 2 or 3 weeks my computer seems to not run autofs services.
I'm trying to map QNAP shared folders and to make them accessible to my ubuntu 21.10 computer.

Here is what my auto.misc is:
```
qnap-dynamic-data        -fstype=nfs,rw        qnap:/dynamic-data
qnap-static-data        -fstype=nfs,rw        qnap:/static-data
```

and in my auto.master I added a line:
```
/misc /etc/auto.misc --ghost,--timeout=30
```

autofs service is running:
```
[FONT=monospace][COLOR=#54ff54]**&#9679;**[/COLOR][COLOR=#000000] autofs.service - Automounts filesystems on demand [/COLOR]
     Loaded: loaded (/lib/systemd/system/autofs.service; enabled; vendor preset: enabled) 
     Active: [COLOR=#54ff54]**active (running)**[/COLOR][COLOR=#000000] since Mon 2022-06-27 15:01:59 CEST; 42min ago [/COLOR]
       Docs: man:autofs(8) 
    Process: 37959 ExecStart=/usr/sbin/automount $OPTIONS --pid-file /var/run/autofs.pid (code=exited, status=0/SUCCESS) 
   Main PID: 37960 (automount) 
      Tasks: 4 (limit: 38315) 
     Memory: 1.3M 
        CPU: 14ms 
     CGroup: /system.slice/autofs.service 
             &#9492;&#9472;37960 /usr/sbin/automount --pid-file /var/run/autofs.pid 

juin 27 15:01:59 PC0001 systemd[1]: Starting Automounts filesystems on demand... 
juin 27 15:01:59 PC0001 systemd[1]: Started Automounts filesystems on demand.[/FONT]
```

However while this was working before, now it does not mount any shared folders.
What's happening ?

Even if I write a dumb command line or sentence in /etc/auto.master file, it seems the master file is not read at all as there is no error raised in logs.
thx

---

### Post by TheFu on 2022-06-27
21.10 support ends in a few weeks. **The system has to be moved to 22.04 ASAP to retain support.**

I think QNAP many not support NFSv4.2. I vaguely recall a fix for NFS by specifying NFS v4.0 in the client-side mount options being the fix for some NAS devices, but I don't recall if QNAP is one or not.  The option would be "vers=4.0".  If that doesn't work, perhaps NFSv4 isn't supported, so try using  "vers=3" as the option.  Version 4.2 adds some performance enhancements, but if those aren't supported by the QNAP, what can we do?

I think the issue isn't with autofs, rather it is with NFS support on QNAP not supporting the current standard version.

You can use the **mount** command without any options to see the mounts and options.
```
$ mount | grep D1
istar:/d/D1 on /d/D1 type nfs4 (rw,relatime,**vers=4.2**,rsize=1048576,wsize=1048576,namlen=255,hard,proto=tcp,nconnect=4,timeo=600,retrans=2,sec=sys,clientaddr=172.22.22.3,local_lock=none,addr=172.22.22.20)
```
I don't set most of those. Here's my auto.nfs file:
```
/d/D1 -fstype=nfs,nconnect=4,proto=tcp,rw,async  istar:/d/D1
```

---

