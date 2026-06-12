---
title: "Partitioning Help?"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by Tasogoro on 2011-05-30
So right now I'm dual booting Ubuntu 11.04 and Vista cause Vista got the blue screen of death. Nothing worked, so I switched operating systems. Now I've been trying to uninstall Windows Vista and the whole partition part is confusing me. I thought NTFS was a Windows thing and /dev/sda3 was taking up the most space. It had boot next to it so i didn't wanna screw anything up too much and i really don't know much about GRUB.I reformatted it to Ext 3 and shrunk it to almost minmum, leaving me with a gigantic amount of unallocated space  I tried to start vista again, the loader was still there but vista wouldn't start (mission accomplished?) However, my computer still only has about 500 MB of free space. Exactly how do i get rid of Vista completely, merge my partitions, and what do i want GParted to show my hard drive looking like to have the most free space I can get? Anything i should have NOT done lol?   Oh a 4.3 Gig file appears under the Network folder. It used to be called OS but changed after i shrunk it. What exactly is this? I opened it before when it was called OS and it had the files that were in my Vista folder (windows etc.)

---

### Post by Quackers on 2011-05-30
Welcome to UF :-)
Any partition change should be done from gparted in the live cd desktop - NOT your actual installed Ubuntu.

In gparted right-click on /dev/sda6 (swap partition) and select "swapoff" if it's not greyed out.

Delete /dev/sda3 partition, by right-clicking on it and selecting "delete". Click on the green tick in the toolbar to apply the change.

Right-click on /dev/sda4 (extended partition) and select "Resize/Move" and in the new box which opens type "0" in the field marked "Free space following" and press enter. You should see the first field jump in size. Click on OK
Click on the green tick in the toolbar to apply the change.

Right-click on /dev/sda6 and select "Resize/Move". In the box that opens up you want to move the partition right to the end of the disc (so that "0" appears in the field marked "Free space following" and the field marked "Free space preceding" jumps up in size). Click on the green tick to apply the change.

Right-click on /dev/sda5 (your Ubuntu partition) and select "Resize/Move" and expand that partition to whatever size you want (in MiB) or to the end of available space if you want to use it all). Click OK, then click on the green tick to apply the change.
This one may take some time.

---

### Post by wildmanne39 on 2011-05-30
> **Tasogoro said:**
> So right now I'm dual booting Ubuntu 11.04 and Vista cause Vista got the blue screen of death. Nothing worked, so I switched operating systems. Now I've been trying to uninstall Windows Vista and the whole partition part is confusing me. I thought NTFS was a Windows thing and /dev/sda3 was taking up the most space. It had boot next to it so i didn't wanna screw anything up too much and i really don't know much about GRUB.I reformatted it to Ext 3 and shrunk it to almost minmum, leaving me with a gigantic amount of unallocated space  I tried to start vista again, the loader was still there but vista wouldn't start (mission accomplished?) However, my computer still only has about 500 MB of free space. Exactly how do i get rid of Vista completely, merge my partitions, and what do i want GParted to show my hard drive looking like to have the most free space I can get? Anything i should have NOT done lol?   Oh a 4.3 Gig file appears under the Network folder. It used to be called OS but changed after i shrunk it. What exactly is this? I opened it before when it was called OS and it had the files that were in my Vista folder (windows etc.)
Hi partitioning gets tricky it would have been best if you were not keeping windows to just let ubuntu partition for you and it could have used the whole disk. I am going to give you a link to look at. If the empty space is in the right place it is easy to reclaim if it is not you have to resize but also move the partition before you can resize and this can cause data loss you should do a back up on a separate disk if you have files in home folder you want to keep just in case,If you have to move the partition then you will have to reinstall grub,and if your grub is on the windows partition if you wipe that out you will have to reinstall grub.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by Tasogoro on 2011-05-30
Ah thanks guys. I already backed up most of my stuff and the unallocated space is all the way on the right. The only thing i was concerned about was the booting. 
Right now I just put the disc in and selected Modify partitions, but I'm not exactly sure what to do after. Im guessing NOT press &quot;Install Now&quot; again if i want to keep the stuff already on there? It's a few gigs of music that i'd havta put on a bunch of USB's


Now it says theres an I/O error when i try and restart :/  Now it's working sheesh. Anyways, when i tried to resize sda/4 it said an error occured. None of my drivers have a boot flag now either but I don't know if thats a problem. When i restarted it worked just fine.   Weird, now the minimum i can make it is 1 higher than the max on sda 2 and 4

---

### Post by CaptainJamie on 2011-05-30
Sounds like too much of a mess to me. Can't you just put your important data on an external hard drive and erase the whole lot and start again? That is definitely what I'd do. Then install Ubuntu normally using the selection "install using whole hard drive" or whatever it says.
Optional: After that simply make a windows boot USB using wintoflash (on a separate computer if you have one, or does it work on wine?) partition 50GB of your HDD separately and pop Windows back.

---

### Post by Tasogoro on 2011-05-30
Eh, that's probably the best option if this doesn't work out. Don't really want windows, downloaded VMware player if i needa use Windows. If i do do that, is there an easier way of running it? I gave it executive rights and then it said it had a root problem. Had to switch to the root user and redownload -.-  I'm actually trying to get RID of vista. Got the blue screen of death, system restore didn't work. I thought one of the registry keys were corrupt, but that looks complicated as balls.

---

### Post by Quackers on 2011-05-30
If you install Ubuntu using the whole hard drive you will lose the Vista recovery partition too. Have you made a set of recovery discs and a repair disc? You may want to get Vista back one day! Without those you won't be able to.

---

### Post by CaptainJamie on 2011-05-30
You will be able to get Vista back but you'll have to pay for it again. Or make use of the extensive torrent sites such as the pirate bay, not that anyone on the Ubuntu forums including myself suggests doing anything illegal, but it's up to you. (The way I see it you've paid for Vista once, and using a torrent site to repair it and crack it is only fair since they sold you faulty goods in the first place - right I've said too much, this post is going to be deleted isn't it?)

---

### Post by satanselbow on 2011-05-30
> **CaptainJamie said:**
> You will be able to get Vista back but you'll have to pay for it again. Or make use of the extensive torrent sites such as the pirate bay, not that anyone on the Ubuntu forums including myself suggests doing anything illegal, but it's up to you. (The way I see it you've paid for Vista once, and using a torrent site to repair it and crack it is only fair since they sold you faulty goods in the first place - right I've said too much, this post is going to be deleted isn't it?)

If you have an authentic key for windows - the source of the media is irrelevant as long as you install the version for which you have a valid key ;)

"dd" - ing the recovery partition to an external drive (or just moving it to the very end of the drive) might be a better "just in case" option ;)

---

### Post by Tasogoro on 2011-05-30
Thanks for the help, ended up reinstalling it after getting an external hardrive.

---

