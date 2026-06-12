---
title: "Boot loader install failed"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by Andrey0614 on 2011-03-24
i know there is already a thread with the same problem, but still does not work. trying to install ubuntu 10.10 and having "boot loader install failed" message. cant choose any options. keep pressing them, but no response.
 
using internal hhd, installing of cd, have internet connection

---

### Post by oldfred on 2011-03-24
A few BIOS have the capability of locking the MBR from writing bitlocker, corelocker etc. Have you checked BIOS? Was drive ever part of RAID set?

Post this:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by jtarin on 2011-03-24
Is this an initial installation? Did the operating system install and you only have problems with Grub being installed? Is there another operating system on the drive (dual-boot)?

---

### Post by Andrey0614 on 2011-03-24
sorry, was running errands. guys take it easy on me and use crayon version of tech talk. i had ubuntu on it before and it had some issues so i decided to reload it and start from begining. followed all the right steps from previous posts and when i get to that step i get error message. can you provide detailed step by step instructions.

---

### Post by Andrey0614 on 2011-03-24
so, here is where i have problems:
running "grub-install/dev/mmcblk0" step message poped up saying
"unable to instal GRUB in /dev/mmcblk0"
 
"executing 'grub-install/dev/mmcblk0' failed
"thisis fatal error"
"ok"
 
when i click "ok" another window pops up
 
"bootloader install failed"
options are
 
'choose different device"
""/dev/sda""
""/dev/sda1""
 
"continue without a bootloader"
 
"cancel the instalation"

---

### Post by oldfred on 2011-03-25
/dev/mmcblk0 is not a standard device. Are you running RAID or LVM? 

Standard devices are sda, sdb etc. And BIOS normally boot from the MBR of the primary master drive, but RAID & Logical Volumes start to change some things.

Post boot script so we can see details.

---

### Post by jtarin on 2011-03-25
/dev/mmc.....MultiMediaCard.

---

### Post by ,.. on 2011-09-17
> **Andrey0614 said:**
> so, here is where i have problems:
running "grub-install/dev/mmcblk0" step message poped up saying
"unable to instal GRUB in /dev/mmcblk0"
 
"executing 'grub-install/dev/mmcblk0' failed
"thisis fatal error"
"ok"
 
when i click "ok" another window pops up
 
"bootloader install failed"
options are
 
'choose different device"
""/dev/sda""
""/dev/sda1""
 
"continue without a bootloader"
 
"cancel the instalation"

I had the same problem and here's what I did to fix it (although at this  point my solution is probably just for the benefit of anyone who finds this thread through googling the error like me):

1. I had an SD card plugged in which I unplugged. I kind of doubt this is what fixed it, but just to be superstitious I recommend removing any SD cards that you aren't using to install off of.
2. I think this is what really did it, in my bios there was some memory protection thing enabled with I disabled. I'm using a Lenovo E520 so anyone with the same should probably watch out for that. Also anyone with this laptop might have some wifi problems for which a solution can be found here:
[http://ubuntuforums.org/showthread.php?t=1760181](http://ubuntuforums.org/showthread.php?t=1760181)
3. And finally for some guidance on how to overwrite the bad install I found this link sort of helpful:
[http://sites.google.com/site/easylinuxtipsproject/reinstallation](http://sites.google.com/site/easylinuxtipsproject/reinstallation)
Best of luck,
~,..

---

### Post by P05TMAN on 2011-09-17
> **Andrey0614 said:**
> so, here is where i have problems:
running "grub-install/dev/mmcblk0" step message poped up saying
"unable to instal GRUB in /dev/mmcblk0"
 
"executing 'grub-install/dev/mmcblk0' failed
"thisis fatal error"
"ok"
 
when i click "ok" another window pops up
 
"bootloader install failed"
options are
 
'choose different device"
""/dev/sda""
""/dev/sda1""
 
"continue without a bootloader"
 
"cancel the instalation"

I had a very similar error when I installed 10.10. This link & its instructions worked for me! 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

