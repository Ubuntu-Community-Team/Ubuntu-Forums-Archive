---
title: "Samba connection fails"
date: 2018-10-30
forum: Networking &amp; Wireless
---

### Post by andriy.svirskyy on 2018-10-30
Ubuntu 18.04 LTS connected to a local network with some Windows PCs.  Windows PCs have Samba shares (password protected), accessible from  other Windows PCs on the network. Following [this workaround]("https://ubuntuforums.org/showthread.php?t=2390509&p=13761597#post13761597") and other suggestions my /etc/samba/smb.conf has:


 ```
[global]

    client use spnego = no
    client NTLMv2 auth = no

    workgroup = WORKGROUP
    client max protocol = NT1
  
```

However Files(nautilus) still gives me [errors]("https://i.stack.imgur.com/QRqzB.png") after clicking on remote computers.


  How I can configure access to those Windows shares?

---

