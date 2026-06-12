---
title: "&quot;No Wi-Fi Adapter Found&quot; on ASUS X409FA-EK034T"
date: 2019-11-05
forum: Networking &amp; Wireless
---

### Post by KNAKjao0 on 2019-11-05
I am new to Ubuntu. I am running Ubuntu 18.04.3 from a live USB on my laptop (ASUS X409FA-EK034T). I wish to connect to the internet wirelessly. When I go to Settings > Wi-Fi I see the message


[INDENT]No Wi-Fi Adapter Found
Make sure you have a Wi-Fi adapter plugged in and turned on[/INDENT]

How can I connect to the internet by Wi-Fi?

---

### Post by mörgæs on 2019-11-06
Hi, welcome to the fora.
New hardware runs best with new software. Do you see any difference in a live boot of 19.10?

---

### Post by KNAKjao0 on 2019-11-06
> **mörgæs said:**
> Hi, welcome to the fora.
New hardware runs best with new software. Do you see any difference in a live boot of 19.10?

 I have tried a live boot of 19.10. There is no difference.

---

### Post by slickymaster on 2019-11-06
Thread moved to **Networking & Wireless** for a better fit

---

### Post by kurt18947 on 2019-11-06
> **ethylene-glycol said:**
> I am new to Ubuntu. I am running Ubuntu 18.04.3 from a live USB on my laptop (ASUS X409FA-EK034T). I wish to connect to the internet wirelessly. When I go to Settings > Wi-Fi I see the message
[INDENT]No Wi-Fi Adapter Found
Make sure you have a Wi-Fi adapter plugged in and turned on[/INDENT]

How can I connect to the internet by Wi-Fi?

This is an internal adapter? If so could you show the results of this terminal command?

```
lspci
```

You should see similar to this. This device is wired ethernet. You wireless device may be labeled network controller or similar.

```
15:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset USB 3.1 xHCI Controller (rev 02)
15:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset SATA Controller (rev 02)
15:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b2 (rev 02)
1d:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
1d:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
1d:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
**1f:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)**
22:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos XTX [Radeon HD 8490 / R5 235X OEM]
22:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6450 / 7450/8450/8490 OEM / R5 230/235/235X OEM]
2e:00.0 Non-Volatile memory controller: Silicon Motion, Inc. Device 2262 (rev 03)
38:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] (rev c8)
38:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 15de
38:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 15df

```

---

### Post by KNAKjao0 on 2019-11-06
> **kurt18947 said:**
> This is an internal adapter? If so could you show the results of this terminal command?

```
lspci
```

You should see similar to this. This device is wired ethernet. You wireless device may be labeled network controller or similar.

```
15:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset USB 3.1 xHCI Controller (rev 02)
15:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset SATA Controller (rev 02)
15:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b2 (rev 02)
1d:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
1d:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
1d:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
**1f:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)**
22:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos XTX [Radeon HD 8490 / R5 235X OEM]
22:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6450 / 7450/8450/8490 OEM / R5 230/235/235X OEM]
2e:00.0 Non-Volatile memory controller: Silicon Motion, Inc. Device 2262 (rev 03)
38:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] (rev c8)
38:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 15de
38:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 15df

```

INPUT:

```
lspci
```

OUTPUT:

