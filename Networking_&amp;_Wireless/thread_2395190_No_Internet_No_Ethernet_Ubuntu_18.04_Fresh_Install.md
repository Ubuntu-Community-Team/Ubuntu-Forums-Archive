---
title: "No Internet No Ethernet Ubuntu 18.04 Fresh Install"
date: 2018-06-27
forum: Networking &amp; Wireless
---

### Post by fernando550 on 2018-06-27
My issue is simple...

I have no internet connectivity while connected via ethernet. Since I have no internet I cannot install anything else. However, it is worth mentioning that I had ubuntu installed on another disk and the internet did work. I installed it on a second disk and formatted the first disk to use it as network storage space under the FAT32 filesystem, and somehow now I am left without ethernet connection. In Settings>Network there is only the option to set up a VPN and a proxy, there is no wired option. I also do not see an internet icon at the top right on the top toolbar. Is it possible my actual ethernet port got damaged? I highly doubt that...

I am not familiar with too many linux commands, and so i've been following other posts by just copying and pasting what seems right. Not the best approach probably, but is the reason why I am now here writing a post.

 I cannot run lshw -c network
I run ip route show and I get nothing in return
I run ifconfig and it says ifconfig cannot be found as a package

Not sure what else to look for... Please advise.

EDIT: I think it is important to note that when i run ubuntu from the bootable USB drive that I am using, there isn't any internet connection either...

---

### Post by Autodave on 2018-06-28
Since no one else has jumped in, I would say that the second install failed somewhere. Have yo tried reinstalling it again? That would be my first thought.

---

### Post by fernando550 on 2018-06-28
i tried reinstalling just now and it has the same issue. It has no internet... I guess I can try reinstalling the actual boot USB? I wouldn't think that installing it on this particular drive would be a problem? Going to try and install it on my new drive... perhaps this drive is just bad...

---

### Post by praseodym on 2018-06-30
Please show the output of
```

lspci -nnk | grep -iA2 net
```

---

### Post by fernando550 on 2018-07-23
Upon entering "lspci -nnk | grep -iA2 net" it returns to the next line as if I've just pressed enter on an empty line...


Here's the report for just running "lscpi -nnk":

fernando@fernando-NY545AA-ABA-p6210y:~$ lspci -nnk
00:00.0 RAM memory [0500]: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller [10de:0754] (rev a2)
    Subsystem: Hewlett-Packard Company MCP78S [GeForce 8200] Memory Controller [103c:2a81]
00:01.0 ISA bridge [0601]: NVIDIA Corporation MCP78S [GeForce 8200] LPC Bridge [10de:075c] (rev a2)
    Subsystem: Hewlett-Packard Company MCP78S [GeForce 8200] LPC Bridge [103c:2a81]
00:01.1 SMBus [0c05]: NVIDIA Corporation MCP78S [GeForce 8200] SMBus [10de:0752] (rev a1)
    Subsystem: Hewlett-Packard Company MCP78S [GeForce 8200] SMBus [103c:2a81]
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c_nforce2, nv_tco
00:01.2 RAM memory [0500]: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller [10de:0751] (rev a1)
    Subsystem: Hewlett-Packard Company MCP78S [GeForce 8200] Memory Controller [103c:2a81]
00:01.3 Co-processor [0b40]: NVIDIA Corporation MCP78S [GeForce 8200] Co-Processor [10de:0753] (rev a2)
    Subsystem: Hewlett-Packard Company MCP78S [GeForce 8200] Co-Processor [103c:2a81]
00:01.4 RAM memory [0500]: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller [10de:0568] (rev a1)
    Subsystem: Hewlett-Packard Company MCP78S [GeForce 8200] Memory Controller [103c:2a81]
00:02.0 USB controller [0c03]: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077b] (rev a1)
    Subsystem: Hewlett-Packard Company MCP78S [GeForce 8200] OHCI USB 1.1 Controller [103c:2a81]
    Kernel driver in use: ohci-pci
00:02.1 USB controller [0c03]: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077c] (rev a1)
    Subsystem: Hewlett-Packard Company MCP78S [GeForce 8200] EHCI USB 2.0 Controller [103c:2a81]
    Kernel driver in use: ehci-pci
00:04.0 USB controller [0c03]: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077d] (rev a1)
    Subsystem: Hewlett-Packard Company MCP78S [GeForce 8200] OHCI USB 1.1 Controller [103c:2a81]
    Kernel driver in use: ohci-pci
00:04.1 USB controller [0c03]: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077e] (rev a1)
    Subsystem: Hewlett-Packard Company MCP78S [GeForce 8200] EHCI USB 2.0 Controller [103c:2a81]
    Kernel driver in use: ehci-pci
00:07.0 Audio device [0403]: NVIDIA Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio [10de:0774] (rev a1)
    Subsystem: Hewlett-Packard Company MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio [103c:2a81]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:08.0 PCI bridge [0604]: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge [10de:075a] (rev a1)
00:09.0 SATA controller [0106]: NVIDIA Corporation MCP78S [GeForce 8200] AHCI Controller [10de:0ad4] (rev a2)
    Subsystem: Hewlett-Packard Company MCP78S [GeForce 8200] AHCI Controller [103c:2a81]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:0b.0 PCI bridge [0604]: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:0569] (rev a1)
    Kernel modules: shpchp
00:10.0 PCI bridge [0604]: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:0778] (rev a1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:12.0 PCI bridge [0604]: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:075b] (rev a1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:13.0 PCI bridge [0604]: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge [10de:077a] (rev a1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:14.0 PCI bridge [0604]: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge [10de:077a] (rev a1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control [1022:1204]
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation C78 [GeForce 9100] [10de:0847] (rev a2)
    Subsystem: Hewlett-Packard Company C78 [GeForce 9100] [103c:2a81]
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau
04:00.0 SATA controller [0106]: JMicron Technology Corp. JMB363 SATA/IDE Controller [197b:2363] (rev 10)
    Subsystem: JMicron Technology Corp. JMB363 SATA/IDE Controller [197b:2363]
    Kernel driver in use: ahci
    Kernel modules: ahci
04:00.1 IDE interface [0101]: JMicron Technology Corp. JMB368 IDE controller [197b:0368] (rev 10)
    Subsystem: JMicron Technology Corp. JMB368 IDE controller [197b:1368]
    Kernel driver in use: pata_jmicron
    Kernel modules: pata_jmicron, pata_acpi
05:00.0 Communication controller [0780]: LSI Corporation Device [11c1:0630] (rev 01)
    Subsystem: LSI Corporation Device [11c1:0630]
06:00.0 SATA controller [0106]: Marvell Technology Group Ltd. Device [1b4b:9215] (rev 11)
    Subsystem: Marvell Technology Group Ltd. Device [1b4b:9215]
    Kernel driver in use: ahci
    Kernel modules: ahci

---

### Post by praseodym on 2018-07-24
Please run

```
dmesg >> dmesg.txt
```

and upload the file "dmesg.txt"

---

### Post by fernando550 on 2018-08-19
'Ubuntu Paste' link (couldnt upload due to size, and couldn't paste due to length):

[https://paste.ubuntu.com/p/nbBw8BKJmx/](https://paste.ubuntu.com/p/nbBw8BKJmx/)

---

