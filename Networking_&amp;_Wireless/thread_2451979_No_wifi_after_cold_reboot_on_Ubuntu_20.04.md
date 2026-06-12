---
title: "No wifi after cold reboot on Ubuntu 20.04"
date: 2020-10-14
forum: Networking &amp; Wireless
---

### Post by gacoka on 2020-10-14
Hello,

TL;DR

I recently cold booted my laptop and the wifi stopped working. Both wifi and bluetooth don't work but my priority is having wifi working. I tried searching for a solution for three days (including pertinent bugs and patches). However, I have not been able to find a fix yet. It used to work before and I have the wireless-info.txt for that too. If needed, I can upload it too.

Relevant specs:
---------------
Operating System:
Distributor ID:     Ubuntu
Description:     **Ubuntu 20.04.1 LTS**
Release:     20.04
Codename:     focal

PC make:** Dell Inspiron 7586 2-in-1 **

name@name:~$ dmesg | grep iwl
[    7.308388] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[    7.321602] iwlwifi 0000:00:14.3: Found debug destination: EXTERNAL_DRAM
[    7.321606] iwlwifi 0000:00:14.3: Found debug configuration: 0
[    7.322475] iwlwifi 0000:00:14.3: loaded firmware version 46.8902351f.0 op_mode iwlmvm
[    7.358023] iwlwifi 0000:00:14.3: **Detected Intel(R) Dual Band Wireless AC 9460,** REV=0x318
[    7.365714] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[    7.366888] iwlwifi 0000:00:14.3: Allocated 0x00400000 bytes for firmware monitor.
[    7.371425] iwlwifi 0000:00:14.3: Microcode SW error detected. Restarting 0x0.
[    7.371432] iwlwifi 0000:00:14.3: Not valid error log pointer 0x00000000 for Init uCode
[    7.371442] iwlwifi 0000:00:14.3: Fseq Registers:
[    7.371445] iwlwifi 0000:00:14.3: 0x8000E404 | FSEQ_ERROR_CODE
[    7.371455] iwlwifi 0000:00:14.3: 0x1440C788 | FSEQ_TOP_INIT_VERSION
[    7.371458] iwlwifi 0000:00:14.3: 0x45163477 | FSEQ_CNVIO_INIT_VERSION
[    7.371461] iwlwifi 0000:00:14.3: 0x055260E5 | FSEQ_OTP_VERSION
[    7.371464] iwlwifi 0000:00:14.3: 0x39B2FADF | FSEQ_TOP_CONTENT_VERSION
[    7.371466] iwlwifi 0000:00:14.3: 0xC3BBD7F0 | FSEQ_ALIVE_TOKEN
[    7.371469] iwlwifi 0000:00:14.3: 0x00489810 | FSEQ_CNVI_ID
[    7.371472] iwlwifi 0000:00:14.3: 0xF7EA67FF | FSEQ_CNVR_ID
[    7.371475] iwlwifi 0000:00:14.3: 0x01000100 | CNVI_AUX_MISC_CHIP
[    7.371511] iwlwifi 0000:00:14.3: 0xA5A5A5A2 | CNVR_AUX_MISC_CHIP
[    7.371586] iwlwifi 0000:00:14.3: 0xA5A5A5A2 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    7.371662] iwlwifi 0000:00:14.3: 0xA5A5A5A2 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    7.371866] iwlwifi 0000:00:14.3: SecBoot CPU1 Status: 0xa5a5a5a2, CPU2 Status: 0xa5a5a5a2
[    7.371877] iwlwifi 0000:00:14.3: Failed to start INIT ucode: -5
[    7.371880] iwlwifi 0000:00:14.3: Collecting data: trigger 16 fired.
[    7.618273] iwlwifi 0000:00:14.3: Firmware not running - cannot dump error
[    7.630421] iwlwifi 0000:00:14.3: **Failed to run INIT ucode: -5**

name@name:~$ lspci
00:14.3 Network controller: **Intel Corporation Cannon Point-LP CNVi [Wireless-AC] **(rev 30)

name@name:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

* I dont know why I do not have a WLAN option (it was there previously).

Here is the link to my wireless-info.txt for further scrutiny.
[https://pastebin.com/d4keAusL](https://pastebin.com/d4keAusL)

* I have currently tethered my connection to my phone and that is why there is an Ethernet option and usb0 in wireless-info.txt in ifconfig.
* I tried loading other iwlwifi firmware versions (including the -34.ucode from Intel and Dell and also the **-33, -34, -38, -41, -43 and -46.ucode** from /lib/firmware)


name@name:~$ apt list | grep linux-firmware
**linux-firmware/now 1.189** all [installed,local]

name@name:~$ uname -r
**5.4.0-42-generic**


name@name:~$ sudo lshw -C network
[sudo] password for name: 
  *-network                 
       description: Network controller
       product: **Cannon Point-LP CNVi [Wireless-AC]**
       vendor: **Intel Corporation**
       physical id: 14.3
       bus info: pci@0000:00:14.3
       version: 30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: driver=iwlwifi latency=0
       resources: irq:16 memory:a121c000-a121ffff
  *-network
       description: Ethernet interface
       physical id: 2
       bus info: usb@1:4
       logical name: usb0
       serial: 42:8a:b8:cf:17:bd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.39 link=yes multicast=yes

**Note:** I have an Intel Wireless AC 9560 wireless card.

---

