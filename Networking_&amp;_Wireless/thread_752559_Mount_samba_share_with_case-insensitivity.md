---
title: "Mount samba share with case-insensitivity"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by jeffk on 2008-04-11
UPDATED with additional smb.conf and fstab config, problem now seems to be wine interaction with mounted cifs share.

Having followed dmizer's excellent [Mount samba shares with utf8 encoding using cifs]("http://ubuntuforums.org/showthread.php?t=288534"), I now have cifs mounts at /media/sharename and at a point nested under ~.wine, for legacy application compatibility.

Unfortunately, I must run some olde Windows applications under Wine, and this application in particular is looking for an uppercase FOO.DBF, when the filename as written by the installer is foo.dbf.

There are mixed-case files galore, and I think the more practical option is to configure Samba to act case-insensitively.

It has done so with Windows clients to the Samba server, but now with our first Linux client, it is case-sensitive. Do I need to do something in the mount to have case-insensitivity?

with fstab entries like (UPDATE 'nocase' added below):
```
//server/acme/app    /home/joe/.wine/drive_c/App    cifs    guest,rw,iocharset=utf8,nocase,file_mode=0777,dir_mode=0777    0    0
```
And /etc/smb.conf definitions like (UPDATE 'case sensitive = no' added)
```
[acme]
    comment = Acme Server Share
    writable = yes
    locking = no
    path = /path/to/acme
    public = yes
    guest ok = yes
    browsable = yes
    create mask = 0777
    directory mask = 0777
    case sensitive = no
```
and all files under /path/to/home owned by nobody:nogroup, chmod 777.

I do realize that's a wide-open share, but the plan is to get these old apps working first, then apply proper practices.

After the aforementioned updates, I can get linux to search files case-insensitively on these mounts:
```
$ ls /media/acme/app/FOO.EXE
FOO.EXE
$ ls /media/acme/app/foo.exe
foo.exe
```
However, Wine isn't doing the same thing, despite the fact that wine can and does behave case-insensitively on a local search.

Should I be using an nfs share and mount instead?

Thanks for any ideas.

---

