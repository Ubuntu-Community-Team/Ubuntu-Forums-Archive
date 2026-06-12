---
title: "Active Directory drive mounting - Don't know what I don't know"
date: 2024-04-22
forum: Networking &amp; Wireless
---

### Post by adwatkin19 on 2024-04-22
Hi all

I am building a small tester network with some students, We have a Windows Server AD setup, we have used SSSD to join the AD and authenticate the user from Ubuntu, this works perfect BUT

When they log into windows, they get their own personal directory mounted (home drive)... How can I replicate this in Ubuntu? SO regardless of OS their documents follow them around.

I have "some" knowledge, but dont know what I dont know and lack the terms needed to describe it better. So my googling has largely been fruitless. 

Please help my students and I figure this out.

---

### Post by TheFu on 2024-04-22
**autofs**  BTW, HOME directories need to use native Linux file systems.  CIFS mounts won't work. 

However, with Ubuntu, mounting HOME directories over NFS will break snap packages, so you'll need to read up about that problem.  Non-snap distros don't have any issues with it and prior to Canonical forcing snap packages onto everyone, Ubuntu didn't have any issues either.

If you like, you can mount any CIFS data directories elsewhere and create custom XDG settings for where documents are located to that other location, which can be CIFS mounted, probably under /media/ or /mnt/.  Those are the only 1 places that remote storage can be placed and still work with snap packages. Every snap package will be to be configured locally to allow remote-media (I don't remember the exact setting and some packages don't support it at all). There is no way to alter a snap package NOT to mandate which directory locations are allowed. Canonical hard-coded the locations, it seems.  Requests for local control of these locations or disabling them completely since 2017 have gone nowhere.  1 workaround was offered, but it would break lots of other infrastructure for non-Ubuntu systems, so it isn't usually workable.

---

### Post by Morbius1 on 2024-04-22
There's a good chance I am misunderstanding your use case but for a normal standalone samba server it looks like what you want is a [homes] share.

It looks something like this in /etc/samba/smb.conf:

```
[homes]
comment = Home Directories
valid users = %S
read only = No
create mask = 0700
directory mask = 0700
browseable = No
veto files = /*.*/
```

That will create a share of the Linux user's home directory - "on the fly"

It is non-browseable so the client user would have to access it by the user's name: **smb://hostname.local/morbius** in Linux or MacOS and **\\hostname.local\morbius** in Windows

The user ( morbius in this example ) would have to exist on the server and be added to the samba password database:
```
sudo smbpasswd -a morbius
```

You can either "map" the share in Windows or use a mount.cifs mount in Linux to have it done automatically.

How all of this would work within an AD / SSSD setup I have no idea.

---

### Post by TheFu on 2024-04-22
Morbius, excellent point!  I was assuming he wanted the user's HOME directories to follow them around when they were using Linux desktops, not Windows.  Seems the Windows side was already solved and that using autofs would be the method for Linux, with the restrictions of providing a native Linux file system for their HOME directories, not NTFS.  Something like: [https://arstechnica.com/civis/threads/sssd-automounting-home-dirs-from-ldap.1473586/](https://arstechnica.com/civis/threads/sssd-automounting-home-dirs-from-ldap.1473586/) and [https://sssd.io/docs/ad/ad-autofs.html](https://sssd.io/docs/ad/ad-autofs.html)  and an ubuntu-specific answer: [https://askubuntu.com/questions/1397502/auto-home-from-autofs-maps-from-active-directory-not-working](https://askubuntu.com/questions/1397502/auto-home-from-autofs-maps-from-active-directory-not-working)

If using MS-Windows, then the samba [Homes] method does work.

---

