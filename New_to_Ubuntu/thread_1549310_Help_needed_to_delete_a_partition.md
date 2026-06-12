---
title: "Help needed to delete a partition"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by Peterfc on 2010-08-09
Hi

I recently install Mythbuntu in a 400gb partition alongside 100gb partition with my Ubuntu on.

For some reason whenever i try to run the Mythbuntu nothing happens now i just want to go back to a single partition with my Ubuntu on.

Could someone explain how to delete my Mythbuntu partition and leave me with my system as it was before.

Thanks

---

### Post by new__buntu on 2010-08-09
You could run an ubuntu livecd, go to install ubuntu, forward until it gets to the part with formatting your drive, tell it to delete the mythbuntu install, then resize your ubuntu partition to take up the rest of the space. Then wait for it to finish, exit setup, and boot from your hard disk as usual.

EDIT: you can just install gparted on your ubuntu machine and run it from there. you can either find it in the ubuntu software center or use the command "sudo apt-get install gparted"

---

### Post by Thryn on 2010-08-09
(new_buntu's method should work too)

I think to edit partitions that have an OS in them, you have to not be running that os. So you'll need a LiveCD/Thumb drive (the application you need, GParted, has its own cd). So get that running, and run gparted (if running an OS live CD). It requires root/super user permissions. Then you'll need to delete the Mythbuntu partition, and any associated swap partitions (unless you were sharing swap) and expand your Ubuntu partition to fill the space. Wait for it to finish and reboot your computer. Of course copy any files you want to keep to the Ubuntu partition or another hard drive first.

---

### Post by -kg- on 2010-08-09
> **Thryn said:**
> (new_buntu's method should work too)

I think to edit partitions that have an OS in them, you have to not be running that os.

Quite true:

> I recently install Mythbuntu in a 400gb partition [COLOR="Red"]alongside 100gb partition with my Ubuntu on.[/COLOR]

Boot into your regular Ubuntu installation, install Gparted from the repositories, run it, and delete the 400GB partition with Mythbuntu on it.  After doing that, open a terminal and run:

```
sudo update-grub
```

...and that will remove the Mythbuntu entry in the GRUB menu.

If you want to expand your Ubuntu partition to take the whole hard drive, you'll need to boot to a Live CD to expand it.  As Thryn pointed out, you can't edit a partition that you are booted to, or have mounted on the OS.  If you want, you can create another separate partition in the free space and it won't require booting to the Live CD.  Of course, you'll have to mount it from your installation and create an entry in your fstab file.

For further information on partitioning operations, read at the link in my signature block.  For further information on the fstab configuration file, read at:

[How To Fstab]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by Peterfc on 2010-08-09
Thanks Guys

I understand all that you say. I hope that all goes as it should

Thanks

Peter

---

