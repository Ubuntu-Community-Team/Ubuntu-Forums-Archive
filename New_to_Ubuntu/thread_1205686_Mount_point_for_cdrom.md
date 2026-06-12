---
title: "Mount point for cdrom?"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by Wyvernoid on 2009-07-06
Here's an excerpt from VMware's manual:
> If necessary, mount the VMware Tools virtual CD-ROM image by entering a command similar to the following:
 mount /dev/cdrom /mnt/cdrom
Some Linux distributions automatically mount CD-ROMs. If your distribution uses automounting, you can skip this step.
Some Linux distributions use different device names or organize the /dev directory differently. If your CD-ROM drive is not /dev/cdrom or if the mount point for a CD-ROM is not /mnt/cdrom, modify the command to reflect the conventions used by your distribution.Now I go to /dev, and there's a file (maybe a file? it shows up in aqua blue in ls) named cdrom. And when I type "sudo mount /dev/cdrom /mnt/cdrom", an error pops up reading "mount: mount point /mnt/cdrom does not exist". So I guess Ubuntu is one of those Linux distributions that use different mount points for CD-ROMs... What do I do now?

PS. After this, the following should supposedly be executed:
> tar zxpf /mnt/cdrom/VMwareTools-<xxxx>.tar.gzThis code refers to /mnt/cdrom, so if the above problem doesn't get solved, this doesn't work.

---

### Post by Mornedhel on 2009-07-06
The default in Ubuntu is /media/cdrom.

---

### Post by Wyvernoid on 2009-07-06
Thanks a lot! May I ask, then, what /mnt is used for?

---

### Post by derekeverett on 2009-07-06
I think it's intended for external file systems. Like a windows file system...

At least that's what I think it's intended for.

You can mount any file system or device anywhere you want really.

---

### Post by CatKiller on 2009-07-06
> **Wyvernoid said:**
> Thanks a lot! May I ask, then, what /mnt is used for?

/media is traditionally used for removable media; cdroms, floppy disks, thumb drives, memory cards, that kind of thing.

/mnt is used for everything else; non-specific hard drive partitions, network mounts, that kind of thing.

As derekeverett says, you don't need to follow the [standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"). You can mount whatever you want wherever you want.

---

### Post by egalvan on 2009-07-06
to add one more item to CatKiller's excellent post...

devices in** /media **will show an icon on the desktop when mounted.
(very handy for removable media...
pop in the media, it's automounted and an icon pops up on your desktop...
unmount/eject the media, it's unmounted and the icon disappears from your dekstop)


devices in** /mnt** will not show an icon on the desktop when mounted.

---

