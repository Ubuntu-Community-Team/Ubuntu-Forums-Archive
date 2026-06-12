---
title: "ubuntu wifi works, xubuntu does not"
date: 2015-02-08
forum: Networking &amp; Wireless
---

### Post by rb76543 on 2015-02-08
my toshiba laptop satellite L15W-B1302 has a Realtek wireless RTL8723BE PCIe adapter.  when i installed ubuntu 14.04 it worked automatically.  but i prefer xfce, so in installed xubuntu 14.04 on another partition, but xubuntu did not install the driver. and since the laptop has no internet, i cannot download or install anything until the wifi works, unless a usb flash drive will work.  so, the question is: can i copy the ubuntu drivers from their partition to the xubuntu install? i can boot to either and mount the un-booted filesystem, so can i just copy some files? if so, where would i look?  thanks in advance for any advice.

---

### Post by kerry_s on 2015-02-08
/lib/firmware

in a default xubuntu install gksu is not installed, so use "sudo thunar /" in terminal.

---

### Post by rb76543 on 2015-02-08
thanks kerry_s. 

i copied the firmware and the module and rebooted. no change. modprobe says module not found, and insmod says invalid module format.

---

### Post by rb76543 on 2015-02-08
solution: go to the ubuntu install that works. apt-get remove unity. apt-get install xubuntu-desktop.  now i have xfce and wifi. excellent.

thanks again to kerry for the help.

---

