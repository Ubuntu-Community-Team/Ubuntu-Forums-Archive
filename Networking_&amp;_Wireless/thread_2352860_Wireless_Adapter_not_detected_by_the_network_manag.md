---
title: "Wireless Adapter not detected by the network manager"
date: 2017-02-16
forum: Networking &amp; Wireless
---

### Post by ashokcool on 2017-02-16
Hello all,

I am using a NVIDIA Tegra TK1(with ubuntu os) with an Intel Dual Band Wireless AC 7260. The problem i am currently facing is the Intel wireless is showing while using lspci command. But its not getting listed in the nmcli dev and also the network manager only shows wired ethernet and no wireless connection is shown. I have installed linux firmware and all nessesary drivers needed for the intel wireless to work. but still i cannot make the ubuntu network manager realise the presence of a wireless present in the board. Kindly help me understand the problem and what will be the possible step to proceed further.

Regards
Ashok

---

### Post by chili555 on 2017-02-16
Please start here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by ashokcool on 2017-02-16
thank you for your reply. lshw -c Network says Network unclaimed. how can i claim it ? backport installations says not found. please help.

---

### Post by chili555 on 2017-02-16
Did you run the script? Didn't it produce a report? We can see how to help you if you simply post the result. I haven't the faintest idea how to "claim" it without lots of additional information that is right in the report.

---

### Post by ashokcool on 2017-02-16
running the script says unable to resolve host address github.com

---

### Post by ashokcool on 2017-02-16
*-network UNCLAIMED     
       description: Network controller
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: cb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:32200000-32201fff

---

### Post by chili555 on 2017-02-16
Please post:```
lspci -nnk | grep 0280
uname -r
dmesg | grep iwl
rfkill list all
```

---

### Post by ashokcool on 2017-02-16
```
lspci -nnk | grep 0280
```
01:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev cb)


```
uname -r
```
3.10.40-ga7da876


```
dmesg | grep iwl
```
no reply




```
rfkill list all
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by wildmanne39 on 2017-02-16
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by ashokcool on 2017-02-16
ok will do. thank you for your information

---

### Post by chili555 on 2017-02-16
```
uname -r
3.10.40-ga7da876

```I suspect this is not Ubuntu.

Your Intel 7260 device will not be supported until kernel version 4.1 and later. 

I haven't a clue what it is that you are running and therefor not a clue as to how to install a 4.1 kernel. Sorry.

---

### Post by ashokcool on 2017-02-17
```
ubuntu@tegra-ubuntu:~$ lspci -nnk
```
00:00.0 PCI bridge [0604]: NVIDIA Corporation TegraK1 PCIe x4 Bridge [10de:0e12] (rev a1)
        Kernel driver in use: pcieport
01:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev cb)
        Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4c70]
02:00.0 PCI bridge [0604]: NVIDIA Corporation TegraK1 PCIe x1 Bridge [10de:0e13] (rev a1)
        Kernel driver in use: pcieport
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
        Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
        Kernel driver in use: r8169

---

### Post by ashokcool on 2017-02-17
there is no driver in the kernel used by the Intel module. Does it signify you anything ? Is it a kernel issue or ubuntu issue ? please help.

---

### Post by chili555 on 2017-02-17
> **ashokcool said:**
> there is no driver in the kernel used by the Intel module. Does it signify you anything ? Is it a kernel issue or ubuntu issue ? please help.Yes, it signifies just exactly what I said. You are running kernel version 3.10 and there is no support for your Intel 7260 wireless until kernel version 4.1 and later.

You are evidently not running any desktop or server version of Ubuntu and so I have no suggestions as to how to install a newer kernel version. 

The kernel developers try to include drivers for everything they know about when they release the next kernel. Some time well after 3.10 was released, Intel released its 7260 wireless. Kernel version 3.10 doesn't include its driver because it *didn't even exist *when 3.10 was written and released.

If you were running any standard Ubuntu version, I'd suggest that you install Ubuntu 16.04 which includes kernel version 4.4 and you'd be all set.

But you are not.

---

