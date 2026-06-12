---
title: "How does it do that?"
date: 2005-08-07
forum: Networking &amp; Wireless
---

### Post by Tomlin on 2005-08-07
How is it that my ubuntu machine can see, and copy to and from the other machines on my network without me setting up SAMBA?

The folder icons show up with "SMB" as though its using SAMBA, but neither nmbd nor smbd are running.  :???: 

It sees both windoze 2000 and 98 machines and my Suse 9.0 machine.

The reverse is NOT true, i.e. I can't see the ubuntu box from either windoze box or the Suse machine.

TIA

---

### Post by grim42 on 2005-08-07
Nautilus has it's own built-in SMB support (I think) for reading Windows shares (or it could be a kernel filesystem module?)

You need to install Samba to share stuff on your Ubuntu system though (so that the other boxes will be able to see it).

BTW: SMB doesn't necessarily mean Samba, it's just refering to the Windows filesharing protocol (Server Message Block).

---

### Post by az on 2005-08-07
You have the samba client installed by default, but not the samba server.  You can see them, but nothing can come in.

---

