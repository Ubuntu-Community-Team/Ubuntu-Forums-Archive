---
title: "Problems dual booting ubuntu/Win7"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by Dinglehoofis on 2010-04-14
Alright so recently I decided I wanted to start using Ubuntu.  I have Windows 7 Ultimate x64 installed on my computer as my main OS.  I made a 40 GB partition in the Windows disk manager to install linux on.  After installing Ubuntu with the live CD my computer would just boot straight into Windows without even asking me which OS I wanted to use.  After some looking around on google I downloaded EasyBCD to add another entry to the windows bootloader hoping it would allow me to dual boot.  Now when I select Ubuntu as the OS I want to boot, I get this error:

File: \NST\nst_grub.mbr

Status: 0xc000000f

Info: The selected entry could not be loaded because the application is missing or corrupt.

I'm VERY new to linux and the software side of things isn't exactly my strong point.  This is what EasyBCD shows for my bootloader entries:

Entry #1

Name:  Windows 7
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

Entry #2

Name:  Ubuntu
BCD ID:  {8f59edf7-8bd0-11de-b587-ea7b5b5193be}
Drive: \Device\HarddiskVolume1
Bootloader Path:  \NST\nst_grub.mbr

Can anyone help?

---

### Post by Jon Monreal on 2010-04-14
Can you boot Windows, go to (under Computer) C:\NST\ and verify that the file nst_grub.mbr is there?

Thanks.

---

### Post by Dinglehoofis on 2010-04-14
> **Jon Monreal said:**
> Can you boot Windows, go to (under Computer) C:\NST\ and verify that the file nst_grub.mbr is there?

Thanks.

There's no folder called NST under C:\

---

### Post by juanoleso on 2010-04-14
Are you sure that you installed to the new partition?  Did it finish successfully?  If so then Ubuntu uses a different type of bootloader, GRUB, and so messing with easyBCD will not help you.  When you reboot your computer, look for a line that says something to the effect "press ESC to something something Grub Menu".  Press ESC at that point and select Ubuntu.

If you installed Ubuntu using WUBI, which would have been like installing a program in windows, thats when easyBCD might help you.

---

### Post by cK` on 2010-04-14
It would be easier to back up your important files and do a fresh install of each. Install windows on half the drive and leave the other half for ubuntu!

I recently tried to install ubuntu with windows taking up the whole drive. I could not get my drive to shrink or ubuntu to install.

So i just did a fresh install and both work great.

---

### Post by wilee-nilee on 2010-04-14
It sounds like you want a true dual boot, separate operating systems on separate partitions. If this is the case you need to have a open unallocated space for Ubuntu to install into it will build the partition for you. Although if you want a custom partition setup you can build it from gparted on the live CD. I would wait for custom partitioning though until you can maybe experiment with it.

You will install Ubuntu with the Live CD this way and grub will be the bootloader, which is pretty reliable and easily manipulated if you get the correct help, at least easily examined along with all your partitions for errors.

---

### Post by Jon Monreal on 2010-04-14
While a fresh install can be a good idea, I don't think it's ideal in this situation.

I missed that Windows 7 was installed before Ubuntu. If you install Ubuntu second, GRUB should overwrite the Windows bootloader as [juanoleso]("http://ubuntuforums.org/member.php?u=561613") stated above. Reinstalling Ubuntu alone is probably the best option - should you need more space later, you can shrink the Windows 7 partition from within Windows and grow the Ubuntu partition.

---

### Post by ed-koala on 2010-04-14
Just so you know, installing 9.10 after Windows will result, TEMPORARILY, in you ONLY being able to boot into Ubuntu due to Grub2 overwriting the Windows MBR and Grub2 not "seeing" Windows 7. (At least, it happened to me!)

It is easily fixed however by editing /etc/default/grub as shown in this thread...

[http://ubuntuforums.org/showthread.php?t=1453700]("http://ubuntuforums.org/showthread.php?t=1453700")

Good luck!

---

### Post by cuberts on 2010-04-14
> **Dinglehoofis said:**
> Alright so recently I decided I wanted to start using Ubuntu.  I have Windows 7 Ultimate x64 installed on my computer as my main OS.  I made a 40 GB partition in the Windows disk manager to install linux on.  After installing Ubuntu with the live CD my computer would just boot straight into Windows without even asking me which OS I wanted to use.  After some looking around on google I downloaded EasyBCD to add another entry to the windows bootloader hoping it would allow me to dual boot.  Now when I select Ubuntu as the OS I want to boot, I get this error:

File: \NST\nst_grub.mbr

Status: 0xc000000f

Info: The selected entry could not be loaded because the application is missing or corrupt.

I'm VERY new to linux and the software side of things isn't exactly my strong point.  This is what EasyBCD shows for my bootloader entries:

Entry #1

Name:  Windows 7
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

Entry #2

Name:  Ubuntu
BCD ID:  {8f59edf7-8bd0-11de-b587-ea7b5b5193be}
Drive: \Device\HarddiskVolume1
Bootloader Path:  \NST\nst_grub.mbr

Can anyone help?I think that u are having problems with with you r harddrive. If what you did is not working, then I think that You should try running Ubuntu inside of Windows, by just installing the live CD inside. it will come up with a file called WUBI, then you should be able to run it from that. Then remember to install that file as well.

---

### Post by Dinglehoofis on 2010-04-14
The install completed successfully and it's definitely on the 40GB partition I created.  I also didn't realize that there was an x64 version of Ubuntu until just now also.

I'm currently downloading that one and am going to do the entire process over again.  I'm actually a computer technician, but like I said, the software side of things (well, not for an unfamiliar OS anyway) aren't my strong point... I'm more of a hardware guy.  There's a tech that I work with who is a total linux junkie and said he'd help me resolve my issue if I can't get it resolved.  I'm taking this as a learning experience anyway lol.

I didn't mention that I've actually got 4x 250GB drives in RAID 0, does this make a difference? I don't think it would, and I noticed that ubuntu supports RAID so it shouldn't an issue...

---

### Post by ed-koala on 2010-04-15
Oh, it may certainly make a huge difference if it's fake raid!

I had to use the alternate install CD, with the nodmraid option and saying no to active raid devices to get a working 9.10 Ubuntu install.

Ubuntu "saw" my 2 500gb drives as a 1tb drive, but no matter how I tried Ubuntu wouldn't boot doing normal installs to my combined drives.

---

### Post by Dinglehoofis on 2010-04-15
> **ed-koala said:**
> Oh, it may certainly make a huge difference if it's fake raid!

I had to use the alternate install CD, with the nodmraid option and saying no to active raid devices to get a working 9.10 Ubuntu install.

Ubuntu "saw" my 2 500gb drives as a 1tb drive, but no matter how I tried Ubuntu wouldn't boot doing normal installs to my combined drives.

I didn't know there was a real and a fake RAID lol.  I just used the RAID configuration thing in my BIOS to setup the array.  Ubuntu definitely saw my drives as a RAID 0 array during the install, but because this is a partition on an array that would make sense.

---

