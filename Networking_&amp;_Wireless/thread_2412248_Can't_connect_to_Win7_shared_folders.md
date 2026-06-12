---
title: "Can't connect to Win7 shared folders"
date: 2019-02-10
forum: Networking &amp; Wireless
---

### Post by jrs77 on 2019-02-10
Another one of those failed attempts to connect the shared folders on my Windows 7 machine.

I've installed samba, edited the smb.conf to include the line "client max protocol = NT1" and now I can see the Windows machines in Nautilus under Other Locations. When I try to connect to my Windows 7 shared folders it requests a username and password as expected. After entering the username and password however it just throws me back to enter the username and password again and again without connecting to my Windows 7 shared folders.

At this moment it looks pretty much impossible to solve this problem after having read through dozens of topics regarding this issue, as nothing works no matter what I try.

---

### Post by TheFu on 2019-02-10
Have you tried manually mounting?

```
sudo mount -t cifs //172.22.22.8/Data /mnt/win7ult -o credentials=/etc/samba/win7ult.credentials,iocharset=utf8,rw,sec=ntlmv2
```

The credentials file is just 2 lines:
username=thefu
password=some-really-secure-password-that-nobody-will-guess

The file permissions are root:root and 600.
Obviously, the mount point directory must already exist, the name of the shared folder must be correct and the IP address.

---

### Post by jrs77 on 2019-02-10
Found the culprit in another Forum where I asked the question. It was an Windows Update, that caused a SMB-bug.

[https://borncity.com/win/2019/01/12/fix-for-the-windows-7-smb-network-bug-caused-by-update-kb4480970-kb4480960/](https://borncity.com/win/2019/01/12/fix-for-the-windows-7-smb-network-bug-caused-by-update-kb4480970-kb4480960/)

---

