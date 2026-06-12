---
title: "how do you translate mount commands to fstab"
date: 2014-07-06
forum: Networking &amp; Wireless
---

### Post by uwe-bungto on 2014-07-06
Translate mount to fstab

This works 
sudo mount -t cifs -o username=USERNAME,password=PASSWORD   //192.168.0.14/Volume_2   /mnt/D-link
    
when I try to automount with fstab

192.168.0.14:/Volume_2    /mnt/D-link    -t cifs -o username=USERNAME,password=PASSWORD    0  0

it does not mount

What am I doing wrong.

Thanks

Paul

---

### Post by Toz on 2014-07-06
You're missing the //s and you need to drop the colon, -t and -o. Try this:
```
//192.168.0.14/Volume_2     /mnt/D-link     cifs     username=USERNAME,password=PASSWORD     0     0
```

Resource: [https://wiki.ubuntu.com/MountWindowsSharesPermanently]("https://wiki.ubuntu.com/MountWindowsSharesPermanently")

---

### Post by uwe-bungto on 2014-07-10
> **Toz said:**
> You're missing the //s and you need to drop the colon, -t and -o. Try this:
```
//192.168.0.14/Volume_2     /mnt/D-link     cifs     username=USERNAME,password=PASSWORD     0     0
```

Resource: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Thank you The D-link NAS now works using CIFS. I couldn't get it to work properly since NFS4 was introduced. I think it is using NFS3 or maybe even 2

---

