---
title: "i have a few questions"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by shaullx on 2008-12-26
1. what ubuntu should i install? 64 or 32bit? (i have athlon64)
will the 64 work better then the 32?
2. i have 2 HD on one of them i have 20-30gb free
i want to make a partition out of this space to install ubuntu on it
how do i do that?
3. is there a way to install ubuntu directly from a HD? i dont have any empty CD disks right now lol
4. how can i transfer files from ubuntu partition to other ntfs partitions? if i remember linux don't see ntfs partitions and windows doesnt see the linux partition
thanks.

---

### Post by billgoldberg on 2008-12-26
> **shaullx said:**
> 1. what ubuntu should i install? 64 or 32bit? (i have athlon64)
will the 64 work better then the 32?
2. i have 2 HD on one of them i have 20-30gb free
i want to make a partition out of this space to install ubuntu on it
how do i do that?
3. is there a way to install ubuntu directly from a HD? i dont have any empty CD disks right now lol
4. how can i transfer files from ubuntu partition to other ntfs partitions? if i remember linux don't see ntfs partitions and windows doesnt see the linux partition
thanks.

1. I would go for the 32bit version, more support and apps.
2. Use the "gparted" live cd. Look at their documention for info on how to use the app (it's pretty easy).
3. Yes, as long as your pc can boot from usb (most can).

Simply format your external hdd (or usb stick) to fat32 and add a boot flag to it (with gparted), download an app called "unetbootin" and use that to put the ubuntu image file onto your external hdd.

Then boot from usb and install ubuntu like you would from cd.
4. Ubuntu can read and write to ntfs partitions out of the box.

And there are ext3 drivers and reiserfs drivers for windows.

---

### Post by zvacet on 2008-12-26
If you are going to install Ubuntu 8.10 and you want your Windows partition to see Ubuntu install [this.]("http://sourceforge.net/projects/ext2fsd")

---

### Post by shaullx on 2008-12-26
> **billgoldberg said:**
> 1. I would go for the 32bit version, more support and apps.
2. Use the "gparted" live cd. Look at their documention for info on how to use the app (it's pretty easy).
3. Yes, as long as your pc can boot from usb (most can).

Simply format your external hdd (or usb stick) to fat32 and add a boot flag to it (with gparted), download an app called "unetbootin" and use that to put the ubuntu image file onto your external hdd.

Then boot from usb and install ubuntu like you would from cd.
4. Ubuntu can read and write to ntfs partitions out of the box.

And there are ext3 drivers and reiserfs drivers for windows.

Thanks:)
I Will try now

---

### Post by shaullx on 2008-12-26
> **zvacet said:**
> If you are going to install Ubuntu 8.10 and you want your Windows partition to see Ubuntu install [this.]("http://sourceforge.net/projects/ext2fsd")

Thanks, but the other way around?
Linux can read&write to NTFS without any problem?
becouse i remember you need to run mount commands in the terminal or something

---

### Post by jamesrl on 2008-12-26
You have a amd64, a 64-bit processor.  I would go with the 64 bit version.  Back in the day there were a few more problems with running certain things (e.g., flash) but nowadays its not a big deal (and flash runs fine now).  And in some applications you can see big performance boosts.

[http://fedora.thelinuxpimp.com/files/amd64vsi386.pdf](http://fedora.thelinuxpimp.com/files/amd64vsi386.pdf)> Conclusions
Wide range of software was tested that covers major aspects of computers usage:
    1. Multimedia &#8211; audio, video and image processing.
    2. Server purpose software &#8211; LAMP stack and standalone HTTP server.
    3. Development tools &#8211; mathematical processing and compilation.
    4. Software for daily/home use &#8211; Mozilla Firefox web browser.
    5. Gaming &#8211; Nexuiz FPS game.
Following conclusions were made:
    1. It was clearly shown that most of applications have better performance in 64 bit environment.
    2. Performance degradation was observed in very few cases and it was very low &#8211; in about few
       percents &#8211; lame MP3 encoder, GNU compiler.
    3. Most of applications have 20-30% performance gain in 64 bit mode.
    4. In very few cases the gain was extremely high &#8211; 70-100% &#8211; mathematical processing in octave,
       image processing with ImageMagic.


I disagree about more support and apps.  You can install 32 bit apps in 64 bit mode.  Slightly more difficult (type a few lines from the command prompt), but doable.

[http://forums.amd.com/devblog/blogpost.cfm?threadid=93648&catid=317](http://forums.amd.com/devblog/blogpost.cfm?threadid=93648&catid=317)
> 

Benchmarks
First we picked some real world benchmarks for our 32-bit vs. 64-bit comparisons. Oggenc, Mencoder and Povray as well as some compilation tests. Furthermore micro benchmarks were used to show specific performance differences for syscalls and 64-bit arithmetics.

We set up three system configurations - a 32-bit installation, a 64-bit installation and a combination of 32-bit installation with 64-bit kernel to challenge the compat layer. All tests were performed on a dual-core AMD-K8(tm) processor with 1 GB RAM.

The tests showed that the penalty of using the compat layer instead of running your 32-bit application on a native 32-bit kernel is about 1-2 percent. So it is almost negligible.

64-bit took the lead in the media encoding tests. Our Povray and Mencoder benchmarks took about 5% less time in the 64-bit case, Oggenc even 25%. Just C-compilation tests showed a performance advantage of 5% to 8% for 32-bit versus 64-bit.

Native arithmetic performance (64-bit data types used in 64-bit software vs. 32-bit data types used in 32-bit) showed a gain of 10% for the 64-bit case. Using 64-bit data types on 32-bit and 64-bit in the arithmetic performance test showed that 64-bit is more than twice as fast as 32-bit.


Downsides of 64-bit
A 64-bit execution environment and 64-bit software surely have their downsides, too. First there is the larger memory footprint. Binaries get larger because of an increased pointer size and 64-bit operands. This leads to higher memory transfer load and therefore increases cache utilization.


Myths revisited

    * "You don't need 64-bit software with less than 3 GB RAM"
          o Performance improvement even on systems with less than 3 GB RAM 
    * "There are less drivers for 64-bit OS"
          o Irrelevant to Linux, hail open source  
    * "You will need all new software, all 64 bit"
          o 32-bit compat layer performs very well and is transparent 
    * "64-bit software is twice as fast"
          o Rarely the fact, software is usually optimized for 32-bit 


---

### Post by theozzlives on 2008-12-26
> **shaullx said:**
> Thanks, but the other way around?
Linux can read&write to NTFS without any problem?
becouse i remember you need to run mount commands in the terminal or something

Checkout this post by me:
[http://ubuntuforums.org/showthread.php?t=1015834]("http://ubuntuforums.org/showthread.php?t=1015834")

---

### Post by jamesrl on 2008-12-26
Linux can read/write to NTFS and its probably safe to do so now (use to be use at your own risk).  See [ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29") for instructions.

---

