---
title: "Swap space."
date: 2011-03-03
forum: New to Ubuntu
---

### Post by Canime on 2011-03-03
So I installed Ubuntu 10.10 and due to some back issues and frustration during the installation, I didn't get the opportunity to give it any swap space. The window clearly states that it might not run as fast, and now that I am running a program that is taking some time to react, I am wondering if it is at all possible to add some swap space for the Linux installation?

I don't have any more room on the primary hard drive, just an external hd! Is this possible at all now? How much do I need? Can I employ a USB stick anywhere in this process?

---

### Post by Sef on 2011-03-03
Let's see how your partition on your internal hard drive is set up.

Copy and paste this command into a terminal (Applications > Accessories > Terminal):

```
sudo fdisk -l
```

Then copy and paste the results here.

---

### Post by Canime on 2011-03-03
[HTML]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f02d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5156    41413632    7  HPFS/NTFS
/dev/sda2            5157       19457   114871293    5  Extended
/dev/sda5           11114       19457    67020796    7  HPFS/NTFS
/dev/sda6            5157       11113    47849472   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10588463

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2    31008256   976760032+   7  HPFS/NTFS[/HTML]

Sdb1 is my external hard drive where some of my backups are. 1 and 5 are Windows 7.

---

### Post by NightwishFan on 2011-03-03
You can add a swap file using the process detailed here. It is no slower than a dedicated swap partition. (Disclaimer: I have never done this personally, but it seems simple enough)
[https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

---

### Post by Canime on 2011-03-03
Nice. With that said, I have added a swap file of 512 Mb. 

Also, my swappiness is set to 10 now, although when I run the 'free' command, check it out:

[HTML]Mem:       2059680    1314072     745608          0      56308     539492
-/+ buffers/cache:     718272    1341408
Swap:       524284          0     524284
[/HTML]

Its not being used at all.

---

### Post by NightwishFan on 2011-03-03
Swappiness of 10 will tend to cache less, it really does not improve performance. I would leave it as the default of 60.

If your swap is not being used it does not need to be used. Since it does detect it, it is working right. :)

---

### Post by mcduck on 2011-03-03
> **Canime said:**
> Nice. With that said, I have added a swap file of 512 Mb. 

Also, my swappiness is set to 10 now, although when I run the 'free' command, check it out:

[HTML]Mem:       2059680    1314072     745608          0      56308     539492
-/+ buffers/cache:     718272    1341408
Swap:       524284          0     524284
[/HTML]

Its not being used at all.

Looks fine, you have plenty of free RAM available so there's no reason for the system to start swapping.

Using a swap will not make your computer work faster, it makes it work *slower*, but allows it to handle tasks that would require more RAM than what you have. Hard drives are roughly 1000 times slower than your RAM is, so using that instead of RAM is something you want to avoid as long as possible, yet you still should have soem swap space available as even a slowly operating computer is better than one that can't do some task at all and instead complains that it doesn't have enough memory.

(another use for swap is hibernating the computer, all the data from RAM is written to the swap and then the computer is powered off. At the next boot the computer just reads the data from the swap into RAM and can then continue from where it left. This of course requires you to have at least as much swap space available as you have RAM)

---

### Post by Canime on 2011-03-03
Alright, I admit that having it is a good thing, but rebooting without the swap was easy and didn't take that much time. Its only when the memory usage gets to about 2GB's that I am concerned... And this can happen occasionally, like when I run some video, browsers and picture programs. I'm happy it was so easy and proud to do it so quickly :)

---

