---
title: "Wireless Network on MSI ghost GS60 pro 4k"
date: 2015-10-30
forum: Networking &amp; Wireless
---

### Post by SouheilBs on 2015-10-30
network issue (fixed with the following)
========================================  =======

**Killer 1525** specific firmware:
Download:
[https://github.com/kvalo/ath10k-firm...w2.1/board.bin]("https://github.com/kvalo/ath10k-firmware/blob/master/ath10k/QCA6174/hw2.1/board.bin")
and put it in the /lib/firmware/ath10k/QCA6174/hw2.1/ folder 
Download:
[https://github.com/kvalo/ath10k-firm...firmware-5.bin]("https://github.com/kvalo/ath10k-firmware/blob/master/ath10k/QCA6174/hw2.1/firmware-5.bin") 

and put them in the /lib/firmware/ath10k/QCA6174/hw2.1/ folder

(create the folder if it doesn’t exist)
sudo mkdir /lib/firmware/ath10k/QCA6174/hw2.1/

 

**THEN**
cd hw2.1
sudo depmod -a
sudo update-initramfs -u 

modinfo ath10k_pci

sudo service network-manager stop
sudo modprobe -rfv ath10k_pci
sudo modprobe -v ath10k_pci
sudo service network-manager start
=======================================
Then I ve got the wireless network up

---

### Post by jeremy31 on 2015-10-30
It would help to reveal what kernel you are using ```
uname -a
``` and what device  the Killer 1525 actually is ```
lspci -nnk | grep -iA2 net
```
I do suspect it is the 003e device

---

