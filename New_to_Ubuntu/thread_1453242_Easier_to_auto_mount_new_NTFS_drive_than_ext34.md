---
title: "Easier to auto mount new NTFS drive than ext3/4?"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by powel212 on 2010-04-13
I just built a new file server with 2 drives, one boot and one backup.

I used the "Disk Utility" to setup and initialize the second drive as ext4 but it would not mount automatically on startup.

So I formatted it NTFS and used "NTFS configuration tool" to auto-mount it on Startup.

I would have preferred to leave the secondary drive as ext4 but did not see a straight forward method in Disk Utility for adding it to fstab.

Am I missing something or do I still have to manually add the new drive to /etc/fstab after initilizing it in "Disk Utility"?

Best regards

Powel

---

### Post by Elfy on 2010-04-13
You can use pysdm, it's in the repos - but I tend to do it manually - doesn't take long and once it's done you don't have to do it again.

---

