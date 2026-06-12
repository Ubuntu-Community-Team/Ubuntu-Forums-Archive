---
title: "Problem with nfs directory when unplugged cable without umount directories"
date: 2016-06-06
forum: Networking &amp; Wireless
---

### Post by sed_faster on 2016-06-06
Hello guys,

I have installed nfs (network file system) on pc with  Ubuntu 14.04 LTS 32 bits and I access it through ssh through Lubuntu  16.04 LTS. I can mount "drive" via this command "sudo mount -t nfs  ip:directory_of_the_files directory_in_my_pc. When I executed this  command I need wait a couple minute to my system mount the folders on my  file system, but I ok! I can browse tranquillity through all folders.  But the problem occur when I need disconnect my pc of the network and  forgotten make "sudo umount directory_where_I_mounted_the_directories.  If I unplugged the cable without ran the previous command my file  manager, on Lubuntu I use the native file system "  PCManFM", crashed  and in some cases I need reset the pc :/

How can I do for I haven't this problem on the cases when I forgotten umount the nfs directories?
Another detail, If is possible when I plug my cable on the network the nfs directory mounted alone?

Thanks

---

### Post by TheFu on 2016-06-06
NFS expects a constant connection.  Unplugging is like disconnecting a SATA cable.  There aren´t any perfect solutions - please umount the storage.

However, you can use a workaround to make the unplugging less likely while mounted.  Use **autofs**.  I´m not thrilled with the Ubuntu autofs instructions. They have to cover all sorts of things that aren´t important to you.  In short, autofs only mounts storage when it is requested. If the storage isn´t requested, then it isn´t mounted.  Additionally, if previously requested storage hasn´t been used in some period of time - I think about 15 minutes - it is automatically umounted.  I don´t know the actual timeout numbers. Sorry. Suspect they are configurable for each automount.

I use autofs for all nfs, samba and USB storage here. [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
Don´t have any 16.04 servers yet and only have 1 16.04 client, but the client autofs is working perfectly to multiple 14.04 NFS servers.  Autofs is client-side only.

If you recently accessed NFS storage and unplug the client, it shouldn´t be as bad as with a permanent NFS mount, but it is still bad if it is still mounted.

---

