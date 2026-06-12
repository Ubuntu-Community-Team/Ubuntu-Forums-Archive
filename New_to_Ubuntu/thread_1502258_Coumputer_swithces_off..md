---
title: "Coumputer swithces off."
date: 2010-06-05
forum: New to Ubuntu
---

### Post by Vege 4wd on 2010-06-05
Hi all. I am looking for some advice with my Acer laptop.
I am running Lucid. all has been going well since it was released.

3 times tonight it just turned off.  It does not feel hot. 
I am not sure how to look for error reports. 

anyone able to help??

---

### Post by mapes12 on 2010-06-05
How did you install Ubu? Aplpications>Accessories>Terminal ```
sudo fdisk -l
```

---

### Post by davec64 on 2010-06-05
Hi I've got an Acer A150 Netbook, and had the same problem.

In my case it was the system fan sticking which forced an automatic shutdown to prevent damage and hence not feeling particularly hot. After a lot of googling(!) the solution was to lightly tap arond the base where the fan was located to free it. I know not very scientific! it did the trick for me.
i did read with the Acer Netbooks that the fan was poorly located and prone to this happening.

If you feel confident you could always remove the base and check for a build up of dust around the fan.

Hope that helps!

---

### Post by Vege 4wd on 2010-06-05
hi Mapes12. I installed with a live cd. Burnt iso.

davic64 sounds like it. I will check the fan out thanks.

---

### Post by Vege 4wd on 2010-06-05
Hi again. This is what I got from the terminal.

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b3696

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14220   114220032   83  Linux
/dev/sda2           14220       14594     2998273    5  Extended
/dev/sda5           14220       14594     2998272   82  Linux swap / Solaris
aaron@aaron-laptop:~$ 

Cant see any problems myself.

---

### Post by AndyS_UK on 2010-06-05
Hi folks.
I've also had this problem for a while, now. Always happens at ~60% battery remaining - with both a 3-cell Li-ion and a 6-cell. I contacted Acer and was told it may be a BIOS problem, and they'd flash it for £54 (yeh, right!).
Having installed windoze to flash the bios (now on verson 3310, on an aspire one ZG5 b.t.w), I found that battery life was 2hr30 +, but the OS swallowed 7.9 of 8Gb available!
SO - returned to 10:04 variant (as upgrade from 9:10) and I find the battery still dies (not standby or hibernate, 'cos power light is on permanently as is the wifi led) at ~60%.
Sensible suggestions anyone?
Cheers,
AndyS. :confused:

---

