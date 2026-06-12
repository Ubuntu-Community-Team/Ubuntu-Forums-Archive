---
title: "installing windows xp after installing ubuntu"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by Dimitri_Sumlanacht on 2009-11-22
I am sorry that this question does not relate directly to Ubuntu, but rather to Windows XP.  I have installed Ubuntu on my computer as my primary operating system due to XP's various bugs and flaws and the constant virus' that plauge the system and completely formatted the Windows side, got rid of it all.  But now, I wish to reinstall Windows for primarily and pretty much only videogame reasons.  When I got to the part of the XP setup that asked me which partition to install Windows on it was all fine and dandy as I set aside about 90 gigs of space when I installed Ubuntu with Windows gaming in mind.  I clicked to use the free space and hit enter to install and now it is giving me the following message, "To install windows xp on the partition you selected, setup must write some startup files to the folowwing disk: 190780 MB Disk 0 at Id 0 on bus 0 on atapi [MBR]...... HOWEVER, this disk does not contain a windows xp-compatible partition.  To continue installing windows xp, return to the partition selection screen and creat a windows xp-compatible partition on the disk... yadda yadda yadda"  Anyways, I do just that, format the empty space and press enter, same message.  How do I make the free space Windows compatible?  I see no other options then install, delete partition and quit, with nothing obvious that would allow me to make the free space 'windows compatible'.  I understand this is a Windows question, but I figured that my fellow Ubuntu enthusiasts, at least some of you know of the pains of Windows and needing it for such purposes of gaming would be willing to help me now, in my time of need.

Thanks for any advice you may offer me.

---

### Post by Cheesemill on 2009-11-22
Is the space that you've set aside at the start of the disk?
Windows will only install onto the first partition.

---

### Post by danill2008 on 2009-11-22
Maybe you must try to reinstall Ubuntu and reformat the whole disk. If you want to reintall Ubuntu...just remeber to backup grub, because window's mbr is going to overwrite it. See the last post on [this]("http://ubuntuforums.org/showthread.php?t=1317263") thread for more info. Also [here]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm") is a link that may be of help to you...

---

### Post by Dimitri_Sumlanacht on 2009-11-22
No, the space was set aside at the end of the disk.  I really hate Windows.  Is that the only problem?

---

### Post by cliffbreaker on 2009-11-22
Well, you should remember one thing - you can't install windows xp after ubuntu - first you MUST install windows xp and then ubuntu - and bingo, you got a dual boot system. This happens because windows is such an egoistic system that it's loader thinks that windows is the only OS in galaxy)) lolz)

---

### Post by danill2008 on 2009-11-22
You can install Ubuntu first ([here]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")).....but it's much easier to install XP first and then Ubuntu

---

### Post by kansasnoob on 2009-11-22
> **Dimitri_Sumlanacht said:**
> No, the space was set aside at the end of the disk.  I really hate Windows.  Is that the only problem?

Windows not only wants to be first on the disc it demands to be in a Primary partition!

No logical partitions for Windows OS's. It's OK for NTFS storage, but not an OS.

---

### Post by Hazbeen on 2009-11-23
I've just had the same problem. I've seen messages elsewhere that its better to install Windows first but it was too late for me. I eventually got it sorted having tried the following advice:
1) format the partition using windows
2) I deleted Ubuntu from the first partition so that windows could have it; still no joy
3) I made my first disk into a single partition and reformatted it; same message from XP
4) I ran fixboot, fixmbr, and systemroot - this having fixed another contributors problem, but not mine
5) Finally what worked was I disconnected the second drive, Eureka.

I don't know which of 1) to 4) would have been necessary in any case...

---

### Post by Tahakki on 2009-11-23
The link above is what I used a while back.

---

### Post by trundlenut on 2009-11-23
I have recently done exactly this.  I installed XP on the second partition on my laptop's hard drive.  Unfortunately I can't find the link on the internet that had the useful info on it.

I used the dd command to copy the MBR and then created a new primary partition
formatted to NTFS and installed windows, then I used a ubunutu live CD to copy the MBR back and then amended menu.lst so that I had the option to boot into XP.

Here is the bit I had to add into menu.lst:

```
title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		16ebd3b8-3b60-4c72-8211-d6513664b5c2
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=16ebd3b8-3b60-4c72-8211-d6513664b5c2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Windows XP
root		(hd0,2)
makeactive
chainloader	+1
```

---

