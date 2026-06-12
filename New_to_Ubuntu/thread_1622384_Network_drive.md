---
title: "Network drive"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2010-11-15
Hey,

I was wondering if anyone had opinions on the best system to share directories on a server for manipulation across a network. I plan on mounting these directories as drives on my other computers.

I've been looking into NFS, but I thought I'd get some more input before I spent time doing anything.

All input is appreciated.

Thanks,
Kurt

---

### Post by chiefsittingduck on 2010-11-15
Samba would be the obvious choice.

---

### Post by jkurtisr32 on 2010-11-16
> **chiefsittingduck said:**
> Samba would be the obvious choice.

I've had a lot of permission issues with Samba. You don't feel like nfs will be a little bit nicer?

---

### Post by HarrisonNapper on 2010-11-16
Samba arguably is more vulnerable as a result of being more common, but it offers cross-compatibility with other OSes. If it's just a personal file share and all connecting computers will be nix computers, NFS is probably a little cleaner for managing perms. As I've never done any significant work with either, though, that's about all I know (and it's probably wrong).

---

### Post by deconstrained on 2010-11-16
If the machine running the service and the majority of the client machines are going to be Unix/Linux (or Macs) the choice of champions is [NFS4](https://help.ubuntu.com/community/SettingUpNFSHowTo). Unless your file server is running Windows or you run into trouble setting up Windows NFS clients, there's no reason to choose Samba over it.

---

### Post by pricetech on 2010-11-16
I'm terribly comfortable with Samba since I support a herd of windows boxen, but I'll agree that if your herd is *nix boxen, stick with NFS.

---

### Post by jkurtisr32 on 2010-11-20
Got samba up and running. Mapped the drive to /media using the terminal, but I'm having issues editing the fstab. And so my search continues.

---

