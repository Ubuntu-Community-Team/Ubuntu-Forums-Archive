---
title: "NFS shares not accessible"
date: 2023-11-09
forum: Networking &amp; Wireless
---

### Post by rev03 on 2023-11-09
[FONT=arial][COLOR=#2C3E50]Hello,[/COLOR]
[COLOR=#2C3E50]I would like to ask you for advice.[/COLOR]
[COLOR=#2C3E50]
[/COLOR]
[COLOR=#2C3E50]_Situation:_ I have one VM with openmediavault (192.168.0.12) and second VM with Ubuntu(192.168.0.10)[/COLOR]
[COLOR=#2C3E50]_My target:_ Share few folders in OMV via NFS and then automatically mount this folders to Ubuntu.[/COLOR]
[COLOR=#2C3E50]
[/COLOR]
[COLOR=#2C3E50]In OMV I shared few folders via NFS, R/W access for user rev. From Ubuntu server, I test, that folders are visible. See below:[/COLOR]
[COLOR=#2C3E50]
[/COLOR]
```
[COLOR=#2C3E50]
rev@ubuntu:~/jellyfin$ showmount --exports 192.168.0.12
Export list for 192.168.0.12:
/export             192.168.0.0/24
/export/serialy     192.168.0.0/24
/export/ostatni-mix 192.168.0.0/24
/export/hudba       192.168.0.0/24
/export/fotky       192.168.0.0/24
/export/filmy       192.168.0.0/24[/COLOR]
```
[COLOR=#2C3E50]
[/COLOR]
[COLOR=#2C3E50]
[/COLOR]
[COLOR=#2C3E50]In client side (Ubuntu) I do as follow:[/COLOR]
[COLOR=#2C3E50]*file auto.master:*[/COLOR]
[COLOR=#2C3E50]
```
/home/rev/jellyfin /etc/auto.nfs --ghost --timeout=60
```[/COLOR]
[COLOR=#2C3E50]
[/COLOR]
[COLOR=#2C3E50]*File auto.nfs:*[/COLOR]
```
[COLOR=#2C3E50]
serialy -fstype=nfs4, rw 192.168.0.12:/export/serialy
ostatni-mix -fstype=nfs4,rw 192.168.0.12:/export/ostatni-mix
hudba -fstype=nfs4,rw 192.168.0.12:/export/hudba
fotky -fstype=nfs4,rw 192.168.0.12:/export/fotky
filmy -fstype=nfs4,rw 192.168.0.12:/export/filmy[/COLOR]
```
[COLOR=#2C3E50]
[/COLOR]
[COLOR=#2C3E50]Everithing seems perfect, until I try to open one of shared folders:[/COLOR]
[COLOR=#2C3E50]
[/COLOR]
[COLOR=#2C3E50]```

rev@ubuntu:~/jellyfin$ ls -l
ls: cannot access 'filmy': No such file or directory
ls: cannot access 'serialy': No such file or directory
ls: cannot access 'hudba': No such file or directory
ls: cannot access 'fotky': No such file or directory
ls: cannot access 'ostatni-mix': No such file or directory
total 0
d????????? ? ? ? ?            ? filmy
d????????? ? ? ? ?            ? fotky
d????????? ? ? ? ?            ? hudba
d????????? ? ? ? ?            ? ostatni-mix
d????????? ? ? ? ?            ? serialy
```[/COLOR][/FONT][COLOR=#2C3E50][FONT=Montserrat][CENTER][FONT=arial]Display More[/FONT][/CENTER]
[/FONT][/COLOR][FONT=arial]
[COLOR=#2C3E50]
[/COLOR]
[COLOR=#2C3E50]
[/COLOR]
[COLOR=#2C3E50]Do you have any idea, what I doing wrong?[/COLOR]
[COLOR=#2C3E50]
[/COLOR]
[COLOR=#2C3E50]
[/COLOR]
[COLOR=#2C3E50]Thx,[/COLOR]
[COLOR=#2C3E50]R.[/COLOR][/FONT]

---

### Post by TheFu on 2023-11-09
I've never used OMV, but assuming it is Unix-based and providing a standard NFS server, then things work exactly the same. NFS is NFS regardless of Unix platform used.

A)  Using proportional fonts defeats the usefulness of 'code' tags.  Please fix that.  Code needs to use monospaced fonts, which happens automatically, unless you screw with the fonts.  So don't do that.

B)  The line in the auto.master file doesn't begin with a '-' character, so all the mounts will be relative.  Use
```
/-      /etc/auto.nfs --timeout=60 --ghost
```

And it is a bad idea to mount any storage under an existing HOME directory. Best not to do that.  You can figure out for yourself why ... or learn the same lesson that others learned the last 40 yrs.  Your choice.
Similarly, don't share storage under a specific user's HOME. There are many, many, reasons for that too.

C) standard Unix permissions still apply over NFS, so if you can't read the mounted areas, check the permissions and parent directories permissions on both the NFS server and the clients.

So, here's what some of my client-side auto.nfs lines look like:
```
/d/D1 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D1
/d/D2 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D2
/d/D3 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D3
/d/D6 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D6
/d/D7 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D7
```

rw, and tcp are defaults at this point, but they weren't always.  When I go out of my way to ensure the NFS is mounted, the **df -Th** is:
```
Filesystem                                       Type  Size  Used Avail Use% Mounted on
istar:/d/D1                                      nfs4  3.5T  3.4T  117G  97% /d/D1
istar:/d/D2                                      nfs4  3.6T  3.5T   83G  98% /d/D2
istar:/d/D3                                      nfs4  3.6T  3.6T   36G 100% /d/D3
istar:/d/D6                                      nfs4  3.6T  2.9T  598G  83% /d/D6
istar:/d/D7                                      nfs4  3.6T  952G  2.5T  28% /d/D7
```
Note how NFSv4 is automatic, because both sides speak it.  I'm actually using NFS v4.2 client settings to get a little added performance.

You may notice that I go out of my way to force the storage on the NFS server AND all clients to be the same locations. While not required, it helps with my sanity.

There are NFS verbosity and debug modes you can enable.  I don't recall them off the top of my head, but you can look them up as easily as I can.  In general, if the UID/GID match between the NFS clients and servers, then NFS "just works."

---

### Post by rev03 on 2023-11-09
Thank you, your proposal to use relative path helped. Maybe also with combination with VM restart. Seems that just restart of autofs with command was not enough.

R.

---

### Post by TheFu on 2023-11-10
> **rev03 said:**
> Thank you, your proposal to use relative path helped. Maybe also with combination with VM restart. Seems that just restart of autofs with command was not enough.

R.

autofs is a top-level manager for the automountd process. It doesn't control the other 3 related, but not always related, network services too.  Almost always, if you restart autofs after making changes to the autofs config files, that is sufficient, provided identd and the portmapper are fine.

BTW, I suggested and showed using an absolute path, not relative.

---

