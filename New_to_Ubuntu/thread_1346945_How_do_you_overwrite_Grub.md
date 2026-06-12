---
title: "How do you overwrite Grub?"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by Space-Wolf on 2009-12-05
Hi.  If I format the Ubuntu partition grub is still there.  It loads up and says can't find partition or something like that, and goes to "grub rescue>" where I can type things.  I can't load windows or anything.  Luckily I had my Linux Mint bootable USB on me, and I'm hoping the Mint installation overwrites the old grub with a new one, but just for reference, how would I overwrite grub and be able to boot into windows normally again?

---

### Post by halitech on 2009-12-05
2 ways I know of.

1. Boot from a windows install cd into recovery mode and run fixmbr

2. Download and install supergrub [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Space-Wolf on 2009-12-05
I'm on a netbook with no CD drive, but I know there is a recovery center built in.  How would I access that without a disk or anything?

---

### Post by halitech on 2009-12-05
I'm not sure, probably specific to your actual netbook

---

### Post by wilee-nilee on 2009-12-05
In the other thread you suggested that your might install Linux Mint. so do you just want the MS or are you planning to install another Linux distro. If your going to install another in the blank space load a thumb with the distro and install it in the blank space this will put the correct bootloader in the mbr.

You probably realize now that just deleting the Linux partition doesn't leave the MS bootloader to just work, it has to be reinstalled.

---

### Post by Space-Wolf on 2009-12-05
I installed Mint and Mint's Grub took over and everything is fine again.  I just didn't realize that I couldn't format the Ubuntu partition and have everything go back to normal.

---

### Post by wilee-nilee on 2009-12-05
> **Space-Wolf said:**
> I installed Mint and Mint's Grub took over and everything is fine again.  I just didn't realize that I couldn't format the Ubuntu partition and have everything go back to normal.

Yipee! I was surprised the experienced users had not informed you about the loss of a booting MS .

---

### Post by Space-Wolf on 2009-12-05
Yeah, ah well.  Thing is though, I'd like to be able to figure out how to do this recovery thing, just incase I decide to pass this laptop down and the person doesn't want Linux on it or something you know?

---

