---
title: "Formatting second drive?"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by Autodave on 2010-10-25
I have 2 HDs in my netbook.  I accidentally installed 10.10 to the second drive and now wish to remove it from that drive.  I have EEEBUNTU (Ubuntu 9.04) installed on the first drive.  How do I remove the files or format the second hard drive?

---

### Post by ArgusVision on 2010-10-25
Boot into eeebuntu, go to Synaptic Package manager, and install Gparted.
Use with caution. Be **sure** to select the second drive (should be unmounted).
Format it as EXT3 or NTFS. (I'm pretty sure 9.04 couldn't see ext4.) You might want to add it to your /etc/fstab so it will automatically mount.

---

### Post by Autodave on 2010-10-25
> **ArgusVision said:**
> Boot into eeebuntu, go to Synaptic Package manager, and install Gparted.
Use with caution. Be **sure** to select the second drive (should be unmounted).
Format it as EXT3 or NTFS. (I'm pretty sure 9.04 couldn't see ext4.) You might want to add it to your /etc/fstab so it will automatically mount.


Hmmm....don't see gparted, but I do see one called "parted" which I am hoping is thew same thing.  Thanks!

---

