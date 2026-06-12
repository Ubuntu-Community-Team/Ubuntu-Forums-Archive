---
title: "No sound"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by Ymurti on 2011-04-26
Hi I have a Sony Vaio with Windows 7 and Ubuntu.
The sound works fine in Windows but when I switch to Ubuntu no sound at all.

Please can someone help me?

---

### Post by Ymurti on 2011-04-27
I entered the command:  lshw -c sound 
And got it:

 *-multimedia            
       description: Audio device
       product: Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:17 memory:f0040000-f0043fff
  *-multimedia
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:f5e00000-f5e03fff

---

### Post by Ymurti on 2011-04-27
And I got the following result from the command: lspci

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4381 (rev 11)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by Toz on 2011-04-27
1. Goto Applications ---> Accessories ---> Terminal

2. Copy and paste the code below into the terminal....

```
wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
```
3. Basically just press "y" for everything, and it will splurt out a link for you to go to on the web.

4. Copy and paste that link in the forums here....

---

### Post by Ymurti on 2011-04-27
> **Toz said:**
> 1. Goto Applications ---> Accessories ---> Terminal

2. Copy and paste the code below into the terminal....

```
wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
```
3. Basically just press "y" for everything, and it will splurt out a link for you to go to on the web.

4. Copy and paste that link in the forums here....
Your ALSA information is located at [http://www.alsa-project.org/db/?f=7bdb656ad68631a4b147168e35957cbf50838869](http://www.alsa-project.org/db/?f=7bdb656ad68631a4b147168e35957cbf50838869)

---

### Post by Ymurti on 2011-04-27
> **Ymurti said:**
> Your ALSA information is located at [http://www.alsa-project.org/db/?f=7bdb656ad68631a4b147168e35957cbf50838869](http://www.alsa-project.org/db/?f=7bdb656ad68631a4b147168e35957cbf50838869)
Thank You Toz,

I just upgraded from Ubuntu 10.04 to 10.10 and the sound is working fine. :)

---

