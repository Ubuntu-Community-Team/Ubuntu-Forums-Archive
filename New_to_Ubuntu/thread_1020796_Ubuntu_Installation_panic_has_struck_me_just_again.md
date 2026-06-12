---
title: "Ubuntu Installation panic has struck me just again"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by uv2008 on 2008-12-24
Hi guys,

I will very shortly repeat my (not that interesting story): I have Vista only installed on my Dell laptop, and I want to add an Ubuntu partition, so I will have 210 GB Vista and 40 GB Ubuntu.
Using Vista, I have shrinked 40 GB out of 250 GB hard drive.
Then in the Ubuntu installation process I got to the partitioning part that got me really confused: there are two bars, for "before" and "after". On the "before" bar I could clearly see the area I shrank in white colour as "free space" (it was 18%, 40 GB so it must be this space). Then when needing to choose an option, I thought that the most reasonable one would be the "use largest continuous free space" (or something like that), but when I chose that option then the "after" bar showed 100% Ubuntu, and to me it seemed that this option would completely format my whole hard drive and make it only Ubuntu. Do you think that this option is still best for what I want? 

Many thanks for any hint.

---

### Post by ercferret18 on 2008-12-24
don't do that. just say "manual" and then partition it like that. using the contigous option will just delete windows.

---

### Post by laser on 2008-12-24
Hi

i have exactly the same problem as you uv2008.

ercferret18 could you or someone elarobate more as how to manually partition the spare space?

I have tried to do this, but when rebooting i get a grub error 17 as i suspect it cant find the MBR.

Like uv2008 i have about 20GB free to put ubuntu on.  Could someone please post a suitable partition structure.

Am i right in saying the grub error is caused beacuse it cant find the MBR?  When this happens, i then cannot get my windows OS to load as it just hangs on the grub screen.

Any info would be appreciated.  An output of fdisk -l is below:

root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xc3ab8d7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23032   174115840    7  HPFS/NTFS
/dev/sda2           23032       25842    21242880    c  W95 FAT32 (LBA)

Thanks in advance.

Rich

---

### Post by uv2008 on 2008-12-24
Thanks you ercferret18. Like laser, it would be of great help for me to have a link or an explanation regarding manual partitioning in the installation - I tried the first steps of it and stopped it because I couldn't find how to use only the specific bit where I actually want to put Ubuntu on and nothing else (or nothing less...).

---

### Post by sportscrazed2 on 2008-12-24
its an error in the installer i played russian rollete knowing i didn't have anything important on windows and i had the install disc so i just did the largest continuous free space and it worked of course i read about the error online first

---

### Post by Keen101 on 2008-12-24
Yeah, i'm pretty sure it's a bug in the installer.

If you want peace of mind you could try the alternate install disc instead. It's a text based installer, and i don't think it has the bug. Otherwise just do a manual partition i suppose.

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

normally largest continuous space should only use free space.

---

### Post by uv2008 on 2008-12-24
sportscrazed2, when you used the "largest continuous space" option - did it actually install Ubuntu just there and kept your Windows partition ok? And when you chose that option - do you remember if the "after" bar (the lower one) turned to be all Ubuntu? Because if that's the case then maybe there's a bug in this bar display? Anyways, if anyone can explain about the largest space or manual options it would be great.

---

### Post by sportscrazed2 on 2008-12-24
> **uv2008 said:**
> sportscrazed2, when you used the "largest continuous space" option - did it actually install Ubuntu just there and kept your Windows partition ok? And when you chose that option - do you remember if the "after" bar (the lower one) turned to be all Ubuntu? Because if that's the case then maybe there's a bug in this bar display? Anyways, if anyone can explain about the largest space or manual options it would be great.

yep everything worked out just fine both parttions in tact.  rather big error to make in an installer i too panicked and quit out install and came here first

---

### Post by kansasnoob on 2008-12-24
I'd suggest working from the Ubuntu Live CD first and going to System > Administration > Partition Editor (aka: Gparted).

I'd like to see a screen shot of Gparted.

BTW, you've done well so far! Vista should always be resized using it's own tools!

---

### Post by uv2008 on 2008-12-24
Cool, thanks guys. I'll give it a try now and will be back to tell you about it (well, if I still have at least one functional operating system left :-)).

---

### Post by sportscrazed2 on 2008-12-24
no problem i almost didn't even install ubuntu because of this bug but i am so glad i did.  i just clicked it hoped for the best and it when it worked i was so relieved.

---

### Post by kansasnoob on 2008-12-24
Oh, and which version of Ubuntu are you installing. I'd guess 8.10 (Intrepid).

The additional "art-work" in the installer adds to the confusion!

---

### Post by kansasnoob on 2008-12-24
> **laser said:**
> Hi

i have exactly the same problem as you uv2008.

ercferret18 could you or someone elarobate more as how to manually partition the spare space?

I have tried to do this, but when rebooting i get a grub error 17 as i suspect it cant find the MBR.

Like uv2008 i have about 20GB free to put ubuntu on.  Could someone please post a suitable partition structure.

Am i right in saying the grub error is caused beacuse it cant find the MBR?  When this happens, i then cannot get my windows OS to load as it just hangs on the grub screen.

Any info would be appreciated.  An output of fdisk -l is below:

root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xc3ab8d7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23032   174115840    7  HPFS/NTFS
/dev/sda2           23032       25842    21242880    c  W95 FAT32 (LBA)

Thanks in advance.

Rich

Similar problem yes! Identical NO!

Please start a new thread. It becomes impossible to give instructions to two different people in the same thread.

---

