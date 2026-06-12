---
title: "Need help uninstalling Grub?"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by Aod43254 on 2011-01-20
I recently installed Ubuntu 10.10, and chose to have Grub installed on an external HDD with Ubuntu. I was expecting that doing so would cause Grub to only be used when the external is in but when I try to boot my computer up without the external in I get a message saying Grub can't be found and it won't load. So I want to find out how to remove Grub completely, since I have my internal HDD with Windows 7 set as the last device to be booted to I don't really need to worry about having a boot loader since all I plan to have it so when I boot with the external HDD plugged in then Ubuntu will be booted up instead of Windows 7. So can anyone help? I just want to remove Grub completely.

~Aod43254

---

### Post by hansolo4949 on 2011-01-20
The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

---

### Post by hansolo4949 on 2011-01-20
The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

---

### Post by hansolo4949 on 2011-01-20
The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

---

### Post by hansolo4949 on 2011-01-20
The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

---

### Post by hansolo4949 on 2011-01-20
The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

---

### Post by hansolo4949 on 2011-01-20
The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

---

### Post by hansolo4949 on 2011-01-20
The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

---

### Post by hansolo4949 on 2011-01-20
The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

---

### Post by Aod43254 on 2011-01-20
> **hansolo4949 said:**
> The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

I don't have a recovery disk, all I have is my HP system restore disk. My Windows 7 came pre-installed on my laptop. And just wondering is there anyway that I can use Ubuntu on my external without having Grub?

---

### Post by Aod43254 on 2011-01-20
> **hansolo4949 said:**
> The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

What if I don't have a Window 7 recovery disk? And if I want to have Ubuntu on my external do I have to have a Grub?

---

### Post by Aod43254 on 2011-01-20
> **hansolo4949 said:**
> The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

What if I don't have a Window 7 recovery disk? And if I want to have Ubuntu on my external do I have to have a Grub?

---

### Post by Aod43254 on 2011-01-20
> **hansolo4949 said:**
> The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

What if I don't have a Window 7 recovery disk? And if I want to have Ubuntu on my external do I have to have a Grub?

---

### Post by Aod43254 on 2011-01-20
> **hansolo4949 said:**
> The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

What if I don't have a Window 7 recovery disk? And if I want to have Ubuntu on my external do I have to have a Grub?

---

### Post by Aod43254 on 2011-01-20
> **hansolo4949 said:**
> The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

What if I don't have a Window 7 recovery disk? And if I want to have Ubuntu on my external do I have to have a Grub?

---

### Post by Aod43254 on 2011-01-20
> **hansolo4949 said:**
> The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

What if I don't have a Window 7 recovery disk? And if I want to have Ubuntu on my external do I have to have a Grub?

---

### Post by Aod43254 on 2011-01-20
> **hansolo4949 said:**
> The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

What if I don't have a Window 7 recovery disk? And if I want to have Ubuntu on my external do I have to have a Grub?

---

### Post by Aod43254 on 2011-01-20
> **hansolo4949 said:**
> The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

What if I don't have a Window 7 recovery disk? And if I want to have Ubuntu on my external do I have to have a Grub?

---

### Post by Aod43254 on 2011-01-20
> **hansolo4949 said:**
> The exact same thing happened to me. All you have to do is boot up your windows 7 recovery disk (not the restore disks, they will reinstall windows 7) and open up the commando prompt. Type: bootrec /fixmbr then bootrec /fixboot. You should be good to go, thought you won't be able to use Ubuntu on the external drive I don't think. You should go into a partition manager and delete the Ubuntu partitions on that drive if you have other stuff on it (the Ubuntu partitions are in the EXT3 format or something similar, or just format it.

What if I don't have a Window 7 recovery disk? And if I want to have Ubuntu on my external do I have to have a Grub?

---

