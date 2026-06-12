---
title: "nautilus as root can't see network drive"
date: 2020-03-14
forum: Networking &amp; Wireless
---

### Post by bthoven on 2020-03-14
If I run nautilus as normal user, I can see and map network drives without problem; but if run as root by sudo nautilus, the mapped network drive can't be accessed and I can no longer see any network computer in the same workgroup.

What I have to do more to make it work?

---

### Post by TheFu on 2020-03-15
Don't use nautilus as root.  Doing so is an "anti-pattern."  Running most GUi programs as root, usually is a really bad idea for a number of reasons.

But if you insist, we need to know the specific mount types you want.  NFS?  CiFS?  AFS? Plan9? Something else?

i would suggest using the automount daemon instead.  it can be accessed either using autofs or systemd-automount.

---

### Post by bthoven on 2020-03-16
Thank you for your suggestion. I usually mount some network folder temporarily when I want to copy some files over to some root folders. Automount seems overkill for my case. The folder could be an smb share from Win10, afs share from synology, or ??share from another ubuntu server.

---

### Post by TheFu on 2020-03-16
> **bthoven said:**
> Thank you for your suggestion. I usually mount some network folder temporarily when I want to copy some files over to some root folders. Automount seems overkill for my case. The folder could be an smb share from Win10, afs share from synology, or ??share from another ubuntu server.

No Win10 here. Sorry.

How each of those (cifs, AFS, NFS, ....) gets mounted is different.  Best to open a thread for each.  Doesn't synology support NFS?  That would be the native Unix sharing to be used whenever possible. Basically, use CiFS for Windows-only and NFS for everything else.  I'm assuming you don't have MVS or a Cyber mainframe. ;)

systemd.automount is 1 line in the fstab for each mount. Don't think that is too hard for storage that is on your network, always.

Plus, if you are just copying some files off a friend's computer, one-time, then perhaps sftp, rsync or sshfs would be easier alternatives?  iDK.  Every Linux file manager supports the sftp:// URL.

i put files under /tmp/ somewhere first, always, then move them as needed or let a reboot delete them.  Safer, especially when /tmp/ is mounted with nodev and noexec options.  Don't want bad-guy-code getting onto our systems too easily.

---

### Post by Morbius1 on 2020-03-16
Nautilus uses gvfs to discover and connect to networked assets. Gvfs in turn uses fuse to create the "virtual" mount of that asset. Fuse by design allows a **non-privileged user ( i.e., not root or sudoer )** the ability to create a "view" of that "virtual" filesystem to be used by that user alone. So by design root cannot use this process.

I suppose you could mess around with the internal plumbing of fuse to allow root but I would suggest a different method of access.

---

