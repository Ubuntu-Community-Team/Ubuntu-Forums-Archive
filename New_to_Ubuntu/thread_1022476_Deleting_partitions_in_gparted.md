---
title: "Deleting partitions in gparted"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-12-26
If I delete a partition in gparted, like one of the first ones, will it reconfigure GRUB and fstab and other stuff so that they refer to the correct partition once the numbering has changed?

---

### Post by theozzlives on 2008-12-26
No

---

### Post by mkvnmtr on 2008-12-26
You need to be very careful deleting those small partitions especially those first ones. If you arnt sure take a screen shot and ask here in the forums.

---

### Post by moredhel on 2008-12-26
however it's easy to edit GRUB and fstab afterwards

```
gksudo /boot/grub/menu.lst
```

```
gksudo /etc/fstab
```

---

### Post by kansasnoob on 2008-12-26
> **linkmaster03 said:**
> If I delete a partition in gparted, like one of the first ones, will it reconfigure GRUB and fstab and other stuff so that they refer to the correct partition once the numbering has changed?

Uh not to be disagreeable but look at mine:

[ATTACH]97709[/ATTACH]

Grub is set to boot from sda7, so if I delete sda7 I'll have to restore grub to either sda5 or sda9. And I'd have to edit the menu list in those OS's!

If I were to delete Windows which is sda1, then I'd have no Primary partition at the beginning of the drive. It's not a deal breaker but it creates a huge problem!

Deleting or editing partitions requires planning!

---

### Post by linkmaster03 on 2008-12-26
Thanks guys.

---

