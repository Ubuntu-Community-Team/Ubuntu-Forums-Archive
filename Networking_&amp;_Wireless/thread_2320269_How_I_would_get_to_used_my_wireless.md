---
title: "How I would get to used my wireless"
date: 2016-04-12
forum: Networking &amp; Wireless
---

### Post by Jan_Hnninen on 2016-04-12
Hi,

I have problem within wireless adapter of my laptop. I have Acer Predator 17 (laptop) and on it have been installed Ubuntu 15.10 64 bit. My system find that device to some level, but networking part doesn't find any wireless. I have also tested external device via usb port, but I appears the same problem.  My laptop shout be wireless device ( product: QCA6174 802.11ac Wireless Network Adapter). I am not a beginner. I have tried find solved, but suit solved haven't been found still.

---

### Post by chili555 on 2016-04-12
>  I have tried find solved, but suit solved haven't been found still. >  QCA6174 802.11ac Wireless The driver for your device *ath10k_pci* is included by default in Ubuntu 15.10. The required firmware is not included. Please identify your device with the terminal command:```
lspci -nnk | grep 0280 -A2
```Find the pci.id; something like 168c:0041 but maybe not exactly that. Search for the pci.id and check any of the many threads that tell how to install the firmware.

You may get some clues from the message log:```
dmesg | grep ath
```Post back if you get stuck.

---

### Post by Jan_Hnninen on 2016-04-17
Hi,
 
 
 I found solved to my problem within url: [http://www.killernetworking.com/support/knowledge-base/17-linux/20-killer-wireless-ac-in-linux-ubuntu-debian](http://www.killernetworking.com/support/knowledge-base/17-linux/20-killer-wireless-ac-in-linux-ubuntu-debian). I downloaded four files and compiled needed backports.  

 
 
 
 
 The steps are similar to the following:

 
 
 
 
 
 
 **Killer 1525** specific firmware paragraph:
   
 Copy board.bin and firmware-5.bin_SW_RM.1.1.1-00157-QCARMSWPZ-1 to /lib/firmware/ath10k/QCA6174/hw2.1/  
 
 
 Remember replace irmware-5.bin_SW_RM.1.1.1-00157-QCARMSWPZ-1 to firmware-4.bin
 
 
 
 
 So on .........

 
 
 **Killer 15****3****5** specific firmware paragraph:
   
 Copy board.bin and firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1  to /lib/firmware/ath10k/QCA6174/hw3.0/  
 
 
 Remember replace  firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1 to firmware-4.bin
 
 
 
 
 
 
 and then backports compiling  
 
 
 
 
 Download latest version of that for example to [https://wireless.wiki.kernel.org/en/users/drivers/ath10k/backports](https://wireless.wiki.kernel.org/en/users/drivers/ath10k/backports)

 
 
 
 
 Sure, that you have extract directory of package is as your computer latest kernel. You can check that directory for example; ls /lib/modules.
 
 
 [FONT=Liberation Serif, serif][SIZE=3]make defconfig-ath10k[/SIZE][/FONT] 
 
 make
 
 
 sudo make Install
 
 
 
 
 Finally it should be installed  
 
 
 sudo rmmod ath10k_pci
 
 
 sudo modprobe -v ath10k_pci
 
 
 
 
 Now enjoy:)

---

