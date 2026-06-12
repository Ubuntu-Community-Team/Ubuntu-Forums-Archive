---
title: "Please direct me to some good guides to install Windows 7 on the same HD as Lucid."
date: 2010-11-12
forum: New to Ubuntu
---

### Post by mikodo on 2010-11-12
Hi everyone, 

I've looked but I haven't found any guides that can show me how to install Windows 7, 64 bit on the same HD as Lucid 32 bit. I just have the one drive. I just want to learn how to do it. I put the Windows 7 in a vm in VirtualBox, that works.

I don't know really anything about working with grub2 and MBR,s, so I would have to follow concise guides.

Below is a screenshot of my partitioned HD, all partitions after /dev/sda7 are empty and I can change the partitioning as is needed.

See the screenshot below.

Thank you.

---

### Post by bioterror on 2010-11-12
Here you go:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

I'm going to take part in your partition problem, but I can't undertand why so many partitions.

---

### Post by mikodo on 2010-11-12
> **bioterror said:**
> Here you go:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I'm going to take part in your partition problem, but I can't undertand why so many partitions.

Thanks for the link. I'll give a good read.

I am not going to do any partitioning tonight, as it is after midnite here. Thanks for the offer to take part in my partitioning. The offer was a generous one and appreciated by me.

I was going to install a bunch of linux vm's in the multiple logical partitions, but changed my mind.

Thanks.

Mike

---

### Post by XubuRoxMySox on 2010-11-12
[COLOR="Red"]**Extreme caution!**[/COLOR] 

In a computer with Windows installed it is pretty easy to install Linux alongside it. In a 'puter with Linux installed, adding Windows is problematic for alot of folks (especially newbies). The Windows bootloader won't recognize Linux, but most Linux bootloaders recognize other OSes.

If you have lots of time and good backups of everything, it might be worth your while to install Windows first, and then your Linux distro(s) on their own partitions. This allows the bootloader to "see" both operating systems and offer a choice at boot-up.

-Robin

---

### Post by mikodo on 2010-11-12
> **dixiedancer said:**
> [COLOR=Red]**Extreme caution!**[/COLOR] 

In a computer with Windows installed it is pretty easy to install Linux alongside it. In a 'puter with Linux installed, adding Windows is problematic for alot of folks (especially newbies). The Windows bootloader won't recognize Linux, but most Linux bootloaders recognize other OSes.

If you have lots of time and good backups of everything, it might be worth your while to install Windows first, and then your Linux distro(s) on their own partitions. This allows the bootloader to "see" both operating systems and offer a choice at boot-up.

-Robin
Thanks for the response/warining dixiedancer. I was beginning to think what you wrote might be the wiser way also. I find lots of guides showing how to easily dual boot with Windows first; but not too much showing how to do it with Linux/Ubuntu first, and what is available is not too well described.

So I went to bed last nite to sleep on it, and have now found your warning and suggestion, giving credence to reinstalling with Windows first. Seems a sign post. I am sure given my newbie track record of screwing things up and having to reinstall, that that is more than likely, exactly what would happen. Not always would someone as knowledgeable and generous have the time to help with my mistakes, or give direction when I needed,  as offered by **bioterror**  earlier (last nite).

I use Deja-Dup for backup of my /home partition and when I recently tested it on a new install of Maverick, it brought my data from my external drive backup perfectly. "PLUG". Since then I have gone back to using Lucid, as it works so well for my needs.

So, blah, blah; your point is well taken and I think I'll dual boot with Windows first.

Thank you all,  

Mike

---

### Post by Grez on 2010-11-12
> **mikodo said:**
> Thanks for the response/warining dixiedancer. I was beginning to think what you wrote might be the wiser way also. I find lots of guides showing how to easily dual boot with Windows first; but not too much showing how to do it with Linux/Ubuntu first, and what is available is not too well described.

So I went to bed last nite to sleep on it, and have now found your warning and suggestion, giving credence to reinstalling with Windows first. Seems a sign post. I am sure given my newbie track record of screwing things up and having to reinstall, that that is more than likely, exactly what would happen. Not always would someone as knowledgeable and generous have the time to help with my mistakes, or give direction when I needed,  as offered by **bioterror**  earlier (last nite).

I use Deja-Dup for backup of my /home partition and when I recently tested it on a new install of Maverick, it brought my data from my external drive backup perfectly. "PLUG". Since then I have gone back to using Lucid, as it works so well for my needs.

So, blah, blah; your point is well taken and I think I'll dual boot with Windows first.

Thank you all,  

Mike

You could always install Windows in a Virtual Machine that runs under Linux, instead of dual booting. I do that with XP running inside "VirtualBox" and it goes really well. It also means that you can have Windows and Linux up and running on the same machine. I had the prerelease version of Windows 7 running in this way as well, but wasn't impressed enough to take it any further.

Just a thought!

---

### Post by mikodo on 2010-11-12
Thanks Grez. 

I have put the Windows 7 64 bit OS in a VBox vm and it works for my box. I am thinking of natively booting Windows and other Linux distros, just for the experience, and fun of it.

Mike

---

### Post by mikodo on 2010-11-12
@ **bioterror;**

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

By the way, that was exactly what I needed to learn about bootloaders and working with them. A right on direction by you. A huge resource.

Thanks again!

Mike

---

### Post by oldfred on 2010-11-12
windows does not have to be first but just about has to be installed to a primary partition - sda1 thru sda4.

Older but discusses the issues, reinstall grub2, not other alternatives:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
chroot version:
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)
chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by mikodo on 2010-11-13
Thanks oldfred,

Again, you came in weighing in spades.

LOL! I think that is how the saying goes. My g'ma used that saying a lot.

Mike

---

