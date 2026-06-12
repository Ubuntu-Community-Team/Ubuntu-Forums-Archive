---
title: "atheros Ar58bxb63 not working on ubuntu 12.04"
date: 2016-11-11
forum: Networking &amp; Wireless
---

### Post by chincerdante on 2016-11-11
Good Day all

i been having problems with my compaq presario f700 (F754LA) 
the wifi card cant be detected apparently and i havent been able to find proper drivers for ubuntu, running a lspci command also dont recognize the card at all and im not sure of where i can find proper drivers for this card, i can tell by opening the laptop and reading that is an atheros AR58BXB63
lspci results:
```
00:00.0 RAM memory: NVIDIA Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: NVIDIA Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: NVIDIA Corporation MCP67 Co-processor (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB controller: NVIDIA Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB controller: NVIDIA Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB controller: NVIDIA Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:08.0 PCI bridge: NVIDIA Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: NVIDIA Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: NVIDIA Corporation C67 [GeForce 7000M / nForce 610M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
```

---

### Post by Hadaka on 2016-11-11
Hi, your wireless card is not showing in your "lspci" list.
Let-s issue some commands to ask directly about the wireless and
nothing else. First to insure that the card is functioning, shut down
remove the power cord and remove the battery. Then remove and
inspect the card for anything damaged,missing,burned or corrosion
on the contacts or the pci slot. If all looks well firmly seat the card
then replace the battery and power back up and issue these commands...
```
lspci -nnk | grep -iA2 0280
```
and
```
nmcli nm
```
verifi that WIFI-HARDWARE and WIFI  are "enabled"
please post the output of both commands
thanks.

---

### Post by wildmanne39 on 2016-11-11
I believe that is a old computer so you can see if this command sees your card.
```
sudo pccardctl ident
```

---

### Post by wildmanne39 on 2016-11-11
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

