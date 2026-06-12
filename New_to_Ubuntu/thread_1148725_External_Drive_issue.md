---
title: "External Drive issue"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by aas452 on 2009-05-04
I am getting a error while trying to mount a NTFS external Hard Drive

Invalid mount option when attempting to mount the volume 'BACKUP'.

BACKUP is the name of the NTFS Drive, and connected to the USB port.

Any help??

---

### Post by jbrown96 on 2009-05-04
NTFS drives have to be removed safely before you unmount them (Windows and Ubuntu). to be safe Ubuntu does not force mount "dirty" drives (improperly unmounted). 

Easiest solution is to boot into windows and safely remove the drive.

---

### Post by Mark Phelps on 2009-05-04
> **aas452 said:**
> I am getting a error while trying to mount a NTFS external Hard Drive

Invalid mount option when attempting to mount the volume 'BACKUP'.

BACKUP is the name of the NTFS Drive, and connected to the USB port.

Any help??

You can't mount based on the "name" -- that's just a "label" for the device and doesn't mean anything.  You have to mount based on device ID (e.g., /dev/sda1).  

Besides, when you plug in an external drive via USB, it should be mounted automatically and you see an icon for it on the desktop.

Would be best to repeat the mount command syntax you're using so we can tell you specifically what you would need to change.

Also, if you're going to do this regularly, ensure that the package ntfs-3g is installed; if not, add it through Synaptic before proceeding.

---

