---
title: "How to optimize Ubuntu for SSD?"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by madsc89 on 2009-06-09
Update: Se the sixth reply for question about NILFS.

I'll post here as well because I don't seem to get an answer anywhere else, and because some aspects of the question are related to me not being too sure on commands.

Here goes:
In a fedora forum, I found this list for SSD-optimalization. I've just baught a new laptop with a Kingston 80GB SSD (which is a rebranded Intel X25-M), and plan to install Ubuntu on it. I'm going to run dual boot with W7 for games.
What I understand so far, is that I should use ext4 without journaling, and that I should do some other tweaks.
The question is: Which parts of this list should I do, What needs to be changed in order for it to work in Ubuntu, What can I skip, How should I partition the drive bearing in mind it's a SSD, and is there anything else I should do?
Quote:
> SSD Optimization
Perform the following if you’re using an SSD. If you’re using a hard drive you can skip this section.
Create Ramdisks to Store Frequently Written Areas

1. Edit your /etc/fstab file. Add the following lines.
tmpfs /var/log tmpfs defaults 0 0
tmpfs /tmp tmpfs defaults 0 0
tmpfs /var/tmp tmpfs defaults 0 0

Disable Access Time Attributes

1. Edit your /etc/fstab. Modify the root partitions settings. Add noatime and nodiratime to defaults.
/dev/sda2 / ext4 defaults,noatime,nodiratime 0 0

Optimizing the Kernel

1. Add the following to your /etc/rc.local file.
# Economize the SSD
sysctl -w vm.swappiness=1 # Strongly discourage swapping
sysctl -w vm.vfs_cache_pressure=50 # Don't shrink the inode cache aggressively

# As in the rc.last.ctrl of Linpus
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate_max > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate

echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo 20 > /proc/sys/vm/dirty_ratio
echo 10 > /proc/sys/vm/dirty_background_ratio

echo 1 > /sys/devices/system/cpu/sched_smt_power_savings
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo 5 > /proc/sys/vm/laptop_mode

#Decrease power usage of USB while idle
[ -w /sys/bus/usb/devices/1-5/power/level ] && echo auto > /sys/bus/usb/devices/1-5/power/level
[ -w /sys/bus/usb/devices/5-5/power/level ] && echo auto > /sys/bus/usb/devices/5-5/power/level

/sbin/setpci -d 197b:2381 AE=47
/sbin/modprobe pciehp
/sbin/modprobe sdhci

Change the I/O Scheduler

1. Edit the /etc/grub.conf file. Add “elevator=noop” to the kernel line.
kernel /vmlinuz-2.6.27.5-117.fc10.i686 ro root=/dev/sda
Source: [http://forums.fedoraforum.org/showthread.php?t=215109](http://forums.fedoraforum.org/showthread.php?t=215109)

I've run Ubuntu for a year now, but I'm still not completely sure on commands.

Thank you.

---

### Post by Cowchip7 on 2009-06-09
I wouldn't worry about writes to an SSD. You'll be buying a new computer before you wear it out!

---

### Post by furialis on 2009-06-09
I'm not sure if the rules apply to all makes of SSD, but the OCZ [forums]("http://www.ocztechnologyforum.com/forum/showthread.php?t=54379") have some excellent information.

Just remember before you post questions, that the forum is for OCZ products. Ask questions generically if you can.

Some things you can do are to change the line in your fstab from reltime to noatime. You can also mount some cache folders to [RAM]("http://ubuntuforums.org/showthread.php?t=991205)

---

### Post by Miljet on 2009-06-09
I'm not familiar with all the recommendations listed, but the first few listed seem to be intended to minimize disk usage. Most SSDs tend to be much smaller than the disk based counterparts. (I read a post the other night where someone bought a new notebook with a 4 GB SSD!)

With an 80G drive, I wouldn't think you would have to take such drastic measures to conserve space. If you store a lot of media files, I would keep them on an external drive.

---

### Post by madsc89 on 2009-06-10
Thank you for the answers.

The reason for tweaking would be both reduced writes => Longer liftime of the SSD, and remove any delay-properties (which isn't smart on a SSD because of the low access time).

Thank you.

---

### Post by sdennie on 2009-06-10
That list looks like fairly standard things to do on most machines.  Some aren't directly disk related and some may not have any noticeable effect but, I don't see anything there that is harmful.  A number of those options are for power savings and not SSD performance and some are machine specific and may not work for you.  Setting the I/O elevator to noop is not something I've tried but, I could see how it might work well for an SSD.

---

### Post by madsc89 on 2009-06-11
I found that NILFS is a file system optimized for SSDs. Also I believe The newest Linux kernel, 2.6.30, supports this system. Is it unwise to install Ubuntu 9.04 on my new Intel X25-M using this file system? If not: how do I do it? Also, is there any tweaks I still should do?

Thank you so much for any reply in this somewhat difficult question. I expect my new computer ready for me at my local post office this Saturday, and for that reason, I would like to try this (or another preferred alternative) in the next days.

---

### Post by sdennie on 2009-06-11
> **madsc89 said:**
> I found that NILFS is a file system optimized for SSDs. Also I believe The newest Linux kernel, 2.6.30, supports this system. Is it unwise to install Ubuntu 9.04 on my new Intel X25-M using this file system? If not: how do I do it? Also, is there any tweaks I still should do?

Thank you so much for any reply in this somewhat difficult question. I expect my new computer ready for me at my local post office this Saturday, and for that reason, I would like to try this (or another preferred alternative) in the next days.

NILFS2 is marked as experimental in the 2.6.30 kernel so I wouldn't try it unless you are feeling adventurous and want to both compile your own kernel and try an experimental filesystem.

---

### Post by madsc89 on 2009-06-12
Ok.

Thank you.

Is ext4 the best system to use for my SSD?

---

### Post by MaXMhZ on 2010-03-04
> **Cowchip7 said:**
> I wouldn't worry about writes to an SSD. You'll be buying a new computer before you wear it out!

That might be true - but everyone buys an SSD for reliability AND speed.
If you don't optimize, it WILL slow down within days of heavy use, and weeks otherwise. That's a LOT of money wasted.

If you do not want to bother, stay with conventional Hard Drives.

That said, newer SSDs like the Kingston Vseries Gen2 have massively improved garbage collection and support ATA TRIM. This should help keep performance up over time.

---