```
00:00.0 Host bridge: Intel Corporation Device 3e34 (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (Whiskey Lake)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 0b)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Cannon Point-LP Thermal Controller (rev 30)
00:14.0 USB controller: Intel Corporation Cannon Point-LP USB 3.1 xHCI Controller (rev 30)
00:14.2 RAM memory: Intel Corporation Cannon Point-LP Shared SRAM (rev 30)
00:15.0 Serial bus controller [0c80]: Intel Corporation Cannon Point-LP Serial IO I2C Controller #0 (rev 30)
00:15.1 Serial bus controller [0c80]: Intel Corporation Cannon Point-LP Serial IO I2C Controller #1 (rev 30)
00:16.0 Communication controller: Intel Corporation Cannon Point-LP MEI Controller #1 (rev 30)
00:17.0 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 30)
00:19.0 Serial bus controller [0c80]: Intel Corporation Device 9dc5 (rev 30)
00:1d.0 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #9 (rev f0)
00:1d.1 PCI bridge: Intel Corporation Device 9db1 (rev f0)
00:1e.0 Communication controller: Intel Corporation Device 9da8 (rev 30)
00:1e.2 Serial bus controller [0c80]: Intel Corporation Device 9daa (rev 30)
00:1f.0 ISA bridge: Intel Corporation Cannon Point-LP LPC Controller (rev 30)
00:1f.3 Audio device: Intel Corporation Cannon Point-LP High Definition Audio Controller (rev 30)
00:1f.4 SMBus: Intel Corporation Cannon Point-LP SMBus Controller (rev 30)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Point-LP SPI Controller (rev 30)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter

```

---

### Post by chili555 on 2019-11-06
> Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network AdapterPlease check here: [https://askubuntu.com/questions/1162223/lenovo-18-04-no-wi-fi-adapter-found/1162258#1162258](https://askubuntu.com/questions/1162223/lenovo-18-04-no-wi-fi-adapter-found/1162258#1162258)

---

### Post by KNAKjao0 on 2019-11-06
> **chili555 said:**
> Please check here: [https://askubuntu.com/questions/1162223/lenovo-18-04-no-wi-fi-adapter-found/1162258#1162258](https://askubuntu.com/questions/1162223/lenovo-18-04-no-wi-fi-adapter-found/1162258#1162258)

This has solved the problem. Thank you very much.

---

### Post by KNAKjao0 on 2019-11-06
> **chili555 said:**
> Please check here: [https://askubuntu.com/questions/1162223/lenovo-18-04-no-wi-fi-adapter-found/1162258#1162258](https://askubuntu.com/questions/1162223/lenovo-18-04-no-wi-fi-adapter-found/1162258#1162258)

I have one more question: what directory should I be in when I run these commands? git clone will create a sub-directory rtl8821ce in that directory and I would like rtl8821ce to be in the most sensible place.

---

### Post by chili555 on 2019-11-06
I doubt that it matters. Your /home/username directory is just fine. To be certain that you are in that directory before you start, simply do:```
cd
```I have git cloned to my desktop, home and also, when I am answering forum questions here and elsewhere, to a directory I created; namely, /home/chili/Desktop/Forum. It can be abbreviated as ~/Desktop/Forum.

The dkms install process automagically takes care of placing needed files in /usr/src and /var/lib as needed. The starting place; /home or Desktop or Downloads, etc., doesn't change it.

---

### Post by KNAKjao0 on 2019-11-06
> **chili555 said:**
> I doubt that it matters. Your /home/username directory is just fine. To be certain that you are in that directory before you start, simply do:```
cd
```I have git cloned to my desktop, home and also, when I am answering forum questions here and elsewhere, to a directory I created; namely, /home/chili/Desktop/Forum. It can be abbreviated as ~/Desktop/Forum.

The dkms install process automagically takes care of placing needed files in /usr/src and /var/lib as needed. The starting place; /home or Desktop or Downloads, etc., doesn't change it.

Can the folder rtl8821ce be deleted afterwards?

---

### Post by chili555 on 2019-11-06
> Can the folder rtl8821ce be deleted afterwards?Are you my ex-wife? Is that you, Sharon? You want to throw away my clothes??

Seriously, you can delete it if you are quite confident that *nothing *will go wrong and that you will *never *need to repeat the process. I am not that confident. It takes up relatively little space. I'd keep it.

---

### Post by KNAKjao0 on 2019-11-07
> **chili555 said:**
> Are you my ex-wife? Is that you, Sharon? You want to throw away my clothes??

Seriously, you can delete it if you are quite confident that *nothing *will go wrong and that you will *never *need to repeat the process. I am not that confident. It takes up relatively little space. I'd keep it.

OK, thank you for your help.

---

