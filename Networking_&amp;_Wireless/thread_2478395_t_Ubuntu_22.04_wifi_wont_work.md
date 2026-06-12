---
title: "t Ubuntu 22.04 wifi wont work"
date: 2022-08-25
forum: Networking &amp; Wireless
---

### Post by devdlp on 2022-08-25
so just installed ubuntu 22.04 and ran into my wifi not working properly ive tried mainline app to change the kernal
to 5.13, then changed it to 4.20, back up to 5.11 none of this is working. i just need yto know how to get my onbroad wifi to work because me 
making this post right now im using a adapter and i rather not do that. this is output of lspci....
"chewy@chewy-HP-Laptop-15-bs1xx:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Device 5906 (rev 07)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 08)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point LPC Controller/eSPI Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
02:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 20)"

---

### Post by chili555 on 2022-08-26
> Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network AdapterThe usual driver for this is ath10k_pci which appears in later kernel vesions only. 4.anything will probably not work.

Let's load the driver and see if there are any interesting clues in the logs.

```
sudo modprobe ath10k_pci
sudo dmesg | grep ath
```Post the results and we'll proceed.

---

### Post by mikestein on 2022-08-27
This is the second time in a few weeks that an update to 22.04 has "broken" my wi-fi. In both cases I could connect to my iphone and use my 4G signal but I couldn't connect to my router without an ethernet cable which is a real nuisance as the router is nowhere near my laptop. This was fixed and then broken again yesterday but now it's fixed again. Come on, stop breaking things!!

---

### Post by devdlp on 2022-09-03
i fixed it by reinstalling and having it connected to the ethernet
and Ubuntu updated the drivers it self,
so now my wifi is fine. Thanks

---

