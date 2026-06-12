---
title: "Samba Service Requires Restart To Show New Files"
date: 2014-09-13
forum: Networking &amp; Wireless
---

### Post by leomoon2 on 2014-09-13
Hello,

I'm having a strange problem with Samba Service. I didn't have this problem when I was using Ubuntu 12.04 x64. I formatted and installed Ubuntu 14.04 x64 and it started doing this.

I installed samba service to share the Deluge torrent client's download folder with a Windows 8.1 computer. Now every once in a while, I must restart samba server to show the newly created files/folders.

Here is my smb.conf:
```
[global]
refresh = 1
workgroup = WORKGROUP
server string = SERVERNAMEHERE
netbios name = SERVERNAMEHERE
security = user
map to guest = Bad User
dns proxy = no
guest account = nobody
create mask = 0644
directory mask = 0755
[PUBLIC]
commnet = PUBLIC
path = /mnt/samba/PUBLIC
browsable = yes
guest ok = yes
read only = no
create mask = 0755
```

Any suggestions is greatly appreciated.

Thanks.

---

### Post by leomoon2 on 2014-09-14
Anybody?

---

