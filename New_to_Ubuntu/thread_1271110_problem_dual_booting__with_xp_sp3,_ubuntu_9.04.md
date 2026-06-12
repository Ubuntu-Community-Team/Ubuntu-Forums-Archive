---
title: "problem dual booting  with xp sp3, ubuntu 9.04"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by x7n on 2009-09-20
Hi i am new here!
i have two sata hard drives Maxtor 500Gb and Western Digital 640Gb i install windows xp in WD Hdd, and then install Ubuntu 9.04 in Maxtor Hdd.
My problem is when i start my pc windows xp loads. there is no boot option.
and when i unplug windows xp hdd. and start my pc ubuntu dual boot screen displays. and in boot list, last item is windows xp but at that time i unplug that windows xp Hdd.
please help me
[COLOR=DarkRed]**i want to run both disks.**[/COLOR]
**how i disable windows xp booting?**
i try it, i create backup of boot.ini, ntldr and NTDETECT.COM and then delete from c:\ drive but no luck. after booting it says ntldr is missing press ctrl+Alt+delete.

**is there any way to add ubuntu in boot.ini?** Or **Disable windows xp Booting?**
(because i want to run windows xp from ubuntu dual boot menu.)

thanks

---

### Post by Shazaam on 2009-09-20
Reconnect all drives first.
Do you know how to enter your pc's bios setup screen? If you do, find the boot sequence section and change which hard drive boots first. Make the drive with Ubuntu the first one in the order.
Some pc bios keys (press them when you turn on your pc)...
Delete
F2
F12

---

### Post by DarinB on 2009-09-20
using the bios is a good way but i recommend putting ubuntu on half the xp drive. and making the 2nd drive your /home folder. having ubuntu added on the xp drive you will need to defragment the drive. by having a seperate /home you will never lose that data on upgrades of either os. there are tons of tutorials on how to do it and 9.04 makes it really easy to have the /home folder on the second drive.

---

### Post by x7n on 2009-09-20
thank you soo much!!! :)
problem solved.
thanks.

---

### Post by x7n on 2009-09-20
@[DarinB]("http://ubuntuforums.org/member.php?u=330217")
i will try it. 
is there any tutorial?
thanks

---

### Post by Darkwing-Duck on 2009-09-22
Another thing you might want to try is the dual booting from GRUB. Here is a tutorial for setting up grub the way you want it to work.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

Hope this helps you out.

---

