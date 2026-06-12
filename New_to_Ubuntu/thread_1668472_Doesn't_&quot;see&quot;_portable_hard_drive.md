---
title: "Doesn't &quot;see&quot; portable hard drive"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by PaulHA2 on 2011-01-16
Hi everyone. I'm running Maverick. I have a 250g portable hard drive that I recently formatted (FAT) and now the computer doesn't see it when I plug it in. It sees other portables just fine. I'd gladly re-format it in another format, but cannot do so if I cannot access it. I imagine there's a code-based solution to this, but I'm a recent convert from Windows and still tend to go GUI (shame!). 

Any help would be greatly appreciated.

-p.

---

### Post by coffeecat on 2011-01-16
> **PaulHA2 said:**
> still tend to go GUI (shame!). 

If you don't mind, we'll try the terminal. :wink: It'll be quicker and tell us more.

Plug the drive in and switch it on (if it has its own power supply). Now open a terminal and post the output of these two commands:

```
sudo fdisk -lu
dmesg | tail
```You will be prompted for your password for the first command. Just type away - it is going in but you get no visual feedback.

Please post the output in [noparse][CODE][/CODE[/noparse] tags for readability. You can use the # icon in the toolbar above the message field. The output will tell us what, if anything, the system is seeing.

Questions: is this a laptop-sized 2[FONT=Arial]½ [/FONT]inch drive or a full-size 3[FONT=Arial]½ [/FONT]inch one? If a 2[FONT=Arial]½ [/FONT]does it have a second USB cable for power? If it only has one cable, sometimes you don't get enough power from the USB port. Try another port.

---

### Post by PaulHA2 on 2011-01-16
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ec17d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   959057919   479527936   83  Linux
/dev/sda2       959059966   976773119     8856577    5  Extended
/dev/sda5       959059968   976773119     8856576   82  Linux swap / Solaris

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
1 heads, 63 sectors/track, 7752336 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0127cbe0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   488392127   244196032+   7  HPFS/NTFS
polarbear@polarbear-main:~$ dmesg | tail
[58304.247459] scsi 21:0:0:0: Direct-Access     Seagate  Backup           0130 PQ: 0 ANSI: 4
[58304.248436] sd 21:0:0:0: Attached scsi generic sg2 type 0
[58304.249622] sd 21:0:0:0: [sdd] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[58304.251824] sd 21:0:0:0: [sdd] Write Protect is off
[58304.251834] sd 21:0:0:0: [sdd] Mode Sense: 2f 08 00 00
[58304.251841] sd 21:0:0:0: [sdd] Assuming drive cache: write through
[58304.255565] sd 21:0:0:0: [sdd] Assuming drive cache: write through
[58304.255578]  sdd: sdd1
[58304.321469] sd 21:0:0:0: [sdd] Assuming drive cache: write through
[58304.321481] sd 21:0:0:0: [sdd] Attached SCSI disk
polarbear@polarbear-main:~$ 

```

I believe it's a2.5 inch, but it's enclosed, not one I put together--the one I made w/ an old drive and an enclosure worked fine--but that doesn't matter, i think, because I was able to use/see/format the drive in question before I formatted it, always with a single cable. 

Thanks!

-p.

---

### Post by PaulHA2 on 2011-01-16
Sorry for multiple submissions, something messed up.

---

### Post by PaulHA2 on 2011-01-16
Sorry for multiple submissions, something messed up.

---

### Post by PaulHA2 on 2011-01-16
Sorry for multiple submissions, something messed up.

---

### Post by PaulHA2 on 2011-01-16
Sorry for multiple submissions, something messed up.

---

### Post by PaulHA2 on 2011-01-16
Sorry for multiple submissions, something messed up.

---

### Post by PaulHA2 on 2011-01-16
Sorry for multiple submissions, something messed up.

---

### Post by coffeecat on 2011-01-16
It's being seen OK as sdd, but it's formatted NTFS, not FAT. Which doesn't matter. It should be automounted but occasionally some drives don't, perhaps because of some conflict between the drive firmware and the USB driver. Only a guess that, but a nuisance when it happens. Although that doesn't explain why you were able to see it before. Odd.

A couple of things to check. Plug it in and if a nautilus (file browser) window doesn't open, see if you can see it in the Places menu. If it's not there, try this from the terminal:

```
udisks --mount /dev/sdd1
```

---

### Post by PaulHA2 on 2011-01-16
```
polarbear@polarbear-main:~$ udisks --mount /dev/sdd1
Mount failed: Error mounting: mount: you must specify the filesystem type 
```

I'll also try it on my other machine (lubuntu 10.10) and see if that tells me anything...

-p.

---

### Post by coffeecat on 2011-01-16
> **PaulHA2 said:**
> ```
polarbear@polarbear-main:~$ udisks --mount /dev/sdd1
Mount failed: Error mounting: mount: you must specify the filesystem type 
```

I thought udisks was intelligent enough to work out the filesystem type itself. Ho hum. :)

Try this:

```
udisks --mount-fstype ntfs /dev/sdd1
```

---

### Post by PaulHA2 on 2011-01-16
```
polarbear@polarbear-main:~$ udisks --mount-fstype ntfs /dev/sdd1
Usage:
  udisks [OPTION...] udisks commandline tool

Help Options:
  -h, --help                   Show help options

Application Options:
  --enumerate                  Enumerate objects paths for devices
  --enumerate-device-files     Enumerate device files for devices
  --dump                       Dump all information about all devices
  --monitor                    Monitor activity from the disk daemon
  --monitor-detail             Monitor with detail
  --show-info                  Show information about a device file
  --inhibit-polling            Inhibit polling
  --inhibit-all-polling        Inhibit all polling
  --poll-for-media             Poll for media
  --set-spindown               Set spindown timeout for drive
  --set-spindown-all           Set spindown timeout for all drives
  --spindown-timeout           Spindown timeout in seconds
  --inhibit                    Inhibit the daemon
  --mount                      Mount the given device
  --mount-fstype               Specify file system type
  --mount-options              Mount options separated by comma
  --unmount                    Unmount the given device
  --unmount-options            Unmount options separated by comma
  --detach                     Detach the given device
  --detach-options             Detach options separated by comma
  --ata-smart-refresh          Refresh ATA SMART data
  --ata-smart-wakeup           Wake up the disk if it is not awake
  --ata-smart-simulate         Inject libatasmart BLOB for testing

See the udisks man page for details.

```

Also, no better result on the lubuntu machine.

---

### Post by coffeecat on 2011-01-16
Hmm. It seems  udisks is not going to co-operate.

Open System > Administration > Disk Utility. Can you see it there? If so, try reformatting it and see if that helps. If not, install Gparted from Software Centre or from Synaptic and I'll take you through creating a new partition table on the drive. Bit of a long shot that, but it might help.

---

### Post by PaulHA2 on 2011-01-16
YES! Saw it in the disk utility, reformatted, it popped up on the desk top.

Thanks so much. This whole Ubuntu thing rocks. Great community support!

-p.

---

### Post by coffeecat on 2011-01-16
I'm glad to hear it. As I posted last it came to me that it could have been as simple a thing as a corrupted filesystem. Ubuntu will refuse to mount a damaged NTFS filesystem, but by reformatting it you've effectively solved that.

By the way, if you use NTFS on an external drive, make sure you have Windows available to be able to run chkdsk if you ever get filesystem corruption again with valuable files on the drive. NTFS is a Microsoft filesystem and although read and write to it in Linux is reliable, there is no Linux repair tool for it as comprehensive as Windows' chkdsk.

Good luck, and happy Ubuntu-ing!

---

### Post by tikitikimaji on 2011-01-24
[QUOTE=coffeecat;10364841]If you don't mind, we'll try the terminal. :wink: It'll be quicker and tell us more.

Plug the drive in and switch it on (if it has its own power supply). Now open a terminal and post the output of these two commands:

```
sudo fdisk -lu
dmesg | tail
```


Sorry to hijack the thread, but I had a problem getting my USB flash drive read also, so I put the codes into a terminal, think you could help me out too?

this it what I got:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x27002700

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    83923559    41960756    7  HPFS/NTFS
/dev/sda2        83923621   312576704   114326542    5  Extended
/dev/sda5        83923623   306616589   111346483+  83  Linux
/dev/sda6       306616653   312576704     2980026   82  Linux swap / Solaris
nik@nik-laptop:~$ dmesg | tail
[ 7981.712177] usb 2-2: device descriptor read/64, error -71
[ 7986.936148] usb 2-2: device descriptor read/64, error -71
[ 7987.153155] usb 2-2: new full speed USB device using uhci_hcd and address 6
[ 7992.273155] usb 2-2: device descriptor read/64, error -71
[ 7997.496168] usb 2-2: device descriptor read/64, error -71
[ 7997.713159] usb 2-2: new full speed USB device using uhci_hcd and address 7
[ 8003.125133] usb 2-2: device not accepting address 7, error -71
[ 8003.237164] usb 2-2: new full speed USB device using uhci_hcd and address 8
[ 8008.645073] usb 2-2: device not accepting address 8, error -71
[ 8008.645105] hub 2-0:1.0: unable to enumerate USB device on port 2


Any thoughts or suggestions would be greatly appreciated.  It's weird with this stick drive because it was working fine one day, then started acting up after I started messing with virtual box.

Thanks,

---

