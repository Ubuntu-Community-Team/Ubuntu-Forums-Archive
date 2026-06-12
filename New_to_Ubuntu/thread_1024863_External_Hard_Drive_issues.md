---
title: "External Hard Drive issues"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by tu_mas_gordo on 2008-12-29
I have some issues with my maxtor 1TB hard drive. I use it as my external hard drive and everytime i plug it into ubuntu and try to open a file or copy from it, I get a input/output error, and when I hook it up to windows and try to copy from it, I get a "USB not recognized error". Anyone seen or herd of this before?

---

### Post by mapes12 on 2008-12-29
How is it formatted. Ext3 or NTFS?

Plug it in then post the output to ```
fdisk -l
```

---

### Post by kestrel1 on 2008-12-29
I have an issue with a much smaller HDD & I think it is down to the drive not having external power. I would assume that yours has an external PSU. 
Are you connecting the drive to the USB ports on the front of your case (if you have them) or the back or is it a PCI USB card?

---

### Post by tu_mas_gordo on 2008-12-29
> **mapes12 said:**
> how is it formatted. Ext3 or ntfs?

ntfs

---

### Post by tu_mas_gordo on 2008-12-29
> **mapes12 said:**
> Plug it in then post the output to ```
fdisk -l
```

I don't understand what you are saying to do with this.

I ran "sudo fdisk -l" and all it did was give me some info on the hard drives plugged to my computer.

---

