---
title: "Disk Mounting"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by AlanR8 on 2008-07-07
So.....may have been asked before. I have a Freecom 500 Gig network storage drive that's formatted as fat32. It also has a direct USB connection.

After months of hassle if I plug the drive directly by USB I can now read and write to it. (see one of my other threads about the previous problems).

I now have a "server", running KUBUNTU 8.04, and have the Freecom directly connected. The "server" is headless, no keyboard, monitor or mouse, and I connect via Krdc and it works well. If I log in to the server, I can copy files locally to the USB drive and delete them. I also have this drive shared and it's visible on the network. So far so good.

Here's the catch. Whilst the drive is visible to the network, under Linux I can NOT write to it from a remote machine. "Access denied, you don't have permission......"

I also know what the problem is, I think! Under Permissions, the user is correct but the group is ROOT. I can't change this permanently. I read somewhere on this forum that an external USB HD should not appear in the FSTAB file, and I understand why, probably.

This external drive is going to be permanently attached to the "server" so could it be mounted in FSTAB as follows:

/dev/sdc /media/sdc vfat rw,user,fmask=0111,dmask=0000 0 0

This should sort the Fat 32 permissions issues out, dmask.... and allow read write to the network, or am I missing the point?

---

