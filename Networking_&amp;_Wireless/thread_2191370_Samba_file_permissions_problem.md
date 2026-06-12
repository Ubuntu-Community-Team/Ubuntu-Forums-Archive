---
title: "Samba file permissions problem"
date: 2013-12-02
forum: Networking &amp; Wireless
---

### Post by c-m on 2013-12-02
I've got an ubuntu machine running samba and sharing a usb HDD with Windows and OSX.

The problem i'm having is that none of the other machines can write to the drive.

Being a usb drive it's auto mounted at media/myusername/SAMSUNG

Here's the relevant smb.conf extract

```
[SAMSUNG]
	path = /media/myusername/SAMSUNG
	valid users = myusername
	write list = myusername
	admin users = myusername
	writeable = Yes
	available = yes
	readonly = no 
   	inherit permissions = yes
```

---

### Post by c-m on 2013-12-04
Still not fixed this. It's driving me crazy.

Even tried the following

```
create mask = 0777 
force create mode = 0777 
directory mask = 0777 
force directory mode = 0777
```

But it still doesn't give me write permissions

---

### Post by c-m on 2013-12-17
Arggggghhhh.

This is still on going.

I found that Ubuntu automatically mounting usb drives at /media/$user is a problem as it means only that user can write to it. To combat this I changed the default auto-mount location to /media just like in older versions of Ubuntu. The problem here is only root and the logged in user has permissions.

So I instead I mounted the drive via fstab
```
UUID="CE4C1C244C1C09BB" /media/SAMSUNG ntfs-3g rw,uid=1000,gid=1000,fmask=000,dmask=000 0 0
```

With those permissions everyone should be able to write to the drive, but still my samba user cannot.

Here are my samba permissions

```
[SAMSUNG]
	path = /media/SAMSUNG
	valid users = myusername
	write list = myusername
	admin users = myusername
	writeable = yes
	available = yes
	readonly = no
create mask = 0777 
force create mode = 0777 
directory mask = 0777 
force directory mode = 0777
```

---

### Post by Morbius1 on 2013-12-17
This is a curious symptom since if the NTFS partition is mounting to /media/myusername/SAMSUNG then this should have worked:
> [SAMSUNG]
    path = /media/myusername/SAMSUNG
    valid users = myusername
    write list = myusername
    admin users = myusername
    writeable = Yes
    available = yes
    readonly = no 
       inherit permissions = yes
Actually something much simpler should have worked:
> [SAMSUNG]
    path = /media/myusername/SAMSUNG
    valid users = myusername
    writeable = Yes
    available = yes
Um.....check to see if myusername's uid is consistent between Linux and Samba:
This command should show you your uid number:
```
id myusername
```
This command should show you the uid number in the samba password database:
```
sudo pdbedit -w -L | grep myusername
```
If they are different - and I can't imaging why or how they could be different - change your share definition to this:
> [SAMSUNG]
    path = /media/myusername/SAMSUNG
    valid users = myusername
    [COLOR=#0000cd]**force user = myusername**[/COLOR]
    writeable = Yes
    available = yes
Then restart smbd

---

### Post by c-m on 2013-12-17
They are both "1000"

Here's the output of the pdbedit command:

```
myusername:1000:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:3F9EA2B274FEB8211BBCA96477BA77A4:[U          ]:LCT-5283506A:

```

---

### Post by Morbius1 on 2013-12-17
Do you have a username map file?

It's usually at /etc/samba/smbusers. Look at that file and see if "myusername" is being mapped to some other user name.

---

### Post by c-m on 2013-12-17
Yes, it's got 

# Unix_name = SMB_Name1 SMB_Name2 ...
root = administrator
nobody = guest smbguest pcguest
myusername = myusername

Perhaps the thing to do is turn off all security and start from there.

---

### Post by c-m on 2014-01-11
Come one guys. This is still going on is causing me a big problem.

Does anyone have any idea?

Thanks

---

