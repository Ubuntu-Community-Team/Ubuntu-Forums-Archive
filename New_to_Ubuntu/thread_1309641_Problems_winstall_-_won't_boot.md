---
title: "Problems w/install - won't boot"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by UT_Libertarian on 2009-11-01
Background -  was running windows xp, got a virus off the internet, though it would still boot in windows, decided to take the ubuntu plunge, no turning back.  downloaded 9.10 and 9.04 on other windows machine.  verified iso's and burned cd's.  When installing on pc, got error messages.  retried several times with both 9.10 and 9.04, once even got to the point of entering computer name etc., but it still won't boot after any attempt.  I can get it to run live off the cd, but still no success booting after install.  when running live off the cd, it mat take as much as 1/2 hour to finish loading.  sometimes it flashes error messages, not always the same, and rarely stay on the screen long enough to read them.  is there a utility available to check the integrity of the hd to isolate the problem?  Working two jobs, I usually only have slivers of time here and there to start an install and let it run while I'm at work.  In starting the first install, I selected use entire drive, so there's no turning back.  I will overcome!

---

### Post by kansasnoob on 2009-11-01
Do you know what your computers specs are?

Also, I know you checked the md5sum, but have you selected check disc integrity from the boot menu when you first start the Ubuntu live CD?

If it passes and says that no errors are found go ahead and select try without changes. Then from the live desktop go to Applications > Accessories > Terminal and post the output from these commands:

```
cat /proc/meminfo
```

```
cat /proc/cpuinfo
```

```
sudo fdisk -l
```

BTW that's a lower case L.

---

### Post by UT_Libertarian on 2009-11-01
Info returned (all in kb):

memtotal    477172
memfree        6164
buffers          64800
cached        268196
swapcached         0
active          158568
inactive        272540
active(anon)   80136
inactive(anon)  39656
active(file)      78432
inactive(file)   232884
unevictable             0
Mlocked                  0
hightotal                 0
highfree                 0
lowtotal         477172
lowfree              6164
swaptotal       1516904
swapfree        1516904
dirty                         0
writeback                  0
anonpages          98152
mapped              39112
slab                   27424
SReclaimable      19828
SUnreclaim          7596
Pagetables           2112
NFS_Unstable            0
Bounce                     0
Writebacktemp          0
Commitlimit    1755488
Commited_AS  324168
Vmalloctotal     536568
Vmallocused         4892
Vmallocchunk   526520
Hugepages....            0
hugepagesize        4096
Directmap4k       12288
Directmap4M     479232



cpuinfo

processor    0
Vendor ID   AuthenticAMD
CPU family  6
model         7
model name  AMD Duron(tm) processor
Stepping      1
CPU MHz     1211.891
cache size   64 kb
fdiv_bug         no
hlt_bug           no
f00f_bug         no
coma_bug       no
fpu                 yes
fpu_exception  yes
cpuid level         1
wp                   yes
flags    fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36
          mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up
bogomips   2423.78
clflush size      32
power management   ts




fdisk results:

Disk /dev/sda:   120.0 GB  120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
disk identifier: 0xfb45bf6b

device        boot   start     end        blocks       id       system
/dev/sda1                 1   14419   115820586    83       Linux
/dev/sda2          14420   14593      1397655      5       Extended
/dev/sda5          14420   14593      1397623+   82      Linuxswap/solaris


Disk/dev/sdb:     500MB  500563968 bytes
16 heads, 32 sectors/track,  1909 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier 0x00000000

Device       boot    start      end     blocks      id      system
/dev/sdb1     *           1     1910   488816       e     W95 FAT16 (LBA)

---

### Post by sandyd on 2009-11-01
> **UT_Libertarian said:**
> Info returned (all in kb):

memtotal    477172
memfree        6164
buffers          64800
cached        268196
swapcached         0
active          158568
inactive        272540
active(anon)   80136
inactive(anon)  39656
active(file)      78432
inactive(file)   232884
unevictable             0
Mlocked                  0
hightotal                 0
highfree                 0
lowtotal         477172
lowfree              6164
swaptotal       1516904
swapfree        1516904
dirty                         0
writeback                  0
anonpages          98152
mapped              39112
slab                   27424
SReclaimable      19828
SUnreclaim          7596
Pagetables           2112
NFS_Unstable            0
Bounce                     0
Writebacktemp          0
Commitlimit    1755488
Commited_AS  324168
Vmalloctotal     536568
Vmallocused         4892
Vmallocchunk   526520
Hugepages....            0
hugepagesize        4096
Directmap4k       12288
Directmap4M     479232



cpuinfo

processor    0
Vendor ID   AuthenticAMD
CPU family  6
model         7
model name  AMD Duron(tm) processor
Stepping      1
CPU MHz     1211.891
cache size   64 kb
fdiv_bug         no
hlt_bug           no
f00f_bug         no
coma_bug       no
fpu                 yes
fpu_exception  yes
cpuid level         1
wp                   yes
flags    fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36
          mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up
bogomips   2423.78
clflush size      32
power management   ts




fdisk results:

