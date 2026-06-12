---
title: "best file system on a fileserver / PDC?"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by LoveJoyDK on 2010-04-04
Hi.

As mentioned elsewhere I am making a PDC / Fileserver in Ubuntu Server.

On one Hd at about 200 GB in size, I will put system and swap partitions like /boot, /, /home etc. And 4 x 1TB disks in raid 5 for [alluser] shares on the network. GB large files as well as small KB files will be shared.

In my test builds so far I have used EXT4 on all partitions, and default block sizes.
But only picked that because I expect 4 to be better than 3, and not sure about journaling FS

So what would be best for a system like the one mentioned regarding block size and file system choice?

Thanks in advance.

---

### Post by HDave on 2010-04-07
I would stick to ext4 as it is the most widely used and reliable system.  Also because you will not have to wait as long during a forced file system check during boot up.

The only time I would mess with block size is when I have huge media files on it.

---

