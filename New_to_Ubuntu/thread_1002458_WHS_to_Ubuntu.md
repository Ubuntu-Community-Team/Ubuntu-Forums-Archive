---
title: "WHS to Ubuntu"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by stayrollin on 2008-12-05
I would like to move my Windows Home Server based file server to Unbuntu 8.10. Currently I have two usb drives on the server that store a lot of my data. The drives are NTFS. I know Ubuntu can read and write NTFS natively now but I was not sure if I am going to be able to set user permssions on the folders if the drives aren't converted to FAT32.

---

### Post by mister_pink on 2008-12-05
You won't be able to set any fine grained user permissions on the drive as ntfs or fat32 - you can only set them for the whole drive. Ubuntu typically uses the ext3 filesystem in a default setup, although you can make it use others. As far as I know there isn't a way to convert drives without taking the data off them, formatting to ext3 and then putting it back again.

---

