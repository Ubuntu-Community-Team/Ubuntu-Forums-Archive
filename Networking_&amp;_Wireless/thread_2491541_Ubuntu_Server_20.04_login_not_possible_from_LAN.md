---
title: "Ubuntu Server 20.04 login not possible from LAN"
date: 2023-10-12
forum: Networking &amp; Wireless
---

### Post by lcm-3 on 2023-10-12
I made the mistake of insstalling Open Media Vault on an Ubuntu Server 20.04. The OS was installed over two years ago and was working fine.

The omv instructions said to run 'omv firstaid', which I did. It messed up all my access to that server. I can not ssh into it; it won't even accept my password, but I know it's correct since I use it to login at the console.

I cannot access any CIFS mounts from all workstations. If I try to list a mounted folder, it says 'Host is down'. But I can ping the server's ip.

I ran 'netplan try' and it found now errors. 

I removed all of the omv software.

Any thoughts on what I might do to begin to fix this mess?

---

### Post by TheFu on 2023-10-13
If netplan isn't happy, networking won't be happy. Fix that first.

Is ssh running?
Is samba running?

If your workstations are Linux, then NFS would be much preferred over CIFS.

Are firewall rules in place to allow ssh and samba?

Probably should be looking in the system logs for issues, but no networking will work until netplan is happy.  I assume since you didn't post the exact netplan command + output nor the netplan file, you will happily solve that aspect yourself.

---

### Post by lcm-3 on 2023-10-14
Thanks TheFu. Netplan was working, smbd was not running but not sshd was. I restarted  smbd and mounts were OK. The logs showed the ssh user's group was not included in AllowGroups. After fixing that, ssh worked!

Setting up NFS was not easy for me so I gave up.

---

### Post by TheFu on 2023-10-14
If this is solved, please use the Thread Tools button and mark it as SOLVED. Help the community. Please.

NFS isn't hard. Actually, it is much easier than samba and tends to work for decades without any tweaks.  The NFS protocol has been stable over 20 yrs, but that's a different thread.

---

