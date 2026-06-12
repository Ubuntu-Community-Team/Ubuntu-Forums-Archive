---
title: "Can't Remember how I totally uninstalled Wubi"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by Andavane on 2011-08-06
Hi
I tried Wubi on my Thinkpad X201i while waiting for Ubuntu Natty to settled down, having prepared 2 partitions ready to install it fully alongside Windows 7.

I ran wubi uninstall successfully in C, however I still get the picture below when I go to disk management, which shows the ubuntu partition still there, presumably with its 78 GB of data.

The thing is, I've done this before on another machine and it all went fine. I *think* I deleted the ubuntu partition using the Windows Disk Management, but can't remember and don't want to mess things.

Is deleting that partition all right?

---

### Post by Rex Bouwense on 2011-08-06
Unless I read that wrong, you still have the partition (78.12 Gb) and 78.12 GB of free space in the partition so apparently the OS is gone but the partition is still there.

---

### Post by Old_Grey_Wolf on 2011-08-06
You created the 78 GB partition manually. WUBI uses a virtual disk within the Windows partition, it is basically a file on the Windows partition. WUBI also has a limitation that the disk can be no larger than 30 GB. You have never really been using that 78 GB partition. You have that partition ready for installing Natty along side Windows. You can delete that partition because WUBI isn't using it.

Can you still boot into Ubuntu?

If Ubuntu doesn't boot anymore, then somehow you must have removed the WUBI application using Window's add/remove program control panel or deleted the Virtual Disk file.

---

### Post by Andavane on 2011-08-07
>"If Ubuntu doesn't boot anymore, then somehow you must have removed the WUBI application using Window's add/remove program control panel or deleted the Virtual Disk file"
Indeed I did.
I'll delete that 78 GB partition then make an ext4, also a swap area and then install 11.04.

---

### Post by amjjawad on 2011-08-07
> **Andavane said:**
> then make an ext4, also a swap area and then install 11.04.

Use GParted to do that job while you're booting from the LiveCD or LiveUSB.

Good luck ;)

---

### Post by Andavane on 2011-08-07
> **amjjawad said:**
> Use GParted to do that job while you're booting from the LiveCD or LiveUSB.

Good luck ;)
Thanks - unfortunately I deleted it in Windows, then used the live usb to adjust with Gparted before installing.

It's all dual-booting fine atm, though.

---

### Post by amjjawad on 2011-08-07
> **Andavane said:**
> Thanks - unfortunately I deleted it in Windows, then used the live usb to adjust with Gparted before installing.

It's all dual-booting fine atm, though.

It's ok ... glad it's working now :)

---

### Post by Andavane on 2011-08-10
> **amjjawad said:**
> It's ok ... glad it's working now :)

Cheers mate!
In future it'll be done from the live USB! ;)

---

### Post by amjjawad on 2011-08-10
> **Andavane said:**
> Cheers mate!
In future it'll be done from the **live USB**! ;)

YES, agreed :D

---