Disk /dev/sda:   120.0 GB  120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
disk identifier: 0xfb45bf6b
[B]
device        boot   start     end        blocks       id       system
/dev/sda1                 1   14419   115820586    83       Linux
/dev/sda2          14420   14593      1397655      5       Extended
/dev/sda5          14420   14593      1397623+   82      Linuxswap/solaris[/B]


Disk/dev/sdb:     500MB  500563968 bytes
16 heads, 32 sectors/track,  1909 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier 0x00000000

Device       boot    start      end     blocks      id      system
/dev/sdb1     *           1     1910   488816       e     W95 FAT16 (LBA)
looks ok to me.

have you tried memtest86?


p.s. try testdisk its a nice utility for checking drives.

---

### Post by darksideforge on 2009-11-01
Over a year ago when I first wiped Windoze and tried to install from the boot screen, I couldn't do it. I had to install by going to the "Try without changes" LiveCD desktop and double-click the icon.  I later learned from someone that it might've had something to do with legacy files on my laptop, even after wiping it.

---

### Post by sandyd on 2009-11-01
> **darksideforge said:**
> Over a year ago when I first wiped Windoze and tried to install from the boot screen, I couldn't do it. I had to install by going to the "Try without changes" LiveCD desktop and double-click the icon.  I later learned from someone that it might've had something to do with legacy files on my laptop, even after wiping it.
thtas what military-grade drive wiping is for :)

---

### Post by darksideforge on 2009-11-01
> **carlee said:**
> thtas what military-grade drive wiping is for :)

That's also what 85gr FMJ M-16 rounds are for...laptop HDD's make nice targets at 100M (iron sights).  Of course, I waited to do that til I had a nice backup formatted up with 8.10 (now 9.04...don't like 9.10 so much).   =)

---

### Post by UT_Libertarian on 2009-11-01
[SIZE=7]FINALLY![SIZE=2] After something like 25 attempts, a successful install.  When burning the CDs, the burn utility on the windows machine verified the data reporting a clean burn.  When checking the disk on the Ubuntu machine, various errors were reported in some of the files.  Hoping it would be something non-critical, attempted to proceed with the install anyway, only to crap out somewhere along the way.  Also, getting it to boot from the CD to a live session would take upwards of 20 minutes.   After several agonizing attempts, I swapped out the CD drive in the Ubuntu machine.  Now it loads in less than 1/3 the time.  and rechecking the CDs from within Ubuntu, I found a copy (9.04) that reported no errors. Now, after a clean install, (Woohoo!!!) this reply is posted from the Ubuntu machine, booted from the hard drive.  [SIZE=7]YEEHAW!!![/SIZE][/SIZE][/SIZE]
[SIZE=2]
Anyway, I appreciate all the support and assistance and encouragement from everyone.  Having read of some of the bugs with 9.10 am I better served staying with 9.04 for the time being, since the majority of my use will be Firefox?
[/SIZE]

---

### Post by darksideforge on 2009-11-02
carlee may have more input on this since she's a 9.10 tester, but I feel like 9.04 is faster on my dated laptop and (and this is purely opinion, not fact) I feel like there's less "windows-like fluff" in 9.04.

That being said, one of the main benefits of 9.10 is the integration of UbuntuOne and EC2 and Cloud computing in general. If you're moving in that direction, you should be able to go to System-->Administration-->Synaptic Package Manager and click the "Upgrade Available" button and avoid downloading a completely new .iso image and reinstalling.  Then again, now that you're on an Ubuntu box, downloading and burning a 9.10 .iso would let you experiment with the LiveCD to see if you like it.

---

### Post by sandyd on 2009-11-02
> **UT_Libertarian said:**
> [SIZE=7]FINALLY![SIZE=2] After something like 25 attempts, a successful install.  When burning the CDs, the burn utility on the windows machine verified the data reporting a clean burn.  When checking the disk on the Ubuntu machine, various errors were reported in some of the files.  Hoping it would be something non-critical, attempted to proceed with the install anyway, only to crap out somewhere along the way.  Also, getting it to boot from the CD to a live session would take upwards of 20 minutes.   After several agonizing attempts, I swapped out the CD drive in the Ubuntu machine.  Now it loads in less than 1/3 the time.  and rechecking the CDs from within Ubuntu, I found a copy (9.04) that reported no errors. Now, after a clean install, (Woohoo!!!) this reply is posted from the Ubuntu machine, booted from the hard drive.  [SIZE=7]YEEHAW!!![/SIZE][/SIZE][/SIZE]
[SIZE=2]
Anyway, I appreciate all the support and assistance and encouragement from everyone.  Having read of some of the bugs with 9.10 am I better served staying with 9.04 for the time being, since the majority of my use will be Firefox?
[/SIZE]
Its best to wait a few more weeks. it seems that the current karmic kernel is a bit buggy and some of the drivers (esp. wireless) are not functioning properly. Plus, some people (like me) are getting some random crashes and other weird problems.

If the majority of your computer use is firefox, you can install the latest version (3.5) on your current OS installation by installing the package firefox-3.5.
A new menu item will be created called "shireketo". 

having said all that, you **can** use 9.10 right now, by running
```

sudo upgrade-manager -d

```
or update-manager, i can't remember which one it is.

---

