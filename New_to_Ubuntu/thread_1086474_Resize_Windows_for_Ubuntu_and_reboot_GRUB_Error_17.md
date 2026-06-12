---
title: "Resize Windows for Ubuntu and reboot GRUB Error 17"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by flylehe on 2009-03-04
Hi,
I am reinstalling my Ubuntu on my laptop with Windows XP existing. 

First, with Partition Magic, I resized my Windows C (system) disk to free some space in order to add into new Ubuntu's root. To complete the partition, I have to reboot but at the very beginning of restart I got an error "GRUB Loading stage 1.5 GRUB loading, please wait... Error 17" and it became stuck there. 

I then have no idea how to fix it and I start reinstalling Ubuntun from cd. At the partiton part, the installation guide at first did not recognize the size changing of Windows C but later report the size is smaller that what it shows. It lets me either ignore or cancel. I cancelled and restart again without CD. Now same error of GRUB Error 17 happen again. 

Really appreciated if someone could help me out! Thanks in advance!

---

### Post by AXeS on 2009-03-04
neoob myself but i might be able to help get more info outa you.

ok so you just resized the windows (c:),
using partition magic,did you format it any type of filesystem? example ntfs fat32 or ext2 or 3? 

you say when you complete the partition... are you refering to Partition magic or Ubuntu's partition editor?

what i think might not be right, but i dont think grub was installed at the boot sequence or something. i had a similar problem,but i struggled a bit, i eventually settled to re-install ubuntu and it worked.
there is a way to re-install grub from the ubuntu's recovery console,its in one of the sticky threads in this forum.
if that dont work then you'd have to wait for a complete answer.

anyway hope that helps.

---

### Post by AXeS on 2009-03-04
found the grub section here :

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

check it out and post if you got any more problems.

---

### Post by flylehe on 2009-03-04
Thank you!

Before I was going to reinstall my Ubuntu, I went into Windows and shrinked the size of Windows C disk which is FAT32 by partition magic.

The partition requires restart into Windows again to complete. But the restart produces the GRUB Error 17 at the very beginning. It become stuck, and even the usual selection between Ubuntu and Windows XP does not appear. 

I started reinstall Ubuntu anyway, but the partition step at first showed that the size of Windows C was still the same as the orginal one before my using partion magic. So I guess my shrinking of Windows C might not finished yet. Then I assign partition for Ubuntu. It began to check the disk, applied my partition. Then it reported that the size of Windows C disk had changed, so I chose to quit the reinstallation when asked to ignore or quit.

Looks like the GRUB error is just linux-related instead of Windows-related. However why my Windows is not able to start either? Shall I continue to reinstall Ubuntu with ignoring the size change warning of Windows C disk? After finish, will my Windows be able to start?

---

### Post by AXeS on 2009-03-04
Should you re-install....


Right there, thats my Que to say I DONT KNOW and im not ashamed.

But ...wait come to think of it my system had the same problem. just that i had 3 partitions /windowsXP /Windows 7 (7000) build /Ubuntu intrepid ibex.

i cant remeber exactly now but try the windows install disk to go to recovery and fix. if not, you could try and get it to goto console to repiar yourself using "[COLOR="Red"]chdsk /f[/COLOR]" i think,but i didnt do that to fix it,i really cant remember. If all else Fails, i think you gota re-install both the OS/s.

Anyway ima try and remember and if i do, i'll leave it here. If not there should be an alternative way to remove the grub loader / overwrite grub with the boot.ini file or something.

---

### Post by jaminux on 2009-03-04
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

That is what grub error 17 means. 

What this probably means is is that grub is now looking for your partition in the blank space because you have resized and moved things.

Simply follow:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Using the live cd to re-install grub and the error should be fixed. No need for re-installation.

---

### Post by konqueror7 on 2009-03-04
encountered the same problem a couple of days ago, i used EASEUS Partition Manager, same result... the cause of it is that GRUB doesn't recognize the current filesystem... solution that were recommened were to detached the harddrive and reconnect it again (didn't do it because i have a laptop, and still in warranty;)), the other is to boot with your windows rescue disk, and use "fixmbr" command...what i did is just reinstall the whole thing, how bad could it be:D

---

