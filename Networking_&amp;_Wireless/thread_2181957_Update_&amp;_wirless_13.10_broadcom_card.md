---
title: "Update &amp; wirless 13.10 broadcom card"
date: 2013-10-19
forum: Networking &amp; Wireless
---

### Post by andresmagos on 2013-10-19
i will tell you my story so you can understand, i have been waiting for the release of 13.10 for a couple of weeks & the day of the release i make the update, i was hoping that it solves the problem of the green dashborad that i have ( the transparency have green and black blocks in it)  and since i havent found a distribution in wich i have wirless enabled i decided live with the problem, ubuntu 13.04 is the only that after fresh install have my wirless up and running so the green dashboard was a minor issue. so after the update my computer crashed, i reboot and i get a black screen that says something is wrong i have to reboot ( excuseme i dont remember exactly the text) so it does that every time... i was like well ok lets download it and do a fresh install, i did that i log in and yey! the green dashboard was gone, but my wirless too, i was like ok lets enable the additiona drivers & reboot, but nothing changed i try to open network settings but it crashes every time so i try to get another distro, like always i never get the wirless to work, my question is if i have to stay with 13.04 from wich after all the pain i have reinstall and im writing from it wille it install the updates ^^ and  live with the green dashboard forever? my computer is a Campcom 6715b
like you will guess it have a broadcom card, mores specific its a "10:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)" (lspci comand)

my computer have a lots of problems with linux and sometimes i just wish i can download a distro & run it without having that much pain involved, thanks & well i hope we can solve something and it works for someone else (:

---

### Post by Hadaka on 2013-10-19
Hi, this should be fun !
from a wired conection connected to the internet
please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
does the wireless work?

---

