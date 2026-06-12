---
title: "Warning error on install at partition screen"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by MorrisseyJ on 2010-03-21
I am trying to do a dual install of Ubuntu onto a computer with the hard drive totally devoted to Windows XP. Using the live CD all goes fine until i get the partitioning screen.

I pick the guided dual install option, use the slider to set up the partion as i would like it and click 'forward'.

After sometime a dialogue box appears titled: Warning!

It says:
> The file system is reporting the free space as 2068839 clusters, not 2068849 clusters> 

I am left with two buttons: 'Ignore' or 'Cancel'.

I haven't had the nerve to 'ignore' so when i click 'cancel' i get a msg telling me that not enough free space was made and that i will now have to install manually.

I have not seen this in any of the tutorials that i have looked at. I have also not found a relevant thread on here.

Could someone tell me what is going on, should i click 'ignore' and can i easily get round this with a manual partition.

As you can probably tell i am new to this so basic explanations/instructions would be appreciated.

---

### Post by yeats on 2010-03-21
Have you read this?:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

The screenshots are from a previous Ubuntu version, but the steps are the same.

What's not mentioned explicitly as far as I can tell is that you will most likely want to defrag the WinXP installation, probably with more than one run.  Windows by default spreads itself, piecemeal, all over the hard disk, which the defragger helps with some.  Try defragging and otherwise cleaning up your XP installation, then retry.

---

### Post by buntudawg on 2010-03-21
Or this?:
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

---

### Post by MorrisseyJ on 2010-03-21
Hi, 

Yes, i have read both of those tutorials. 

I have now defragmented twice. I hadn't done this previously as i have just reinstalled windows and so didn't think that disk fragmentation would be an issue. 

So i now have a fresh windows install which has been defragmented twice.

Anyway, the problem persists. I now get the same message but with slightly different numbers - i think this might be because i have not placed the slider in exactly the same place.

Any suggestions?

---

### Post by srs5694 on 2010-03-21
I'm not extremely familiar with the errors that you might see in the Ubuntu installer; however, the message sounds to me like a warning about an inconsistency in the filesystem used on Windows. If so, the proper fix is to reboot into Windows and use the Windows tools to perform a disk check and repair. IIRC, you'll need to reboot Windows again once this is done. After that, try again with the Ubuntu installer.

---

### Post by MorrisseyJ on 2010-03-22
Solved, thanks.

A new problem now arose in that while Ubunut  was installing, after the partition, i got a message that the CD was  corrupt and that install would have to abort.

System eventually  hung and i had to power down. When i rebooted system went straight to  windows.

I am now not entirely sure how far along the install got  as i see the hard drive in windows is at the post-repartition size. I  don't fully understand the GRUB installer stuff but since it booted  straight to windows i am guessing that the GRUB did not install.

I'll  look around to see if there is another thread which covers this and if i  can't find one, post a new thread as i think this constitutes a new  topic.

Otherwise if anyone knows a way to check how far along i  am in the install and then suggest what might be the best order of  actions that would be greatly appreciated.

Thanks again for the  input.

---

