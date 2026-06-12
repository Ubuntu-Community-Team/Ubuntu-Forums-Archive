---
title: "totally disable ntfs-config"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by billgujie on 2009-11-12
Hi, I've installed ntfs-config and uninstalled it through software centre,

however all my ntfs partitions are still automounted everytime, besides that i cant no longer mount/unmount them if not in root mode, i think ntfs-config cause this, how can i totally disable these features and my permission to mount/unmount back?

Thanks

---

### Post by sisco311 on 2009-11-12
Edit the /etc/fstab file and comment out or remove the entries:
```
gksu gedit /etc/fstab
```

the second column is the mount point.

i.e.
```
/dev/sda1   **/media/XP**    ntfs    defaults,gid=64    0    0
```

to comment it out put a # at the beginning of the line:

```
#/dev/sda1   **/media/XP**    ntfs    defaults,gid=64    0    0
```

---

### Post by billgujie on 2009-11-12
> **sisco311 said:**
> Edit the /etc/fstab file and comment out or remove the entries:
```
gksu gedit /etc/fstab
```

the second column is the mount point.

i.e.
```
/dev/sda1   **/media/XP**    ntfs    defaults,gid=64    0    0
```

to comment it out put a # at the beginning of the line:

```
#/dev/sda1   **/media/XP**    ntfs    defaults,gid=64    0    0
```


this is for stopping the automount feature right? how about restore the ownership of these partitions?

---

### Post by falconindy on 2009-11-12
> **billgujie said:**
> this is for stopping the automount feature right? how about restore the ownership of these partitions?
If those entries exist in your /etc/fstab then yes, they will no longer be mounted on boot.

NTFS has no concept of ownership as Ext based filesystems do in Linux. When you mount an NTFS partition, you have to specify the owner in the mounting options. If omitted, the owner will be root.

---

### Post by sisco311 on 2009-11-12
> **billgujie said:**
> this is for stopping the automount feature right? 

yes.

> **billgujie said:**
> 
how about restore the ownership of these partitions?

FAT and NTFS partition don't support linux/ubix file permissions.

The permissions are set at mount time. By default, Ubuntu will set your user as the owner.

---

### Post by billgujie on 2009-11-13
> **falconindy said:**
> If those entries exist in your /etc/fstab then yes, they will no longer be mounted on boot.

NTFS has no concept of ownership as Ext based filesystems do in Linux. When you mount an NTFS partition, you have to specify the owner in the mounting options. If omitted, the owner will be root.

> **sisco311 said:**
> yes.



FAT and NTFS partition don't support linux/ubix file permissions.

The permissions are set at mount time. By default, Ubuntu will set your user as the owner.


Ok, now they dont automount anymore, thanks.

the problem now is when i want to mount then i click one of the partition shown in the "computer", and it says "only root can mount this disk", but normally there should be a window jump out asking my password.

so i can only mount/unmount through terminal. Thats the permission problem i was talking about.

---

### Post by billgujie on 2009-11-13
oh, i was being stupid, problem solved by commenting out the lines. thanks guys.

---

### Post by tanmaykumar on 2011-03-04
This is the current preview of my fstab file. But after restart, all are automounted again :( Can anybody tell me what change should I make in my following fstab file to be able to mount/unmount drives at any time?:
```
UUID=420CBAC60CBAB46F /media/sda1 ntfs-3g defaults 0 0
UUID=f06e7a19-bedf-41f1-8883-2a9e64604575 / ext4 defaults 0 1
UUID=eb84931a-c261-4535-ac78-b738487b3869 swap swap sw 0 0
UUID=0A98C96098C94B41 /media/VIDEO-1 ntfs-3g defaults 0 0
UUID=E8A07872A0784958 /media/VIDEO_2 ntfs-3g defaults 0 0
UUID=B2B8ABA0B8AB6199 /media/AUDIO ntfs-3g defaults 0 0
UUID=0082E9DB82E9D4E6 /media/OTHERS ntfs-3g defaults 0 0
UUID=E2369D47369D1E1B /media/SOFTWARES___GAMES ntfs-3g defaults 0 0
```

[Partitions are unmounted right now, it will be automounted after the restart :(]

---

### Post by JKyleOKC on 2011-03-04
This is a very old thread and you really should create a new one for your question, but here's the answer if you want ALL of your Windows partitions to NOT automount. Make the file look like this:

```
#UUID=420CBAC60CBAB46F /media/sda1 ntfs-3g defaults 0 0
UUID=f06e7a19-bedf-41f1-8883-2a9e64604575 / ext4 defaults 0 1
UUID=eb84931a-c261-4535-ac78-b738487b3869 swap swap sw 0 0
#UUID=0A98C96098C94B41 /media/VIDEO-1 ntfs-3g defaults 0 0
#UUID=E8A07872A0784958 /media/VIDEO_2 ntfs-3g defaults 0 0
#UUID=B2B8ABA0B8AB6199 /media/AUDIO ntfs-3g defaults 0 0
#UUID=0082E9DB82E9D4E6 /media/OTHERS ntfs-3g defaults 0 0
#UUID=E2369D47369D1E1B /media/SOFTWARES___GAMES ntfs-3g defaults 0 0
```That is, add the "#" at the start of every line except the second and third.

To edit the /etc/fstab file you must have root privileges. You can do it via "gksudo gedit /etc/fstab" but be extremely careful as mistakes while in root mode can leave your system unbootable.

---

### Post by tanmaykumar on 2011-03-05
> **JKyleOKC said:**
> This is a very old thread and you really should create a new one for your question, but here's the answer if you want ALL of your Windows partitions to NOT automount. Make the file look like this:

```
#UUID=420CBAC60CBAB46F /media/sda1 ntfs-3g defaults 0 0
UUID=f06e7a19-bedf-41f1-8883-2a9e64604575 / ext4 defaults 0 1
UUID=eb84931a-c261-4535-ac78-b738487b3869 swap swap sw 0 0
#UUID=0A98C96098C94B41 /media/VIDEO-1 ntfs-3g defaults 0 0
#UUID=E8A07872A0784958 /media/VIDEO_2 ntfs-3g defaults 0 0
#UUID=B2B8ABA0B8AB6199 /media/AUDIO ntfs-3g defaults 0 0
#UUID=0082E9DB82E9D4E6 /media/OTHERS ntfs-3g defaults 0 0
#UUID=E2369D47369D1E1B /media/SOFTWARES___GAMES ntfs-3g defaults 0 0
```That is, add the "#" at the start of every line except the second and third.

To edit the /etc/fstab file you must have root privileges. You can do it via "gksudo gedit /etc/fstab" but be extremely careful as mistakes while in root mode can leave your system unbootable.
Actually I am new here. Thanks a lot, it works :)

---

