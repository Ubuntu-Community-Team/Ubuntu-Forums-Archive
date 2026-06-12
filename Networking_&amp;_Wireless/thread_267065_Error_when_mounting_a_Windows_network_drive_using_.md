---
title: "Error when mounting a Windows network drive using samba"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by Nickb-k on 2006-09-28
Hello,

This is probably a trivial problem:  I am trying to use Samba to let me mount windows network drives on an Ubuntu Dapper Server installation that I am using as a desktop.

Using:

```
testparm
```

my smb.conf seems to be ok.

Using ```
smbclient -L GM.local -U username -p
```

Gives me a full listing of all network drives.  So now I try this:

```
sudo mount -t smbfs -o username=username \ //GM.local/DC4 /mnt/win_share/
```

which leads to this error:

```

mount: wrong fs type, bad option, bad superblock on  //GM.local/DC4,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Please help!  I work in a total Windows shop - I'm trying to demonstrate the power of Linux!

Thanks in advance

Nick

---

### Post by Jussi Kukkonen on 2006-09-28
smbfs is not recognized as a filesystem it seems. Do you have the smbfs package installed?

---

### Post by Nickb-k on 2006-09-28
Thank - I didnt have smbfs installed.

Now I have it installed, I get this error when mounting:

```

21631: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

```

But I think this is more of a problem at my end.

Thanks for the help

---

### Post by wieman01 on 2006-09-28
In order to fully share network drives with Windows your Linux machine needs to be part of the same domain. Hence your smb.conf should include something like this:

_/etc/samba/smb.conf:_
```
workgroup = [COLOR="Red"]WORKGROUP[/COLOR]
security = share

[[COLOR="Red"]your_share_name[/COLOR]]
comment = [COLOR="Red"]my_comment[/COLOR]
writable = no
path = /home/[COLOR="Red"]your_user[/COLOR]
public = yes

```
Then restart Samba...

[COLOR="Blue"]N.B.: That's what I remember from the good old days when I HAD Windows.[/COLOR]

---

### Post by Nickb-k on 2006-09-28
Ok, so now I have:

```

nick@nick:$ sudo mount -t smbfs -o username=username \//GM.local/DC4 /mnt/win_share/
cli_negprot: SMB signing is mandatory and we have disabled it.
23500: protocol negotiation failed
SMB connection failed

```

My smb.conf file includes: 

```
client signing = yes
```

but that didnt help either.

Thanks again,

Nick

---

### Post by Jussi Kukkonen on 2006-09-28
It seems the demonstration of the power of Linux failed: smbfs doesn't seem to support smb signing...

[http://lists.samba.org/archive/samba/2003-December/076388.html](http://lists.samba.org/archive/samba/2003-December/076388.html)

---

### Post by Nickb-k on 2006-09-29
I'm trying to connect to a win2k network though - smb only fails with win 2k3.

---

### Post by Jussi Kukkonen on 2006-09-29
I'm not at all sure that the post I referred to meant that it would only fail with 2k3... Or do you mean you have information that says smbfs supports signing?

Try with something else than smbfs, like the smbclient. Then you'll know if the problem is with smbfs or samba in general.

---

