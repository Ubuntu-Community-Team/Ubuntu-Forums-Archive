---
title: "dual boot - Vista won't boot, always goes to recovery"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by bearsquirrel on 2011-06-09
[FONT=Arial][SIZE=2]Hello forums[/SIZE][/FONT],

[FONT=Arial][SIZE=2]This is my first post, so please be patient. I have a laptop running Vista on which I 
installed Ubuntu 10.04 from a USB drive using wubi. Now when I start the machine
it shows a black and white screen with different operating ssytems to choose from.
The last two entries on the list are Windows Vista and Rescue & Recovery. If I choose
Vista it boots up Rescue & Recovery, and I can never get to Vista. (The Linux works fine
and I wouldn't touch Windows again except I have to edit Word documents from other
people :().

Is there a way of fixing this short of going back to factory settings? I hope I have included
enough detail.

Thanks,
Bear&Squirrel
[/SIZE][/FONT]

---

### Post by wildmanne39 on 2011-06-09
> **bearsquirrel said:**
> [FONT=Arial][SIZE=2]Hello forums[/SIZE][/FONT],

[FONT=Arial][SIZE=2]This is my first post, so please be patient. I have a laptop running Vista on which I 
installed Ubuntu 10.04 from a USB drive using wubi. Now when I start the machine
it shows a black and white screen with different operating ssytems to choose from.
The last two entries on the list are Windows Vista and Rescue & Recovery. If I choose
Vista it boots up Rescue & Recovery, and I can never get to Vista. (The Linux works fine
and I wouldn't touch Windows again except I have to edit Word documents from other
people :().

Is there a way of fixing this short of going back to factory settings? I hope I have included
enough detail.

Thanks,
Bear&Squirrel
[/SIZE][/FONT]
Hi, one of these guide should help.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by bcbc on 2011-06-09
> **bearsquirrel said:**
> [FONT=Arial][SIZE=2]Hello forums[/SIZE][/FONT],

[FONT=Arial][SIZE=2]This is my first post, so please be patient. I have a laptop running Vista on which I 
installed Ubuntu 10.04 from a USB drive using wubi. Now when I start the machine
it shows a black and white screen with different operating ssytems to choose from.
The last two entries on the list are Windows Vista and Rescue & Recovery. If I choose
Vista it boots up Rescue & Recovery, and I can never get to Vista. (The Linux works fine
and I wouldn't touch Windows again except I have to edit Word documents from other
people :().

Is there a way of fixing this short of going back to factory settings? I hope I have included
enough detail.

Thanks,
Bear&Squirrel
[/SIZE][/FONT]

If you installed with Wubi - then did you also set the default OS to boot as Ubuntu and the timeout to zero?

If you didn't install with Wubi, then note that grub gets confused and often names the real Windows as recovery. So it might just require booting what grub calls the recovery. 
Check this by noting the partition, and then use "sudo fdisk -l" to see which partition has the boot flag set. That's the one you want.

---

