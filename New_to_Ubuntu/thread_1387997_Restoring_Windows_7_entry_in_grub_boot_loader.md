---
title: "Restoring Windows 7 entry in grub boot loader?"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by justinstrack on 2010-01-22
Okay I installed some updates for Ubuntu Ultimate 2.5. After I was finish I decided to reboot & boot into Windows 7 but I can't it gives me this error: 

***"Error: Invalid Signation, Press any key to continue."***

When I press "e" on the Windows 7 line on the grub menu list. it shows:

***"chainloader +1"***

*_What can I do so that I can boot into windows again with the grub menu?_*

---

### Post by justinstrack on 2010-01-22
Found my answer: [http://ubuntuforums.org/showthread.php?t=1264151&page=3](http://ubuntuforums.org/showthread.php?t=1264151&page=3)

1.sudo apt-get install os-prober
2. sudo os-prober, 
3.sudo mv /boot/grub/device.map /boot/grub/device.map.bak
4.sudo update-grub (came back clean)
5.reboot (all is well)

---

