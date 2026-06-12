---
title: "Activate Wireless drivers in think-pad e440"
date: 2014-06-22
forum: Networking &amp; Wireless
---

### Post by dilantha on 2014-06-22
Hi All,

I have recently bought a think-pad e440 and installed ubuntu 12.04 in it. Everything is working fine expect the wireless drivers. I saw this question has been asked in many places but none of the provided solutions worked for me. Here are some of the commands that i have tried with the outputs.

dmesg | grep iwl [B]did not display anything
[/B]
rfkill list all

```
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

lspci

```
00:00.0 Host bridge: Intel Corporation Haswell DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Haswell Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Haswell HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation Lynx Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Lynx Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point PCI Express Root Port 1 (rev d4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point PCI Express Root Port 3 (rev d4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point PCI Express Root Port 4 (rev d4)
00:1c.4 PCI bridge: Intel Corporation Lynx Point PCI Express Root Port 5 (rev d4)
00:1d.0 USB controller: Intel Corporation Lynx Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point 6-Port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point SMBus Controller (rev 04)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5227 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 10)
04:00.0 Network controller: Intel Corporation Device 08b2 (rev 73)
```


Anyhelp on this is really appriciated as im a beginner in ubuntu. Thanks in advance.

---

### Post by chili555 on 2014-06-22
I suspect your rather new wireless device isn't covered by the 2+ year old driver in Ubuntu 12.04. Would you consider installing 14.04 LTS or would you like to compile a driver from scratch? 

Please help us by posting:```
lspci -nn | grep 0280
```Thanks.

---

### Post by dilantha on 2014-06-22
Hi chili555,

Thanks a lot for your quick reply. It would be great if you can help me to compile the driver from the scratch. below is the output for[B] lspci -nn | grep 0280
[/B]
```
04:00.0 Network controller [0280]: Intel Corporation Device [8086:08b2] (rev 73)
```

---

### Post by chili555 on 2014-06-22
Here ya go! [http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63/](http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63/)

You will also need the compiling prerequisites before you start:```
sudo apt-get install build-essential linux-headers-generic
```Post back if you get stuck.

---

### Post by dilantha on 2014-06-22
chili555 you ROCK..!!! :guitar:it worked. Thanks a million

---

### Post by chili555 on 2014-06-22
Awesome! Glad it's working. Please take note of my comments on the page I linked:> Thanks, that helped! Does this mean though that now I can't update the kernel packages via system update? –  Dmitry Pashkevich Oct 15 '13 at 14:06
  	  	
@DmitryPashkevich- Yes, you can, but **you will have to repeat the compile process above**. The firmware part need not be repeated. –  chili555 Oct 15 '13 at 14:25   
  	
 		
yeah that's what I actually meant :) thanks. I can update the kernel but I would have to reinstall the backport again –  Dmitry Pashkevich Oct 15 '13 at 15:14Please retain the files and these instructions for that time.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

