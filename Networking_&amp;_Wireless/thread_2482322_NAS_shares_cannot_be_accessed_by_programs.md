---
title: "NAS shares cannot be accessed by programs"
date: 2022-12-28
forum: Networking &amp; Wireless
---

### Post by peter-morawetz on 2022-12-28
Hi everybody,

I'm using Ubuntu quite some time now, and use a Synology NAS for my files. I managed to mount and use the MAS shares properly with Ubuntu 20.04. However, after upgrading to Ubuntu 22.04, I have problems accessing my NAS shares. I can access them through the file explorer, as well as e.g. from Libre Office. But for whatever reason, other programs (Digikam, FreeCAD, ...) cannot access the shares.

There are four of them, all mounted in the same way:

```
//<IP-adress>/homes /home/peter/NAS_Dateien cifs username=morawepe,password=<PWD>,uid=1000,gid=1000,vers=1.0 0 0
//<IP-adress>/photo /home/peter/NAS_Fotos cifs username=morawepe,password=<PWD>,uid=1000,gid=1000,vers=1.0 0 0
//<IP-adress>/video /home/peter/NAS_Videos cifs username=morawepe,password=<PWD>,uid=1000,gid=1000,vers=1.0 0 0
//<IP-adress>/music /home/peter/NAS_Musik cifs username=morawepe,password=<PWD>,uid=1000,gid=1000,vers=1.0 0 0

```

FIrst, it is strange to see them having different settings despite beeing mounted in the exact same way:

```
drwxrwxrwx  9 root   root      0 Dez 25 15:13 NAS_Dateien
drwxrwxrwx 42 138862 138862    0 Dez 25 15:13 NAS_Fotos
drwxrwxrwx  6 root   root      0 Dez 25 15:13 NAS_Musik
drwxrwxrwx 10 root   root      0 Dez 25 15:13 NAS_Videos

```

Second, I guess the access problem with different programs comes from how these programs access the NAS, but I'm clueless how to find out what to adjust in oder to have access to my NAS shares through this programs.


ANy help is higly appreciated!

Thanks

---

### Post by Morbius1 on 2022-12-28
Looks like your shares are not being mounted.

cifs is controlled by the Linux kernel

Kernel version 5.15 in Ubuntu 22.04 removed SMBv1 ( vers=1.0 ) as an option - actually it's the ntlm security setting associated with vers=1.0.

cifs will automatically negotiate with the server ( NAS ) the best smb dialect to use starting with SMB3 down to SMB2.1 so either remove the **vers=1.0** setting and let cifs do it's thing. Or set it to **vers=2.0**.

Of course the NAS would have to be changed to accept a smb version higher than SMB1 if that is what it's set to now.

---

### Post by peter-morawetz on 2022-12-28
Thanks, changed to vers. 2.0, it now works for most of the programs. Except Digikam, which still refuses to recognise the content of the share, but I'm a step further - I can browse the folder structure of the NAS .. I guess that is a Digikam-spcific topic, as all other programs (so far) have access now.

Thanks a lot!
CHeers

---

### Post by Morbius1 on 2022-12-28
I think in Ubuntu Digikam is a snap program not a classic deb-like install. snaps have different degrees of isolation as to what they can access - like network mounts.

Sorry, I have been successful so far in not needing them so I can't help you with snaps.

---

