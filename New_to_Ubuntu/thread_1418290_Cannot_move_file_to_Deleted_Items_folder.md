---
title: "Cannot move file to Deleted Items folder"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by illingd on 2010-02-28
I have recently created a new ext3 partition and added an entry in fstab as follows:

```

# /dev/sda4 - Data volume (documents, databases, etc)
UUID=e05c4af1-406a-4af1-964c-51be4ddf4f15 /media/Data ext3 rw,nosuid,nodev

```The partition is mounted and works OK, but when I try to delete a file (in Nautilus gui) it gives an error/warning dialog pops up saying 

```
Cannot move file to the Deleted Items folder, do you want to delete permanently?
The file "test file 2.txt" cannot be moved to the wastebasket.

```What have I done wrong?

---

### Post by Paddy Landau on 2010-02-28
I don't know the answer, sorry, but I do see something that you should add: relatime.
```
UUID=e05c4af1-406a-4af1-964c-51be4ddf4f15 /media/Data ext3 rw,nosuid,nodev,relatime
```

---

### Post by asmoore82 on 2010-02-28
I would also consider adding ```
noexec
```

The error is because nautilus is unable to create a hidden "Trash" folder at the top level of the mounted volume. Create this folder manually and make it writable by everyone - but with the added security of the "sticky bit" ...
```
sudo mkdir /media/Data/.Trash
sudo chmod 1777 /media/Data/.Trash
```

---

### Post by illingd on 2010-03-02
> **asmoore82 said:**
> I would also consider adding ```
noexec
```The error is because nautilus is unable to create a hidden "Trash" folder at the top level of the mounted volume. Create this folder manually and make it writable by everyone - but with the added security of the "sticky bit" ...
```
sudo mkdir /media/Data/.Trash
sudo chmod 1777 /media/Data/.Trash
```

That fixed it! - thanks

On a similar theme, ...
I have an NTFS partition that also won't move to trash, and I assumed this is because it's NTFS. But maybe it's possible to get trash working on that too? I tried the above on that volume, but it still won't move to trash.
 Here's my fstab for that:```

# /dev/sda5 - Visual (Images and Video) (was Vol_D)
UUID=4A2486D12486BF85 /media/Visual ntfs rw,nosuid,nodev,allow_other
```

---

