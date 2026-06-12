---
title: "SMB shares not mounted wicd install"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by mindless1973 on 2008-10-28
Hi,

Du to some shutdown problems, I moved from network-manager to wicd. Since I installed wicd, my SMB shares specified in /etc/fstab are not mounted automatically during boot. I can mount them all manually, but as I use them often, I want to have them mounted automatically.

NFS shares are mounted correctly.

I assume that I have some mess in the rc2.d scripts, so that wicd is started after it tried to mount the smb shares (but I am not sure if that is really the reason).

Which init script is reponsible for mounting smb file shares?

thanks,

bye
me.

---

