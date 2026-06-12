---
title: "Grub 2 delay"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by celticbhoy on 2009-10-30
I was wondering if anyone could shed some light on a small problem I am having, when I power up my PC it runs through the usual BIOS checks, and then the initial indication of grub shows 'Grub loading'. It then takes about 15 secs until grub actually displays on screen.

I have 2 hard drives, sda which has vista and 3 data partitions, sdb which has Ubuntu and swap partitions. 

I have tried grub installed on both drives, but no change.

What is causing the prob, and how do I go about fixing it?

---

### Post by philinux on 2009-10-30
There have been a couple of bug reports for this.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)

I would also search the now closed Karmic forum.

Grub2 is still beta. I guess we are the guinea pigs for lucid.

---

### Post by falconindy on 2009-10-30
Good news: Grub 1.97 was released on the 25th.
Bad news: This is an Ubuntu specific bug, not Grub.

Grub2 works just dandy on Arch Linux.

---

### Post by lovinglinux on 2009-10-30
> **philinux said:**
> There have been a couple of bug reports for this.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)

I would also search the now closed Karmic forum.

Grub2 is still beta. I guess we are the guinea pigs for lucid.

Yep, that's happening to me too. It happens when the mbr and grub are on different drives.

---

### Post by celticbhoy on 2009-10-30
> **lovinglinux said:**
> Yep, that's happening to me too. It happens when the mbr and grub are on different drives.

So if I just change the hard drives around in bios & re-istall grub I should be ok?

---

### Post by lovinglinux on 2009-10-30
> **celticbhoy said:**
> So if I just change the hard drives around in bios & re-istall grub I should be ok?

I guess so. Changing the boot order in bios didn't work for me, but it did for others. Nevertheless, my mbr is still on sda while the OS is in sdb.

---

### Post by Elfy on 2009-10-30
> Changing the boot order in bios didn't work for me, but it did for others. Yep - it worked here without reinstalling grub - I had already tried that fix.

---

### Post by HeinzVoerbakje on 2009-11-05
I have the same problem, I know how to swap the drives in the bios, but as the MBR is located in what is now called sda, changing sdb to sda will not boot anything.

So how can I reinstall Grub2 after changing the disk order? Boot from a live-cd, and then?

Thanks for the help!

HeinzVoerbakje

---

