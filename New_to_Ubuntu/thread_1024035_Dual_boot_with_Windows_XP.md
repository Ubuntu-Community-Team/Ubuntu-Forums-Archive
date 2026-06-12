---
title: "Dual boot with Windows XP"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by bedachtm on 2008-12-28
I am trying to set up a dual boot (Ububtu first, Windows XP second) on a new PC (Intel Q6600, 4GB, 500GB). I am following a guide posted at [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

All goes as instructed (make backup of grub menu, make some space for XP (10GB) at the end of the HD) until I put the XP CD in  and try to boot from it.

I get a message "Windows is inspecting your hardware configuration..." for a few seconds on the screen, then - black screen and nothing. No apparent activity on the PC - it just sits there.

Anybody have any ideas?

---

### Post by zvacet on 2008-12-28
Is something wrong with CD(scratches,dust...)?

---

### Post by Captain_tux on 2008-12-28
It's not impossible to dual boot with Ubuntu first, but Windows OSs, shall we say, like to  "complain" if they're not the first OS installed.

Buena suerte!

---

### Post by bedachtm on 2008-12-28
No, the CD is fine. In fact, I have tried with two XP CDs, one sp1 in English and the other sp2 in Portuguese and both give the same result.

---

### Post by Captain_tux on 2008-12-28
Did you defrag and/or **chkdsk** before beginning the installation?

---

### Post by bedachtm on 2008-12-28
No, I did not. The PC is new, has only had Ububtu installed on it. The problem occured when I tried to boot from the Win CD - there should not be any reason why I can't get the CD to boot.

I just tried a VMware Virtual Machine to install from the same CD and it worked fine! I would rather have a dual boot setup, but I can live with a Virtual Machine environment if I have to. I really only need to run ONE win app - Photoshop Elements. All else I need can be done natively in Ubuntu.

---

### Post by zvacet on 2008-12-29
This is just a guess but did you check BIOS and see AHCI/IDE mode?If it is on AHCI  switch to IDE and then it should work.

---

### Post by mal_conductor on 2008-12-29
> **bedachtm said:**
> I am trying to set up a dual boot (Ububtu first, Windows XP second) on a new PC (Intel Q6600, 4GB, 500GB). I am following a guide posted at [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

All goes as instructed (make backup of grub menu, make some space for XP (10GB) at the end of the HD) until I put the XP CD in  and try to boot from it.

I get a message "Windows is inspecting your hardware configuration..." for a few seconds on the screen, then - black screen and nothing. No apparent activity on the PC - it just sits there.

Anybody have any ideas?
Bedachtm,

I had a similar problem.  Here is how I fixed it:
First I used 3 CD.
1. A Windows install CD that allowed me to delete the partitions on my hard drive
2. A Windows CD that I wanted to install
(CD 1 and 2 could be one and the same.  In my case the CD, containing the version of Windows I wanted to install, did not allow me to delete partitions on my hard drive.  I don't know why)
3. A Ubuntu install CD

What I did. (Note, I was unable to open the guide you followed)
1- With CD #1 I deleted all the partitions
2- With CD #2 I created a partition (I chose to split my hard drive in half)
3- With CD #2 I installed Windows.  I left the other half of the hard drive unformatted
4- With CD #3 I installed Ubuntu following this guide [http://www.herman.linuxmaniac.net/p24.html](http://www.herman.linuxmaniac.net/p24.html)

EXCEPT at STEP 4 of 7 I did something different.  I did not use the Partitioning tool.  I chose to install Ubuntu on the "largest continous free space"

For some reason Screen 014 on the guide did not look "exactly" the same for me.

A word of caution.
- Install Windows first and get basic Windows going (do not install all your Windows-based software just yet until you get Ubuntu stable).  I had to wipeout my hard drive a couple of times, including Windows, before I got Ubuntu working just right.  One of the reasons was that, in Ubuntu, I installed drivers/applications that conflicted with each other.  I did not know how to resolve the conflicts other than wiping out the hard drive and starting over.  And I had to delete everything since, for some unknown reason, the method I described at the beginning was the only way for me to install Ubuntu or I got problems similar to yours.
- Back up ALL your Windows stuff and make sure you have install CD's for your windows based software
- Also, eventhough you have not requested help on this.  May I suggest to follow this guide [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) for when it comes time to install all the other sound/video goodies you will need.  Following this guide helped me avoid creating conflicts by installing applications piece meal.

Hope it helps.

---

