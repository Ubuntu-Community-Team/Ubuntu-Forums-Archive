---
title: "Help me understand what just happened - MBR adventures"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by knurledflanges on 2010-01-18
Alright, I believe I have things working now, but I'd like to confirm that I'm not missing anything I should do and also make sure I understand what might have gone wrong with an install of 9.10 I just did. I'm putting it in Testimonials because it's so long-winded and probably more tolerable to everyone else if viewed as a study of newbie mayhem, but I'd still be very grateful if anyone could advise me on any mistakes I may have made here and not picked up on yet. (Edit: Ack, put it in the wrong place, and I don't think I can change it myself).

I got a virus in XP, needed my computer to work and didn't have convenient access to a CD burner or USB drive, so I did a wubi install. Ditching Windows for good was kind of on my list of things to do anyway, so I took the opportunity. After confirming that Ubuntu/Xubuntu would work well on my rather old machine, and still not having easy access to an install CD or USB drive, I started looking for CD-less ways to wipe my system and install Ubuntu by itself before I became further committed to an install on top of a viral Windows whose bootloader I could only hope was unaffected. After backing up all my personal files on an external drive that would remain safely unplugged while I newbed around with partitions and such, I proceeded to try to use UNetbootin to copy the Ubuntu ISO onto an 2.2gb FAT32 partition on the 10gb drive (the master drive on my primary IDE cable) which also housed my 7.5gb Windows partition. This failed because it ran out of space because I think I misunderstood how Unetbootin works, and it seemed to also completely trash the Windows bootloader, because when I restarted my system it gave an error and couldn't find a boot record on that drive. (The wubi install was on another hard drive, a 40gb with 2 equal-sized partitions, which is the slave drive on my primary IDE cable. I also tried using Unetbootin to copy the ISO to the one of these that the wubi install wasn't on, and had similar results, although since there was no 'real' OS on that disk I suppose that means there was no MBR to trash).

So I went to a friend's house and made a real Ubuntu 9.10 CD and tried to fire up the install process. It quickly went to a black screen and hung, and then when I pressed a key it came out of the black screen and had some kind of error about initrd and squashfs (I know, if I really wanted to know what happened I would have written it down). I believe I tried loading the LiveCD too and something similar happened. ('I believe' as it was very late/early at this point.) I went through this several times. Thinking something the lines of the drive being totally trashed might have occurred, I put in a Puppy Linux CD I happened to have, which booted up no problem. I used gparted on that to reformat the 10gb drive for a single ext3 partition, which seemed to work fine. Then I put the Ubuntu CD back in and things worked on it. So I installed Ubuntu. I wanted to put it on the 40gb drive (the slave drive) and turn that drive into a single massive partition, so I set that up in the partition manager. On the last screen, before you click to begin the install, there's an 'Advanced' button that I clicked to see what was there. There's an option that lets you choose where to write the MBR, or something. Since Ubuntu usually does everything for you, I left it at the default setting and canceled out of the Advanced window and began the install, which worked fine.

I restarted the computer, went into BIOS and pointed boot priority to the drive I had just installed Ubuntu on, which I assumed I needed to do, then attempted to boot it up. I got some kind of 'No boot record' error. Uh-oh. Tried several times. Then I tried restarting with the Ubuntu CD, and used the option that's something like "Attempt to boot from first hard drive," which was able to load the install I just did (although I couldn't understand why at the time). I looked at the Ubuntu partition in Palimpset and noticed that the "Bootable" box wasn't checked on that partition, so I checked it, took the CD out and tried to boot again. It found something but then gave a different error message about there not being a boot record. Then I talked to a friend, got some ideas, fired up the install program again, went through to the end of the setup questions and clicked on that 'Advanced' button again, and saw that the default drive whose MBR to set up was 'hd0', ie the 10gb drive and not the one I had just installed to and pointed my BIOS at. So then I did some research and found the [Grub2 Community Documentation page]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") section on reinstalling GRUB. So I fired up the LiveCD again and did:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

```then restarted, saw that it was now working like I thought it should, and on the advice of the page did:
```
sudo update-grub
```First I assumed that it was the installer's fault for not writing to the right MBR. Then my brain started working and I realized that my error was assuming I needed to change my boot order (where for expediency's sake I'm in the habit of only having one entry in the list).

So now, if I'm not mistaken, there's a GRUB in the MBR of both disks that loads the same installation. Pretty silly story, huh? Is there anything else I should do here? Can someone fill me in on what might have been happening before with my initial problems loading the installer?

---

### Post by audiomick on 2010-01-18
If you go here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
and follow the instructions, the results.txt file that is produced will tell you where you have grub installed. If it is all too much, post it back here. Someone should be able to explain it...;)

---

### Post by knurledflanges on 2010-01-20
> **audiomick said:**
> If you go here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
and follow the instructions, the results.txt file that is produced will tell you where you have grub installed. If it is all too much, post it back here. Someone should be able to explain it...;)

Thanks, I have it pretty well figured out now. I just made the mistake of thinking I would need to assign boot priority to the drive I just installed on, and as I suspected the script shows now I just have grub on both drives. But everything seems to be working fine. Thanks for the reply!

---

### Post by theozzlives on 2010-01-20
You figured out the only thing (that I can see) you did wrong. You figured out a potentially complicated problem on your own, kudos for that!

---

