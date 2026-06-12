---
title: "Installing Ubuntu"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by hwfa on 2009-01-14
I'm running Windows XP Pro on a new computer. I carefully configured it to have three "logical" disks on the one physical disk. In Windows terms these are C:, D: and E:. C and D are reserved for Windows and have stuff on them. E was reserved for Ubuntu and is empty. When I boot the Ubuntu (8.10) install disk and choose Install, these three show up as /dev/sda1, /dev/sda5 and /dev/sda6. I'm then given 4 choices of where to install Ubuntu:

1. Guided. This will resize sda5, which is largely empty. The result will be a very small sda5 with Ubuntu installed into what was the rest of it. **Not** what I want.

2. Guided. Use entire disk. This will do what it says; completely wipe my entire hard disk and install Ubuntu on it. **Not** what I want.

3. Guided. Use largest continuous free space. This will do the same as #2 above.

4. Manual. This *looks* as if it will take the entire disk. I'm scared of proceeding in case I blow my Windows configuration away.

How do I tell the installer to use *only* /dev/sda6 and *nothing* else?

---

### Post by Titan8990 on 2009-01-14
Manual but I am not sure you can install an OS on a logical partition.

---

### Post by hwfa on 2009-01-14
Hmm. Thanks. Where do I install it then?

---

### Post by ugm6hr on 2009-01-14
The simplest way that i recommend for people who don't understand partioning too well is to just delete sda6 comnpletely (i.e. leave it "unallocated")

Then you can use the "Guided - largest continuous free space" option

If you want to do it manually - you will have to edit the partitions anyway - it is recommended to use a swap partition in addition to a "/" (aka "root" partition).

---

### Post by Titan8990 on 2009-01-14
You can give it a try on the logical partition, if you are not using it, it shouldn't hurt anything.


Format /dev/sda6 to ext3 and set its mount point to / . Don't forget about a swap partition (typical size is twice your amount of RAM but no higher than 2-4GB.

---

### Post by ugm6hr on 2009-01-14
> **Titan8990 said:**
> You can give it a try on the logical partition, if you are not using it, it shouldn't hurt anything.

You CAN install Linux on a logical partition.

---

### Post by Titan8990 on 2009-01-14
I was unsure, thanks for the verification.

---

### Post by hwfa on 2009-01-15
Thank you, ugm6hr and Titan8990 for your help.

---

