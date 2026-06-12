---
title: "Installing Ubuntu in free space?"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by JDuc on 2008-12-31
I'm interested in installing Ubuntu in the 40 gigs of free space that I have on my Windows laptop.

Currently, this laptop is completely dedicated to Windows.  All 120 gigs are dedicated to Windows.  I currently have 40 gigs of free space, that's not in it's own partition.

Per this picture: [http://www.psychocats.net/ubuntu/images/installinghardyplus10.png](http://www.psychocats.net/ubuntu/images/installinghardyplus10.png)

Would I just select the 'Guided - use the largest continuous free space' option?

This isn't a new Windows install btw.

Thanks for any information!

---

### Post by ugm6hr on 2008-12-31
> **JDuc said:**
> Would I just select the 'Guided - use the largest continuous free space' option?

No.

The continuous free space has to be unpartitioned.

Your options:
1. Repartition manually to create free space, and use the "free space" option.
2. Use the Guided - resize... and use freed space
3. Use Wubi to install within XP.

Or just install it in VBox (8GB is enough to experiment).

---

### Post by wolfen69 on 2008-12-31
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by balloooza on 2008-12-31
I would recomend downloading :
[http://sourceforge.net/project/showfiles.php?group_id=248002&package_id=302801&release_id=648596](http://sourceforge.net/project/showfiles.php?group_id=248002&package_id=302801&release_id=648596)
and get the first download, burn it to a cd and boot into it (like the ubuntu live cd) then when it comes up,
Start the partitioner, then click on your windows drive, (this is the big bar at the top)
Click the resize/move, then when the window comes up, make it smaller (I would recomend 30 gigs, not 40) Then make a new partition (click on the free area, not used by windows, and make a 25 gb partition, and use the ETC3 filesystem. Then click on the last remaining 5 gigs, make a new partition, and make it SWAP.
Click apply and wait and wait and wait.

I have not had much sucess with the partitioner built into ubuntu installer disk, this is also a great rescue disk when windows crashes (not as a result of this process, it is just smthing that happens :) )
I hope this helps.

---

### Post by donkyhotay on 2008-12-31
> **ugm6hr said:**
> No.

The continuous free space has to be unpartitioned.

Your options:
1. Repartition manually to create free space, and use the "free space" option.
2. Use the Guided - resize... and use freed space
3. Use Wubi to install within XP.


All of these options are correct but there are pros/cons to them. It might help to know if you are just wanting to try out ubuntu (at which point you would want to use wubi) or if linux is going to be a permanent part of your system then you would want to repartition.

---

### Post by JDuc on 2008-12-31
I've had it installed on another laptop for about a week now.  I'm liking it for sure, however, I'm a bit astonished at how much work it takes just to get something simple to work...like syncing my phone...lol

I'm getting ready to make a drive from the Dallas area to Las Vegas for the CES show (we compete in car audio pretty seriously and our sponsors want our car there), and I'm not wanting to take two laptops.  Since I know I'll have plenty of free time, I figured I would install Ubuntu in the free space so I could continue to learn it and mess with it while I had free time.

Eventually, provided I can get everything to work and can become comfortable with it, I'll switch completely (and as soon as someone develops a solid front end for the CarPC, I'll switch the CarPC to Linux as well...but no one has done that yet...:(

Thanks!

---

### Post by donkyhotay on 2008-12-31
I'd recommend wubi then since this sounds like a case of wanting to quickly throw ubuntu on a computer with the least hassle. Especially since you have it installed on another computer already.

---

### Post by JDuc on 2008-12-31
sweet - thanks guys!

I keep seeing a very quick BIOS bug notice upon boot....should I be worried about this?

(posting from the ubuntu laptop now)

Also, now that I've rebooted the other laptop, it's stuck at this prompt:

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [    31.311800] sd 4:0:0:0: [sdb] Assuming drive cache: wright through
[    31.413669] sd 4:0:0:0: [sdb] Assuming drive cach: write through
```Thoughts?

EDIT:

A quick search turned up this thread: [http://ubuntuforums.org/showthread.php?t=440912](http://ubuntuforums.org/showthread.php?t=440912)

I did have MagicISO installed, uninstalled it, and it still throws this error....:(

This is the same CD I used to install on the other laptop.  Before installing, I ran the check disk option and I made sure to burn the disk at the slowest speed that my burner would allow (8x).

---

