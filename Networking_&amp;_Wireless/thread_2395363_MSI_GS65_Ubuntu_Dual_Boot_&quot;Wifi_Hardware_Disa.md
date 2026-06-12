---
title: "MSI GS65 Ubuntu Dual Boot &quot;Wifi Hardware Disabled&quot; After Suspend"
date: 2018-06-30
forum: Networking &amp; Wireless
---

### Post by ericlee123 on 2018-06-30
I currently have Ubuntu 18.04 installed alongside Windows 10 on an MSI GS65. In Ubuntu, whenever I would wake the laptop from sleep, my networking settings would indicate that the wifi hardware is disabled. As another note, it seems like there is also no bluetooth device detected. I have to reboot into Ubuntu to get things working again. I have tried running "sudo service network-manager restart", "sudo rfkill unblock all", and also tried tweaking power management settings in Windows, but nothing has worked. Does anyone have any suggestions as to what to do? For reference, I have the Intel 9560 wireless adapter. I have also tried upgrading my kernel to Linux 4.17.3.

---

### Post by oldfred on 2018-06-30
While not your model, issues often common by brand. More differences if Intel or AMD versions.

       MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)

---

### Post by matt-r2 on 2018-09-18
I had a similar problem with my dell xps 13, it always did this. I had to buy another wifi chip intel 8265 and install it. Very happy it fixed the issue. Another thing, I had similar blue tooth problems before I did this. I then installed blueman and updated to kernel 4.15.

this fixed those issues.

---

