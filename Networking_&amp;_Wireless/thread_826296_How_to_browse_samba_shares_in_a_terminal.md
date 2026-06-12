---
title: "How to browse samba shares in a terminal?"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by rhythminmind on 2008-06-11
Say you don't know what the share names are on a samba server. Can to see a share list from a terminal?

---

### Post by alzyee on 2008-06-11
I think that this will display the shares
```
smbclient -L <IP address of server> -U%
```

this should mount the share
```
sudo smbmount //<IP address of server>/<name ofshare>  /<mountpoint> -o username=dbott,password=mysecretpassword,uid=1000,mask=000
```

this is where I got this stuff from here
[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

