---
title: "Ubuntu says partition is &quot;unusable&quot; in my quintuple-boot?"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by Pascal11110 on 2010-03-21
I get free Windows installations through my school, and since I had a 320 gig laptop drive lying around, I thought I might as well try booting all of the Windows versions, with Ubuntu, and use Grub (because Grub is Freakin awesome) as the boot manager. Getting my Windows OS's installed worked fine (XP 32-bit, Vista 32-bit, Windows 7 32-bit, Windows 7 64-bit). I gave XP a 40 gig partition, Vista a 50, and each of the 7's a 75 gig partition. I was going to use the remaining 50+ gigs at the end of the drive for my Ubuntu installation (Ubuntu Karmic 9.10 32-bit Live CD) but when I got to the partitioning stage it says that the unallocated 50 gigs that are left are "unusable". Is there someway I can get around this? And does anyone know why I am getting this message?

---

### Post by Pascal11110 on 2010-03-21
This is on my Dell XPS M1530 laptop with:
320 GB SATA 7200 rpm HDD
Intel Core 2 Duo T9300 2.5 Ghz
4 GB's DDR2 Ram
Nvidia 8600M 256 MB video card

---

### Post by srs5694 on 2010-03-21
This is the 4-partition limit of the Master Boot Record (MBR) partitioning scheme. I've heard of boot loaders that can juggle multiple MBR versions to work around the problem, but I've never used any of them, and I don't have any pointers. My very limited knowledge of them is also very old (from pre-XP days).

Another option might be to re-install some of your OSes so that at least two of them share a single primary partition. You could then create an extended partition (it counts as one of the four primary partitions) and use it for Linux. I don't know how amenable recent versions of Windows are to sharing their boot partitions, though. I do know that  the System Commander boot loader could do this in days gone by for older versions of Windows (Windows Me and earlier) and DOS.

---

### Post by corncob on 2010-03-21
[How to install and boot 145 operating systems in a PC]("http://www.justlinux.com/forum/showthread.php?t=147959")
Let us know if this is any good.  I haven't really read it myself -- I have six operating systems on three computers and can't find my email now lol.

---

### Post by Jakey_TheSnake on 2010-03-21
Or you could just uninstall Vista, it's pretty damned useless.

---

### Post by corncob on 2010-03-21
> **srs5694 said:**
> This is the 4-partition limit of the Master Boot Record (MBR) partitioning scheme. I've heard of boot loaders that can juggle multiple MBR versions to work around the problem, but I've never used any of them, and I don't have any pointers. My very limited knowledge of them is also very old (from pre-XP days).

I bought a Gateway notebook with Win7.  I left that as it was and installed Karmic.  Having plenty of space left I went on to install Ubuntu Ultimate and the system crashed.  When I recovered I saw in gparted (as well as grub) that win7 was taking up 3 bootable partitions -- #1 appeared to be disk recover, #2 restore, and #3 win7 itself.  I still had Karmic in the 4th partition but where I had installed Ultimate had become unallocated space -- so, in my own experience, I do go along with this 4 partition limit at least if they're primary or bootable ones.  I don't understand Pascal11110's situation though.  If win7 takes up 3 partitions each he already has 8.  Maybe its something to do with Grub?
Incidently, I had been told if I really wanted to install Ultimate I could delete partition #1 if I had win7 backed up on DVDs.

---

### Post by gmjs on 2010-03-21
You are only allow a maximum of four primary/extended partitions per disk.

You need to remove a primary partition and replace it with an extended partition.  You can then create many more logical partitions within that extended partition.

Hope that helps,

Graham

---

### Post by srs5694 on 2010-03-21
> **gmjs said:**
> You are only allow a maximum of four primary/extended partitions per disk.

You need to remove a primary partition and replace it with an extended partition.  You can then create many more logical partitions within that extended partition.

The trouble is that it's difficult to get Windows to boot from logical partitions. I've heard there are workarounds, but I've never looked into this issue in detail, so I can't provide pointers or further information.

FWIW, this whole primary/extended/logical thing (part of the MBR partitioning scheme) is a tiresome relic of computing's neolithic era (the 1980s). It was a pain even then, it caused trouble in the 1990s and in the first decade of the 21st century, but it was just too much hassle to fix. Now the issue is being forced by the fact that the MBR partitioning system is limited to 2TiB partitions (assuming the near-universal 512-byte sector size), and we're fast approaching that limit in disk size. The new [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) system does away with this awkward distinction, but Microsoft is holding it back. Windows -- even Windows 7 -- can't boot from a GPT disk if the computer uses a BIOS. Windows can at least use GPT on data-only hard disks, though. Linux can boot from GPT disks just fine. I've got five Linux computers that do just that. Unfortunately, GPT won't help with Pascal11110's problem because the whole problem is one of Microsoft's unwillingness to create a more flexible boot system.

---

### Post by corncob on 2010-03-21
GPT is something new to me.  I have an eeebox duel booting Karmic and Lucid-beta (no windows).  Does this mean I can add more than two operating systems so long as none are windows?

---

### Post by srs5694 on 2010-03-21
> **corncob said:**
> GPT is something new to me.  I have an eeebox duel booting Karmic and Lucid-beta (no windows).  Does this mean I can add more than two operating systems so long as none are windows?

You can do that with MBR, too. I've got one MBR-based system with six OSes on it, admittedly spread across two drives. The trick is that with MBR, some of your OSes must support booting from logical partitions if you're to have more than four OSes per disk. Linux is quite happy to boot from logical partitions, but Windows isn't. In fact, recent versions of Windows tend to hog two or even three primary partitions, which further reduces your options, although there are ways to get Windows to use just one primary partition. With GPT, though, so long as all your OSes support GPT, there are no practical limits. The default partition table size is 128 entries, but that value can be increased so long as there's room to do it. (If you create partitions that abut the main or backup partition tables, you won't be able to increase the partition table size.) You can boot an OS on any partition.

---

### Post by oldfred on 2010-03-21
Because windows has to boot from a primary partition does not mean it has to be installed in a primary partition. Windows standard install moves the critical boot files to the partition with the boot flag. As long as that partition is used to boot then the other paritions do not have to be primary. Just do not uninstall the primary boot partition version of windows or you break all of them. You also cannot directly boot from grub to each windows without effort - see link.

More info on windows multibooting:
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Way to boot windows in extended logical partition with lilo's MBR
[http://ubuntuforums.org/showthread.php?t=1367323](http://ubuntuforums.org/showthread.php?t=1367323)
Major windows repair with dual boot and logical partition
[http://ubuntuforums.org/showthread.php?t=1411495](http://ubuntuforums.org/showthread.php?t=1411495)
You mean ntdetect and ntldr can't be on a logical partition, that is right. Yes the boot is via sda1. sda1 is there only for that purpose.
But it still needs a primary to boot from.
[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)
[http://support.microsoft.com/kb/306559#f1](http://support.microsoft.com/kb/306559#f1)

---

