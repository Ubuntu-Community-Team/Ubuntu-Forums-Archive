---
title: "NFS shared folders and mounted partitions"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by cdmdotnet on 2008-09-25
I'm sure this is a simple fix

I've shared a folder on my Ubuntu machine (NFS server). Said folder has five subfolders, all of which are mount points for various partitions - eg /music => sda2, /videos => sda3 etc.

when I use fstab to mount the shared folder, i can see the folders, but the contents of each mount point is empty IE NFS isn't reading and following the mount points, just the folder.

is there a way around this without me having to share each mount point individually?

thanks.

---

