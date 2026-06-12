---
title: "fs tab mounts dropping."
date: 2015-08-13
forum: Networking &amp; Wireless
---

### Post by ulao2 on 2015-08-13
I have a few smb mounts in fstab like this 

//192.168.0.27/r$ /down_r   cifs noauto,username=administrator,password=[blahhblahh] 0 0


After a good few hours they all get dropped, folders are empty.  I can reboot or manually redo it. Is there a log I can look at?

---

### Post by bab1 on 2015-08-13
> **ulao2 said:**
> I have a few smb mounts in fstab like this 

//192.168.0.27/r$ /down_r   cifs noauto,username=administrator,password=[blahhblahh] 0 0


After a good few hours they all get dropped, folders are empty.  I can reboot or manually redo it. Is there a log I can look at?
The logs are at ```
/var/log/samba/

```

---

### Post by ulao2 on 2015-08-13
The samba.log is full of 

[2015/08/13 18:34:03.068541,  0] printing/print_cups.c:487(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL

but I dont see how the printers would be a big concern. 

log.smbd and log.nmbd are empty. 

If I try to manually run the fstab line I get No such file or directory

Is samba to blame, no recent changes in config

---

### Post by bab1 on 2015-08-13
> **ulao2 said:**
> The samba.log is full of 

[2015/08/13 18:34:03.068541,  0] printing/print_cups.c:487(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL

but I dont see how the printers would be a big concern. 

log.smbd and log.nmbd are empty. 

If I try to manually run the fstab line I get No such file or directory

Is samba to blame, no recent changes in config

Are the SMB shares unmounted ?  What do you get when you issue ```
sudo mount -a
```Did you use the proper mount syntax (sudo mount -t) when trying to manually  mount the share ?  Is the SMB server up when the shares "drop"?  Is wireless involved here?

---

### Post by ulao2 on 2015-08-13
I get
You have new mail in /var/mail/root


Never knew what that meant? Any ways it does not remount them.

---

### Post by ulao2 on 2015-08-13
I can manually mount like so

smbmount //192.168.0.27/r$ /down_r -o username=administrator,password=[blahhblahh]

this works. I can;t figure out the mount -t option. I'd need to see an example ( I could not find one online), no wireless all lan. samba works fine after reboot.

---

### Post by bab1 on 2015-08-13
> **ulao2 said:**
> I can manually mount like so

smbmount //192.168.0.27/r$ /down_r -o username=administrator,password=[blahhblahh]

this works. I can;t figure out the mount -t option. I'd need to see an example ( I could not find one online)
```
sudo mount -t cifs //192.168.0.27/r$ /down_r -o username=administrator,password=[blahhblahh]

```...if I'm not mistaken.

---

### Post by ulao2 on 2015-08-13
that also works but mount -a does nothing.

---

### Post by bab1 on 2015-08-14
> **ulao2 said:**
> that also works but mount -a does nothing.
The command is```
**[COLOR="#FF0000"]sudo[/COLOR]** mount -a
```

---

### Post by ulao2 on 2015-08-19
I started getting an error "can't allocate memory" and did this
[https://boinst.wordpress.com/2012/03/20/mount-cifs-cannot-allocate-memory-mounting-windows-share/](https://boinst.wordpress.com/2012/03/20/mount-cifs-cannot-allocate-memory-mounting-windows-share/)

So far the issue is gone.

---

