---
title: "Insall trouble"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by Longshankss on 2011-02-10
Hi,

I just converted to Ubuntu, and is, to say the least, very satisfied. Great OS, nice feel, good handling and so on. But alas, I encountered some trouble installing. I tried Linux mint Julia first, from a burned DVD, and it randomly cut the power to my computer at will. So after a few runs, I finally managed to make the install, only to realize this was not what I was looking for. I made a bootable usb of the Ubuntu 10.10 x64 and tried to install this instead. And this time around, it cut the power again. No warning of any kind, just went black. Powered it up again, started install over, and got a bit further, bang. 4-5 times more before i had the OS installed. When i turn on my computer, I'm directed to a dos-like login-screen, and after a minute or two it automatically logs on.  Now if I go online and watch flash-videos,it cuts the power.

1. How do I permanently bypass the "dos login" and get a fast boot up?
2. How do I stabilize my OS, so to watch youtube, and the like unhindered? Do I need a recovery-disc of some sort?

My computer is a zepto 6625wd,intel c2 t9300 duo 2,5 GHz 800MHz, 4GB ddr2 ram, 1GB turbo memory, 250GB SATA 7200 rpm HDD, and nvidia GT8600 512MB dedicated memory.

I'm an ubuntu-beginner, and would very much appreciate any help.

---

### Post by cariboo on 2011-02-10
It sounds like you have an overheating problem, make sure the video adapter fan and heat sink are clean, use the laptop on a unobstructed flat surface.

---

### Post by Longshankss on 2011-02-10
Thanks, I had actually thought about blowing the sh*t out of it, but is that also the reason it halts in the "dos"??

 And can cleaning the fan and sink really "cure" it from spontaneously shutdowns? 

It's positioned on a wodden tv-furniture, and nothing around it.

---

### Post by MJRSnyder on 2011-02-10
Sounds like a hardware problem.  I would check the power supply first, try swapping it out for another one (if you have one).  Once you get it sorted out you should probably just reinstall Ubuntu and that should fix the login "DOS" issue.

---

### Post by JC Cheloven on 2011-02-10
So, if I understood correctly, you have now an ubuntu x64 install, but it randomly reboots by itself. Specially when you do something demanding, as watching videos. It also happened in live sessions.

It could be a problem with your ram. Please choose the "memtest" entry at the grub menu, and let it run for an hour or so, to see if it finds any errors. 

Additional customary question: does it happens with other OS? (windows) If so, a hardware problem is definitely to be considered. 

There are tools in the repos to monitor the temperature of the cpu and hard disks. Search for "temperature" in synaptic. You can use that to discard (or not) heating as the root of your problems.

... no more ideas in this very moment.

---

### Post by ninthcaptain on 2011-02-10
OK so I am having the same issue as the original poster. I have an awesome system and after I installed ubuntu my computer restarted and I went into ubuntu and my computer crashed with my screen lookin like it was fried with images from my Win7 desktop. I hard powered off and restarted, went back into ubuntu and selected for graphic safe installation. The installation completed and my pc restarted again. When it started back up I went into ubuntu and picked ubuntu-linux-generic and the colorful ubuntu loading page came up but after it loaded I was sent to a dos like black background page where it told me to enter my user name and password. After i did i was still stuck in the DOS like world. what went wrong?

---

### Post by Longshankss on 2011-02-11
***"So, if I understood correctly, you have now an ubuntu x64 install, but it randomly reboots by itself. Specially when you do something demanding, as watching videos. It also happened in live sessions."***

Correct, I have the x64 install, but it does not reboot. When watch flash full screen, it cuts the power. A small click, and lights out, no reboot. when i switch on my pc again, it's stuck on the brand/bios-selection screen, and I have to "hard power off and boot up again. It does not do this when I watch video files in the sm player(avi, mkv, wmv ect.) Last night it also cut the power, while I was importing my music files into banshee (lot of files).

And when I say cut cut the power,I mean like, the battery wasn't inserted, and the power cord got pulled.

I run my setup through a vga cable on my tv, 32 inch sony flatscreen, 1078x768 60Hz, but ubuntu is set to 1360x768, and it displays fine on the screen.

---

### Post by Longshankss on 2011-02-11
Could it have something to do with my partitioning? 

swap: 9,48 GB
extended: 9,48
ext4/boot: 223,41

---

### Post by JC Cheloven on 2011-02-11
> **Longshankss said:**
> Could it have something to do with my partitioning?
Hardly, in my opinion. You could post the output of "sudo fdisk -l" for us to see, but it isn't worth really: the behaviour you describe hardly could have anything to do with any system config.

More than likely you have a hardware problem. Be it a power supply problem, a cpu faulty cooling, or whathever. 
You can assest that by booting from other OSes, to see if the problem is reproducible. It can be windows, or a non-ubuntu based linux distro, as Puppy 4.3, SliTaz, Fedora or Mandriva (among many others). Be it live or installed.

Hope to be wrong :/
JC

BTW: to carry on running your pc in this state can't be any good. Electrical peaks never are for (the rest of your still working) hardware.

---

### Post by ninthcaptain on 2011-02-12
1

---

### Post by Clever_Username on 2011-02-12
To rule out overheating issues, please provide the output to the following command from a terminal:
```
grep -i temperature /var/log/messages
```

---

### Post by Longshankss on 2011-02-12
> You could post the output of "sudo fdisk -l" for us to see, but it isn't worth really: the behaviour you describe hardly could have anything to do with any system config.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000376fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29165   234259456   83  Linux
/dev/sda2           29165       30402     9936897    5  Extended
/dev/sda5           29165       30402     9936896   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c894b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953511424    7  HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x288711e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2      182401  1465128000    f  W95 Ext'd (LBA)
/dev/sdc5               2      182401  1465127968+   7  HPFS/NTFS

---

### Post by Longshankss on 2011-02-12
> To rule out overheating issues, please provide the output to the following command from a terminal:
Code:
grep -i temperature /var/log/messages

Nothing happens I'm afraid.....
Perhaps drivers are not found. I'm running maverick on an off-grid brand computer. 

Can you download software to discover which drivers could be missing? 
Or any kind of other software, which could help figure out the glitches, to further my cause and dream to stick it to microsoft? I'm a brand-new ubuntuist. Be gentle

---

