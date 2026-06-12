---
title: "Needing to mount a network share at boot"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by diablo75 on 2011-04-21
I got a phone call from someone today asking for help with Ubuntu.  They basically have a Windows 2000 Server running that they would like to have full read/write access to from Ubuntu and for that access to be auto-mounted when they turn their Ubuntu machine on.

I have had trouble using the file and folder sharing features between Windows and Linux before and suggested that they instead setup an SSH server on Windows and then login to that from Linux (and I've found a good Windows-based SSH server called freeSSHd for this purpose).

So I think all I need help with is figuring out the best way to auto-mount an SSH network share in Ubuntu (would assume this requires editing the fstab, yes?).

I'm open to suggestions about doing it this way (via SSH) as opposed to some other method, but to me it seems the easiest, most reliable and possibly most secure method for what they are wanting to do.

---

### Post by taseedorf on 2011-04-22
If you simply need to access a Windows share from Linux and have it mount automatically on boot I'd use NFS.  You just need to install the proper NFS utilities on windows.  I'm not sure of the exact information you need to put in fstab, but yes, you need to edit it.  search for NFS share fstab on here or google and you'll find it.  You can tunnel it over ssh if you want, but it's not needed.

---

### Post by diablo75 on 2011-04-22
Well I suppose I could experiment with NFS (never setup an NFS server in Windows before; don't know where to begin or what to download).  I think I'll be able to handle the fstab side of things but a recommendation for a good NFS server that will run on Windows 2000 would be a big help.

---

### Post by diablo75 on 2011-04-24
Bump.

---

