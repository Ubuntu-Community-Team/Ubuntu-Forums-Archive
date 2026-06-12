---
title: "dual boot"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by itsferny on 2011-08-23
i installed ubuntu 11.04 and now want to install windows 7 but i am not sure how to partition my hard drive
do i do it in ubuntu or do i do it while i am installing win 7?
thanks in advance

p.s. what if i did not leave partition space?
how would i know for sure?

---

### Post by dave01945 on 2011-08-23
if you have left unpartitioned space on the hard disk you can let windows do it if not you will need to do it using ubuntu but you will have to do it from a live cd because it will be the active partition you want to change

also if your installing windows after ubuntu you will need to read this because windows won't let you access ubuntu after installing

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

it's always easy to install windows first if you have to have both

---

### Post by Megaptera on 2011-08-23
Although different versions of Ubuntu & Windows, you may find this guide with screenshots useful too: [http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by seawolf167 on 2011-08-23
Basically, you'll need to resize your current partition(s) to allow enough room for the Windows installation. This can be done with GParted through a LiveCD (since the partitions need to be unmounted to resize).

Then you'll install Windows to your [now] unallocated space on the hard drive.

Windows will install its MBR to the hard drive, so you'll then need to reinstall GRUB2 after the installation is complete. Take a look [URL="https://help.ubuntu.com/community/Grub2/#Reinstalling%20GRUB2"]at this how-to link
[/URL]

---

### Post by BHEJU on 2011-08-23
If you have already installed Ubuntu... then you might want to install win-7 in virtual env using Virtualbox or vmware... etc...

Otherwise you will have to resize partitions and mess around with MBR. Which is not that complex but if you are new to this.. I suggest you avoid the risk (unless you really want to get into the nuts and bolts)

I have been running win in virtual env for more than a year. no issues. as I rarely use win.

Cheers,

---

### Post by SikDuk on 2011-08-23
In my 5 years of using Ubuntu I found that you have to first install Windows  ,then install Ubuntu because Ubuntu's installer will instal right over the top of Windows due to the installer creating a new MBR..Just my experience..But Installing Win7 in a Virtal machine would be a good idea  if you have the disk space for it inside the Ubuntu install..Have a great day...

---

