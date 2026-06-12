---
title: "Help with Grub"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by Gr3ghammett on 2009-09-11
ok, here's my situation.

I have only linux running on my computer. i want to install windows. i use a windows cd and the windows installer cant see the hard drive. i know the problem is because of Grub. i am currently running off of an ubuntu live cd.

my question is, how do i get rid of the grub? i did some reasearch, tried some commands, but it's still there. i need to get rid of the partition. i have a 250 gb hard drive. when i use the fdisk utility it says all 250 is unallocated and free to use BUT when i use the GUI partitioner, it says i only have 232 gb. with fdisk, i hit d to delete everything (1-2 there's no 3 or 4 cause it tells me "no partition defined" when i do). when i do this it says "ok you have 250 gb free unallocated space". i hit w to save the changes, reboot, and grub still comes up and gives me error 22.

any help is greatly appreciated. before someone states it, i do have the recovery cd's but unfortunately, somehow it got scratched a little and it has problems reading one of the files off the disk, in which i have to abort the operation. thank you all.

---

### Post by Zzl1xndd on 2009-09-11
Grub is normally writen to the MBR so it might still come up after wiping the drive, However that being said, Windows Should still be able to see the hard drive. Do you know if you are using a Sata drive? If so you might need additonal drivers when booting from the Windows CD for it to be recognized.

---

### Post by Bucky Ball on 2009-09-11
[http://members.iinet.net.au/~herman546/p15.html#22](http://members.iinet.net.au/~herman546/p15.html#22)

That might help.

---

### Post by Gr3ghammett on 2009-09-11
its a scsi drive

---

