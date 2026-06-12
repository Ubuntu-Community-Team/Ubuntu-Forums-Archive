---
title: "Samba speed slower from Linux than Windows"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by Jonnyuser on 2007-09-29
Hi.

I setup a Samba server based on CentOS5 and gigabit connenction. I tried the speeds. Under Windows it copies 30MB/s approximately, sometimes even faster. If I tried the same from my Ubuntu on the same desktop computer, it copies 8-13MB/s to the same Samba server, with the same file.

I read many server tunings, but it seems it's a different, client side problem. What can I do with my Ubuntu to get the same speed than Windows to the Samba server ? 

Thanks for advance.

---

### Post by MobiusNZ on 2007-09-29
Are you connecting via SAMBA or CIFS? If you are only using samba, try using cifs... A rough generalisation is that samba should be used if connecting to Win9x networks, and cifs should be used if connecting to newer win networks.

You might also want to consider serving more linux friendly protocols, such as nfs, or sftp.

---

### Post by Jonnyuser on 2007-09-30
I used smb:// with Krusader and Nautilus. I tried mount.cifs, but it needs to use passwords in cleartext form, so I drop it. I tried to firewalling NetBIOS, and only leave 445 open, and Krusader still works in smb:// form, but the speed was the same. I can use NFS with Unix based clients, and Samba with Windows clients, but I would be happier, if I don't need to administer two services. But if a Windows can copy fast to a Linux based service, I think a Linux client can too. Maybe some configuration options needed.

---

