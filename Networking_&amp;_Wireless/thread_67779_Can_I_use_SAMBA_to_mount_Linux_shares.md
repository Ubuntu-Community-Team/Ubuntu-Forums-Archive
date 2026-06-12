---
title: "Can I use SAMBA to mount Linux shares?"
date: 2005-09-21
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2005-09-21
I am still struggling to set up my home network in the most efficient way. I've got a laptop with Ubuntu and a desktop with Ubuntu and WindowsXP. I wonder if I can use Samba to mount Linux shares like I do with Windows shares?

---

### Post by MrCheese on 2005-09-21
[QUOTE=foxy123]I am still struggling to set up my home network in the most efficient way. I've got a laptop with Ubuntu and a desktop with Ubuntu and WindowsXP. I wonder if I can use Samba to mount Linux shares like I do with Windows shares?[/QUOTE]

no problem - just do 

mount -t smbfs {samba share} {mountpoint}

Note that mount -t smbfs uses smbmount to do the actual mount.

---

### Post by foxy123 on 2005-09-21
[QUOTE=MrCheese]no problem - just do 

mount -t smbfs {samba share} {mountpoint}

Note that mount -t smbfs uses smbmount to do the actual mount.[/QUOTE]
thanks for the answer, but I've got:
```
$ sudo mount -t smbfs //10.0.0.11/WindowsD /media/ddrive
Password:
9475: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
```
though I can connect using xfsamba...

---

