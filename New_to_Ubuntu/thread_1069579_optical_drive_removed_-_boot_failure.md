---
title: "optical drive removed - boot failure"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by morgan123 on 2009-02-14
I have installed xubuntu on a IDE hdd with jumpers on Master and I also have a CD IDE drive as slave. The computer also has 2 SATA hdd not formatted.
After install, I can boot fine in Xubuntu from the hdd (I've removed the live cd from the optical drive).
But after shut down and removal of the CD IDE optical drive, GRUB fails to boot from the hdd. The message is something about timeout error with the hdd. If I stick the optical drive back in, it boots ok.
Can anyone help cause I need to boot without this optical drive in the box as it's not meant to stay in.

mobo: ASUS M2A-VM HDMI
proc: AMD 4850e
2 SATA hdd
1 IDE hdd (single partition with xubuntu on it)
1 CD IDE

---

### Post by hyper_ch on 2009-02-14
exact error would be nice

and when you're booted, post the following output:

```

sudo fdisk -l

```

```

cat /boot/grub/menu.lst

```

```

df -h

```

```

ls -al /dev/disk/by-uuid

```

---

### Post by morgan123 on 2009-02-15
thanks for the reply. It was a jumper problem , needed to remove the jumper from the hdd to enable it when there is no optical drive.

---

