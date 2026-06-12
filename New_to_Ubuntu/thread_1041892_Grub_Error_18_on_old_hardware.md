---
title: "Grub Error 18 on old hardware"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by MetalRampage on 2009-01-17
I am attempting to install Ubuntu onto one of my older pcs. It has a P3B-F motherboard (latest bios, 1008.4), 256 MB RAM, and a Maxtor 6Y160P0 hdd (160gigs) which is being reported under my bios with a chs capacity of 8422MB and a maximum LBA capacity of 8455MB. The bios also incorrectly identifies 1024 cylinders, 255 heads, and 63 sectors. According to this site, [http://www.superwarehouse.com/Maxtor_DiamondMax_Plus_9_160GB_Hard_Drive/6Y160P0/ps/193154](http://www.superwarehouse.com/Maxtor_DiamondMax_Plus_9_160GB_Hard_Drive/6Y160P0/ps/193154)
I have 16383 cylinders, 16 heads, but it doesn't specify the number of sectors. Not that it matters since the maximum value I can enter in my bios is 63 which seems too small.

I have come to understand that I am correctly receiving the Grub error 18, due to the previous problem. After reading some forums, I have discovered that I should probably try creating a small partition at the beginning of my drive as a boot partition.

Now I am at a loss. I don't have nearly enough experience with Linux to properly setup and configure GRUB so I am asking for assistance in partitioning and configuring GRUB. I would appreciate help in selecting partition sizes, labels, etc. As I have no idea what any of them do.

I would like to add that I have been using Windows 2000 prior, and it ran without a hitch. I did have 2 partitions though, like 40 and 120 or something like that. So it could be that my bios isn't lba48... but I don't think that should really matter since it only sees 8gigs anyway. I'm not trying to dual boot, just Ubuntu is fine.

One final point I would like to include. I would really, really prefer not to use a live cd to boot into Linux because my cd drive isn't working too well, though I'm sure it installs successfully. I could try another cd drive if it's necessary.

Thank you

---

### Post by bumanie on 2009-01-17
Have a [look here]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition"), there is a good explanation of making a /boot partition to avoid the grub error 18. Good luck.

---

### Post by MetalRampage on 2009-01-17
Hey thanks a lot for the help. I wound up not using that though. I felt it was easier to reinstall from scratch but I wanna chronicle what I did in case someone else has this problem.

With this information in hand, I made a boot partition (254 megs) (ext2), a main partition (150? gigs) (ext3), and a swap partition (756 megs, that's what it was before). Anyway, first I tried choosing the advanced option and manually specify where on the hdd I should install GRUB. I thought I should put it on the first partition, I think that's reasonable. Well, that got rid of error 18, but then I got error 15, which is some GRUB files missing. So then I tried reinstalling yet again (5th? 6th? time), but I didn't change any advanced options, it stayed at hd0 or something, which I found kinda strange, 'cause it's like it's not specified. But whatever, it works! For some reason while it's loading up Linux, the usual Ubuntu splash screen like the windows ones, there's nothing on the screen. In fact my monitor gives me a red warning message, "change output to 1680x1050" (that's my native resolution). But whatever, afterwards, it loads up fine.

Good luck to anyone else having this kind of problem.

---

