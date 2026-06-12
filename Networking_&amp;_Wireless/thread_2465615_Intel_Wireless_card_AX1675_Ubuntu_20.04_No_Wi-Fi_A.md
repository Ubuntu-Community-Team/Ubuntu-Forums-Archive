---
title: "Intel Wireless card AX1675 Ubuntu 20.04 No Wi-Fi Adapter Found"
date: 2021-08-06
forum: Networking &amp; Wireless
---

### Post by jamesyuan on 2021-08-06
My laptop MSI GS66 has Intel Killer WIFI 6E AX1675x, after the installation with kernel 5.11.0, there is no WIFI adapter found. Any suggestion to solve this problem?

---

### Post by chili555 on 2021-08-06
May we have a bit more information? Please run and post:

```
lspci -nnk | grep 0280 -A3
sudo modprobe iwlwifi && sudo dmesg | grep iwl
```

---

### Post by jamesyuan on 2021-11-04
Hi, thanks for your reply,
:~$ lspci -nnk | grep 0280 -A3 
30:00.0 Network controller [0280]: Intel Corporation Device [8086:2725] (rev 1a) Subsystem: Bigfoot Networks, Inc. Device [1a56:1674] Kernel modules: wl

and the last commands got nothing

---

### Post by chili555 on 2021-11-04
Please see: [https://askubuntu.com/questions/1364424/kernel-5-11-wi-fi-unclaimed-dmesg-grep-iwlwifi-is-empty-wifi-80862725](https://askubuntu.com/questions/1364424/kernel-5-11-wi-fi-unclaimed-dmesg-grep-iwlwifi-is-empty-wifi-80862725)

I suggest that you install Ubuntu 21.10 which uses the needed 5.13 kernel.

---

### Post by jamesyuan on 2021-11-25
> **chili555 said:**
> Please see: [https://askubuntu.com/questions/1364424/kernel-5-11-wi-fi-unclaimed-dmesg-grep-iwlwifi-is-empty-wifi-80862725](https://askubuntu.com/questions/1364424/kernel-5-11-wi-fi-unclaimed-dmesg-grep-iwlwifi-is-empty-wifi-80862725)

I suggest that you install Ubuntu 21.10 which uses the needed 5.13 kernel.



Hi,

Thanks, actually it works as I installed latest kernel 5.15. However, the new problem comes together hah. My GPU does not work.:eek:

---

### Post by mIk3_08 on 2021-11-25
> **jamesyuan said:**
> Hi,
Thanks, actually it works as I installed latest kernel 5.15. However, the new problem comes together hah. My GPU does not work.:eek:
It will be more better if you can run this command below in your terminal and show us your result here in thread wrap with code.
```
sudo lshw
```
and this
```
sudo dmesg
```
This is to show us your hardware system information on your machine. Thanks a lot and cheers.

---

### Post by jamesyuan on 2021-11-26
Hi&#65292;

Thanks for your help very much, I install kernel 5.15 and 5,16 both works for wifi issue. However, when I run the command 'nvidia-smi' it gives me &#8220;NVIDIA-SMI has failed because it couldn&#8217;t communicate with the NVIDIA driver&#8221;. Even I tried to switch back to 5.11, it still give me the same error. However, I found cudatookit from Nvidia only support GLIBC 2.13 for Ubuntu 20.04, meanwhile the requirement of kernel 5.15+ is more than 2.13.

---

### Post by jamesyuan on 2021-11-26
> **mIk3_08 said:**
> It will be more better if you can run this command below in your terminal and show us your result here in thread wrap with code.
```
sudo lshw
```
and this
```
sudo dmesg
```
This is to show us your hardware system information on your machine. Thanks a lot and cheers.


```
           *-display
                description: VGA compatible controller
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: /dev/fb0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller cap_list fb
                configuration: depth=32 latency=0 mode=2560x1440 visual=truecolor xres=2560 yres=1440
                resources: iomemory:600-5ff iomemory:620-61f memory:83000000-83ffffff memory:6000000000-61ffffffff memory:6200000000-6201ffffff ioport:4000(size=128) memory:84000000-8407ffff
           *-multimedia
                description: Audio device
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:84080000-84083fff
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list
             configuration: driver=i915 latency=0
             resources: iomemory:620-61f iomemory:400-3ff irq:176 memory:622c000000-622cffffff memory:4000000000-400fffffff ioport:5000(size=64) memory:c0000-dffff memory:4010000000-4016ffffff memory:4020000000-40ffffffff
        


        *-communication
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 11
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: iomemory:620-61f irq:159 memory:622d191000-622d191fff
        *-pci:3
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:126 ioport:3000(size=4096) memory:84300000-843fffff
           *-network
                description: Ethernet interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:2e:00.0
                logical name: enp46s0
                version: 06
                serial: d8:bb:c1:25:1e:ab
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.4-051504-generic firmware=rtl8125b-2_0.0.2 07/13/20 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:16 ioport:3000(size=256) memory:84300000-8430ffff memory:84310000-84313fff
        *-pci:4
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:127 ioport:7000(size=4096) memory:74400000-745fffff ioport:4017000000(size=2097152)
        *-pci:5
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d.4
             bus info: pci@0000:00:1d.4
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:128 memory:84200000-842fffff
           *-network
                description: Wireless interface
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:30:00.0
                logical name: wlp48s0
                version: 1a
                serial: 84:5c:f3:a0:65:e5
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=5.15.4-051504-generic firmware=63.c04f3485.0 ty-a0-gf-a0-63.uc ip=192.168.1.112 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:16 memory:84200000-84203fff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 11
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=sof-audio-pci-intel-tgl latency=32
             resources: iomemory:620-61f iomemory:620-61f irq:177 memory:622d188000-622d18bfff memory:622d000000-622d0fffff
        *-serial:1
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 11
             width: 64 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: iomemory:620-61f irq:16 memory:622d190000-622d1900ff ioport:efa0(size=32)
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@3:7
       logical name: wlxe0e1a951e397
       serial: e0:e1:a9:51:e3:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu driverversion=5.15.4-051504-generic multicast=yes wireless=unassociated
           *-display
                description: VGA compatible controller
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: /dev/fb0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller cap_list fb
                configuration: depth=32 latency=0 mode=2560x1440 visual=truecolor xres=2560 yres=1440
                resources: iomemory:600-5ff iomemory:620-61f memory:83000000-83ffffff memory:6000000000-61ffffffff memory:6200000000-6201ffffff ioport:4000(size=128) memory:84000000-8407ffff
           *-multimedia
                description: Audio device
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:84080000-84083fff
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list
             configuration: driver=i915 latency=0
             resources: iomemory:620-61f iomemory:400-3ff irq:176 memory:622c000000-622cffffff memory:4000000000-400fffffff ioport:5000(size=64) memory:c0000-dffff memory:4010000000-4016ffffff memory:4020000000-40ffffffff
        


        *-communication
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 11
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: iomemory:620-61f irq:159 memory:622d191000-622d191fff
        *-pci:3
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:126 ioport:3000(size=4096) memory:84300000-843fffff
           *-network
                description: Ethernet interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:2e:00.0
                logical name: enp46s0
                version: 06
                serial: d8:bb:c1:25:1e:ab
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.4-051504-generic firmware=rtl8125b-2_0.0.2 07/13/20 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:16 ioport:3000(size=256) memory:84300000-8430ffff memory:84310000-84313fff
        *-pci:4
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:127 ioport:7000(size=4096) memory:74400000-745fffff ioport:4017000000(size=2097152)
        *-pci:5
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d.4
             bus info: pci@0000:00:1d.4
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:128 memory:84200000-842fffff
           *-network
                description: Wireless interface
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:30:00.0
                logical name: wlp48s0
                version: 1a
                serial: 84:5c:f3:a0:65:e5
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=5.15.4-051504-generic firmware=63.c04f3485.0 ty-a0-gf-a0-63.uc ip=192.168.1.112 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:16 memory:84200000-84203fff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 11
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=sof-audio-pci-intel-tgl latency=32
             resources: iomemory:620-61f iomemory:620-61f irq:177 memory:622d188000-622d18bfff memory:622d000000-622d0fffff
        *-serial:1
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 11
             width: 64 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: iomemory:620-61f irq:16 memory:622d190000-622d1900ff ioport:efa0(size=32)
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@3:7
       logical name: wlxe0e1a951e397
       serial: e0:e1:a9:51:e3:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu driverversion=5.15.4-051504-generic multicast=yes wireless=unassociated
```

---

### Post by jamesyuan on 2021-11-26
> **mIk3_08 said:**
> It will be more better if you can run this command below in your terminal and show us your result here in thread wrap with code.
```
sudo lshw
```
and this
```
sudo dmesg
```
This is to show us your hardware system information on your machine. Thanks a lot and cheers.


I can't copy the output of sudo dmesg, it is too long.

I screen some about error and nvidia:

[COLOR=#000000][FONT=Calibri][    1.907091] audit: type=1400 audit(1637927283.720:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe" pid=674 comm="apparmor_parser"
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri][COLOR=inherit][    1.907093] audit: type=1400 audit(1637927283.720:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe//kmod" pid=674 comm="apparmor_parser"[/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri][COLOR=inherit]
[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri][COLOR=inherit][    0.899173] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS01._PLD due to previous error (AE_NOT_FOUND) (20210730/psparse-529)[COLOR=inherit][    0.901642] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS02._PLD due to previous error (AE_NOT_FOUND) (20210730/psparse-529)[/COLOR]
[COLOR=inherit][    0.901859] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS03._PLD due to previous error (AE_NOT_FOUND) (20210730/psparse-529)[/COLOR]
[COLOR=inherit][    0.902070] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS04._PLD due to previous error (AE_NOT_FOUND) (20210730/psparse-529)[/COLOR]
[COLOR=inherit][    0.904012] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS02._PLD due to previous error (AE_NOT_FOUND) (20210730/psparse-529)[/COLOR]
[COLOR=inherit][    0.904559] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS05._PLD due to previous error (AE_NOT_FOUND) (20210730/psparse-529)[/COLOR]
[COLOR=inherit][    1.602321] EXT4-fs (nvme0n1p9): re-mounted. Opts: errors=remount-ro. Quota mode: none.[/COLOR]
[COLOR=inherit][    1.809220] iwlwifi 0000:30:00.0: Direct firmware load for iwlwifi-ty-a0-gf-a0-66.ucode failed with error -2[/COLOR]
[COLOR=inherit][    1.809241] iwlwifi 0000:30:00.0: Direct firmware load for iwlwifi-ty-a0-gf-a0-65.ucode failed with error -2[/COLOR]
[COLOR=inherit][    1.809450] iwlwifi 0000:30:00.0: Direct firmware load for iwlwifi-ty-a0-gf-a0-64.ucode failed with error -2[/COLOR]
[COLOR=inherit][    1.893576] i915 0000:00:02.0: Direct firmware load for i915/tgl_dmc_ver2_12.bin failed with error -2[/COLOR][/COLOR][/FONT][/COLOR]

---

### Post by jamesyuan on 2021-11-26
BTW, do you have any ideas for installing WIFI Driver alone without updating Kernel.

---

### Post by chili555 on 2021-11-26
> **jamesyuan said:**
> BTW, do you have any ideas for installing WIFI Driver alone without updating Kernel.No, sorry.


Please see:

> [ 1.809220] iwlwifi 0000:30:00.0: Direct firmware load for iwlwifi-ty-a0-gf-a0-66.ucode failed with error -2
[ 1.809241] iwlwifi 0000:30:00.0: Direct firmware load for iwlwifi-ty-a0-gf-a0-65.ucode failed with error -2
[ 1.809450] iwlwifi 0000:30:00.0: Direct firmware load for iwlwifi-ty-a0-gf-a0-64.ucode failed with error -2

Please try:

```
cd /usr/lib/firmware
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-ty-a0-gf-a0-66.ucode

```
Reboot and let us see:

```
sudo dmesg | grep iwl

```

---

### Post by jeremy31 on 2021-11-26
It seems that the 5.13 kernel that exists in the linux-generic-hwe-20.04-edge package supports that wifi and may work better with your GPU if they patched the Nvidia driver for the 5.13 kernel

---

### Post by jamesyuan on 2021-11-26
Yes, I agree with you, 5.13 should support that WIFI card. However, I tried 5.13, 5.14, 5.15, and 5.16 kernels. I remember that the booting got stuck with some errors when I was using 5.13 and 5.14. Meanwhile, 5.15 and 5.16 are not compatible with Nvidia GPU. (You’re running a kernel built for 21.10 which has a dependency on glibc 2.33 so modules can’t be compiled.)see [https://forums.developer.nvidia.com/t/rtx-3050ti-not-working-with-ubuntu-20-04-kernel-5-15-rc7/196293](https://forums.developer.nvidia.com/t/rtx-3050ti-not-working-with-ubuntu-20-04-kernel-5-15-rc7/196293). 


I tried re-installed the system this morning (exhuasting hah), right now 5.11.04 at least works fine for GPU.

---

### Post by jamesyuan on 2021-11-26
Really thanks for your help,

nothing output after I used sudo dmesg | grep iwl

---

### Post by jamesyuan on 2021-11-26
I am not sure why people are saying '[COLOR=#232629][FONT=-apple-system]Kernels from the mainline kernel ppa are not compatible with 20.04 anymore, [/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]If you need 5.13 there's now a version in the official repo called linux-image-oem-20.04c[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system] [/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]'  [/FONT][/COLOR]https://askubuntu.com/questions/1351146/ubuntu-20-04-and-kernel-5-13-0-051300-generic-how-to-install-the-headers-and-li

---

### Post by jeremy31 on 2021-11-26
Did you try Ubuntu's 5.13 or the one from mainline?  They could be very different

---

### Post by jamesyuan on 2021-11-26
Yes, I tried to install 5.13 by

 wget [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.13/amd64/linux-headers-5.13.0-051300_5.13.0-051300.202106272333_all.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.13/amd64/linux-headers-5.13.0-051300_5.13.0-051300.202106272333_all.deb)
wget [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.13/amd64/linux-headers-5.13.0-051300-generic_5.13.0-051300.202106272333_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.13/amd64/linux-headers-5.13.0-051300-generic_5.13.0-051300.202106272333_amd64.deb)
wget [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.13/amd64/linux-image-unsigned-5.13.0-051300-generic_5.13.0-051300.202106272333_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.13/amd64/linux-image-unsigned-5.13.0-051300-generic_5.13.0-051300.202106272333_amd64.deb)
wget [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.13/amd64/linux-modules-5.13.0-051300-generic_5.13.0-051300.202106272333_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.13/amd64/linux-modules-5.13.0-051300-generic_5.13.0-051300.202106272333_amd64.deb)

and install these four packages. I see the errors about the dependencies of newer version lib and glicb during the installation. However, if I installed them, my CUDA crash again.

---

### Post by jeremy31 on 2021-11-26
That is from mainline and the 5.13 kernel went EOL at some point on mainline but the Ubuntu version is maintained until August next year.  Did you uninstall that 5.13 kernel and the others?

---

### Post by jamesyuan on 2021-11-26
Yes, I uninstalled it, currently i am using 5.11.0-4. It is hard to decied which kernel I should install next. Right now only 5.10 and 5.15 are long term supported kernels. However, I am afriad that 5.15 is not compatible with CUDA. While I think 5.10 is quite old. It is very annoying that WIFI can't be used.

---

### Post by jeremy31 on 2021-11-26
I would at least try ```
sudo apt install linux-generic-hwe-20.04-edge
```
Reboot when it is done and see if the graphics and wifi work

---

### Post by jamesyuan on 2021-11-26
Thanks but it does not work, it can even boot, the screen freeze in computer brand moment.

---

### Post by jeremy31 on 2021-11-27
Ok, lets try the backports on a working kernel
```
sudo apt install build-esssential
wget https://cdn.kernel.org/pub/linux/kernel/projects/backports/stable/v5.14.13/backports-5.14.13-1.tar.xz
tar -xvf backports-5.14.13-1.tar.xz
cd backports-5.14.13-1
make defconfig-wifi
make
sudo make install
make clean
```

You will likely see some errors but it should complete, reboot and test

---

### Post by jamesyuan on 2021-11-27
Hi,

:~/backports-5.14.13-1$ make defconfig-wifiGenerating local configuration database from kernel ... done.
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
lex -ozconf.lex.c -L zconf.l
make[2]: lex: Command not found
make[2]: *** [Makefile:23: zconf.lex.c] Error 127
make[1]: *** [Makefile.real:41: defconfig-wifi] Error 2
make: *** [Makefile:43: defconfig-wifi] Error 2
:~/backports-5.14.13-1$ make
/--------------
| Your backport package isn't configured, please configure it
| using one of the following options:
| To configure manually:
|     make oldconfig
|     make menuconfig
|
| To get defaults for certain drivers:
|     make defconfig-ar5523
|     make defconfig-ath10k
|     make defconfig-ath5k
|     make defconfig-ath6kl
|     make defconfig-ath9k
|     make defconfig-ath9k-debug
|     make defconfig-b43
|     make defconfig-b43legacy
|     make defconfig-brcmfmac
|     make defconfig-brcmsmac
|     make defconfig-carl9170
|     make defconfig-cw1200
|     make defconfig-hwsim
|     make defconfig-iwlwifi
|     make defconfig-libertas
|     make defconfig-libertas_tf
|     make defconfig-mwifiex
|     make defconfig-mwl8k
|     make defconfig-rtlwifi
|     make defconfig-wcn36xx
|     make defconfig-wifi
|     make defconfig-wil6210
|     make defconfig-wwan
\--
make[2]: *** [Makefile.real:45: .config] Error 1
make[1]: *** [Makefile:43: modules] Error 2
make: *** [Makefile:30: default] Error 2

---

### Post by jeremy31 on 2021-11-27
Two of the same errors in the same day?  [https://askubuntu.com/q/1376871/](https://askubuntu.com/q/1376871/)
Try ```
sudo apt install flex
```
Then try the make defconfig-wifi again

---

### Post by jamesyuan on 2021-11-27
> **jeremy31 said:**
> Two of the same errors in the same day?  [https://askubuntu.com/q/1376871/](https://askubuntu.com/q/1376871/)
Try ```
sudo apt install flex
```
Then try the make defconfig-wifi again


Nothing changed. The error is the same, and WIFI is still not working.

I am curious that distro and kernel both have LTS, will Ubuntu 20.04 provide new handware support in furture update like kernel?

---

### Post by jamesyuan on 2021-11-27
BTW,  I tried  'sudo apt-get install --install-recommends linux-generic-hwe-20.04-edge', actually 5.13 kernel is installed, I see some errors during the installation (e.g. error asscoaiting to 460 gpu driver) and I found that the laptop can not be booted (will be forwarded to initramfs interface )

---

### Post by jeremy31 on 2021-11-27
Are you sure the error was the same or did it say command yacc not found?
You might have to 
```
sudo apt install bison byacc
make clean
make defconfig-wifi
```
and see if it makes it through, it should say changes written to .config on the last line if it works

---

### Post by jamesyuan on 2021-11-27
> **jeremy31 said:**
> Are you sure the error was the same or did it say command yacc not found?
You might have to 
```
sudo apt install bison byacc
make clean
make defconfig-wifi
```
and see if it makes it through, it should say changes written to .config on the last line if it works


Hi,

Yes, this time works fine, the build takes 2-3 mins. After reboot, I can see the WIFI logo, however, the system is super slow now, it takes 2 mins to open settings, and it always shows looking for visible networks (nothing found). Meanwhile, something strange happend, for example, can't shut down (black screen with cursor), vscode can't be opened.

---

### Post by jeremy31 on 2021-11-27
Lets se what this shows ```
dmesg | grep iwl
```

---

### Post by jamesyuan on 2021-11-27
dmesg | grep iwl
[    3.238925] iwlwifi 0000:30:00.0: enabling device (0000 -> 0002)
[    3.244655] iwlwifi 0000:30:00.0: Direct firmware load for iwlwifi-ty-a0-gf-a0-64.ucode failed with error -2
[    3.246408] iwlwifi 0000:30:00.0: api flags index 2 larger than supported by driver
[    3.246433] iwlwifi 0000:30:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 0.0.2.25
[    3.246866] iwlwifi 0000:30:00.0: loaded firmware version 63.c04f3485.0 ty-a0-gf-a0-63.ucode op_mode iwlmvm
[    3.293784] iwlwifi 0000:30:00.0: Detected Killer(R) Wi-Fi 6E AX1675x 160MHz Wireless Network Adapter (210NGW), REV=0x420
[    3.336624] Modules linked in: coretemp snd_soc_dmic snd_sof_pci snd_sof_intel_hda_common snd_sof_intel_hda snd_sof_intel_byt snd_sof_intel_ipc snd_sof snd_hda_codec_hdmi snd_sof_xtensa_dsp snd_soc_hdac_hda snd_hda_ext_core snd_soc_acpi_intel_match snd_soc_acpi ledtrig_audio iwlmvm(OE+) snd_hda_intel snd_intel_dspcfg soundwire_intel soundwire_generic_allocation soundwire_cadence snd_hda_codec snd_hda_core mac80211(OE) snd_hwdep soundwire_bus snd_soc_core snd_compress ac97_bus snd_pcm_dmaengine snd_pcm libarc4 snd_seq_midi snd_seq_midi_event mei_hdcp snd_rawmidi intel_rapl_msr nls_iso8859_1 gpio_keys(+) i915(+) snd_seq kvm_intel fjes(-) iwlwifi(OE) uvcvideo(+) kvm snd_seq_device btusb videobuf2_vmalloc snd_timer btrtl crct10dif_pclmul videobuf2_memops ghash_clmulni_intel btbcm input_leds(+) videobuf2_v4l2 btintel cfg80211(OE) videobuf2_common bluetooth aesni_intel drm_kms_helper snd crypto_simd videodev processor_thermal_device cec cryptd mei_me processor_thermal_rfim rc_core glue_helper
[    3.337200] Modules linked in: intel_powerclamp coretemp snd_soc_dmic snd_sof_pci snd_sof_intel_hda_common snd_sof_intel_hda snd_sof_intel_byt snd_sof_intel_ipc snd_sof snd_hda_codec_hdmi snd_sof_xtensa_dsp snd_soc_hdac_hda snd_hda_ext_core snd_soc_acpi_intel_match snd_soc_acpi ledtrig_audio iwlmvm(OE+) snd_hda_intel snd_intel_dspcfg soundwire_intel soundwire_generic_allocation soundwire_cadence snd_hda_codec snd_hda_core mac80211(OE) snd_hwdep soundwire_bus snd_soc_core snd_compress ac97_bus snd_pcm_dmaengine snd_pcm libarc4 snd_seq_midi snd_seq_midi_event mei_hdcp snd_rawmidi intel_rapl_msr nls_iso8859_1 gpio_keys(+) i915(+) snd_seq kvm_intel fjes(-) iwlwifi(OE) uvcvideo(+) kvm snd_seq_device btusb videobuf2_vmalloc snd_timer btrtl crct10dif_pclmul videobuf2_memops ghash_clmulni_intel btbcm input_leds(+) videobuf2_v4l2 btintel cfg80211(OE) videobuf2_common bluetooth aesni_intel drm_kms_helper snd crypto_simd videodev processor_thermal_device cec cryptd mei_me processor_thermal_rfim
[    3.337588] Modules linked in: intel_powerclamp coretemp snd_soc_dmic snd_sof_pci snd_sof_intel_hda_common snd_sof_intel_hda snd_sof_intel_byt snd_sof_intel_ipc snd_sof snd_hda_codec_hdmi snd_sof_xtensa_dsp snd_soc_hdac_hda snd_hda_ext_core snd_soc_acpi_intel_match snd_soc_acpi ledtrig_audio iwlmvm(OE+) snd_hda_intel snd_intel_dspcfg soundwire_intel soundwire_generic_allocation soundwire_cadence snd_hda_codec snd_hda_core mac80211(OE) snd_hwdep soundwire_bus snd_soc_core snd_compress ac97_bus snd_pcm_dmaengine snd_pcm libarc4 snd_seq_midi snd_seq_midi_event mei_hdcp snd_rawmidi intel_rapl_msr nls_iso8859_1 gpio_keys(+) i915(+) snd_seq kvm_intel fjes(-) iwlwifi(OE) uvcvideo(+) kvm snd_seq_device btusb videobuf2_vmalloc snd_timer btrtl crct10dif_pclmul videobuf2_memops ghash_clmulni_intel btbcm input_leds(+) videobuf2_v4l2 btintel cfg80211(OE) videobuf2_common bluetooth aesni_intel drm_kms_helper snd crypto_simd videodev processor_thermal_device cec cryptd mei_me processor_thermal_rfim
[    3.338078] Modules linked in: x86_pkg_temp_thermal(+) intel_powerclamp coretemp snd_soc_dmic snd_sof_pci snd_sof_intel_hda_common snd_sof_intel_hda snd_sof_intel_byt snd_sof_intel_ipc snd_sof snd_hda_codec_hdmi snd_sof_xtensa_dsp snd_soc_hdac_hda snd_hda_ext_core snd_soc_acpi_intel_match snd_soc_acpi ledtrig_audio iwlmvm(OE+) snd_hda_intel snd_intel_dspcfg soundwire_intel soundwire_generic_allocation soundwire_cadence snd_hda_codec snd_hda_core mac80211(OE) snd_hwdep soundwire_bus snd_soc_core snd_compress ac97_bus snd_pcm_dmaengine snd_pcm libarc4 snd_seq_midi snd_seq_midi_event mei_hdcp snd_rawmidi intel_rapl_msr nls_iso8859_1 gpio_keys(+) i915(+) snd_seq kvm_intel fjes(-) iwlwifi(OE) uvcvideo(+) kvm snd_seq_device btusb videobuf2_vmalloc snd_timer btrtl crct10dif_pclmul videobuf2_memops ghash_clmulni_intel btbcm input_leds(+) videobuf2_v4l2 btintel cfg80211(OE) videobuf2_common bluetooth aesni_intel drm_kms_helper snd crypto_simd videodev processor_thermal_device cec cryptd mei_me
[    3.446051] iwlwifi 0000:30:00.0: loaded PNVM version 0xd35929d8
[    3.457350] iwlwifi 0000:30:00.0: Detected RF GF, rfid=0x10d000
[    3.526469] iwlwifi 0000:30:00.0: base HW address: 84:5c:f3:a0:65:e5
[    3.550699] iwlwifi 0000:30:00.0 wlp48s0: renamed from wlan0
[    5.188421] Modules linked in: cmac algif_hash algif_skcipher af_alg bnep nvidia_uvm(POE) nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) x86_pkg_temp_thermal intel_powerclamp coretemp snd_soc_dmic snd_sof_pci snd_sof_intel_hda_common snd_sof_intel_hda snd_sof_intel_byt snd_sof_intel_ipc snd_sof snd_hda_codec_hdmi snd_sof_xtensa_dsp snd_soc_hdac_hda snd_hda_ext_core snd_soc_acpi_intel_match snd_soc_acpi ledtrig_audio iwlmvm(OE) snd_hda_intel snd_intel_dspcfg soundwire_intel soundwire_generic_allocation soundwire_cadence snd_hda_codec snd_hda_core mac80211(OE) snd_hwdep soundwire_bus snd_soc_core snd_compress ac97_bus snd_pcm_dmaengine snd_pcm libarc4 snd_seq_midi snd_seq_midi_event mei_hdcp snd_rawmidi intel_rapl_msr nls_iso8859_1 gpio_keys i915 snd_seq kvm_intel iwlwifi(OE) uvcvideo kvm snd_seq_device btusb videobuf2_vmalloc snd_timer btrtl crct10dif_pclmul videobuf2_memops ghash_clmulni_intel btbcm input_leds videobuf2_v4l2 btintel cfg80211(OE) videobuf2_common bluetooth aesni_intel

---

### Post by jamesyuan on 2021-11-27
> **jeremy31 said:**
> Lets se what this shows ```
dmesg | grep iwl
```


I think I have to restore my laptop, cuz it is freezing now without any operations.

---

### Post by jeremy31 on 2021-11-27
Try ```
cd backports-5.14.13-1
sudo make uninstall
```
Reboot and we will see if the backports caused it

---

### Post by jamesyuan on 2021-11-27
> **jeremy31 said:**
> Try ```
cd backports-5.14.13-1
sudo make uninstall
```
Reboot and we will see if the backports caused it


Hi,

I did not uninstall that because I can't boot. However, I tried to restore the system (which is backuped before I installed backports-5.14.13-1)

Anyway, I think it's good news that at least  backports-5.14.13-1 will make the system detected the Killer wifi card.

---

### Post by jeremy31 on 2021-11-28
I wonder if we needed to delete the /lib/firmware/iwlwifi-ty-a0-gf-a0.pnvm file for it to work

---

### Post by jamesyuan on 2021-11-28
> **jeremy31 said:**
> I wonder if we needed to delete the /lib/firmware/iwlwifi-ty-a0-gf-a0.pnvm file for it to work

Hi,

Do you mean that I should try to install  backports-5.14.13-1 while remove the /lib/firmware/iwlwifi-ty-a0-gf-a0.pnvm?

---

### Post by jeremy31 on 2021-11-29
I wonder if it is the driver for the graphics that is causing the issue, what is the result for ```
dpkg -l | grep -i nvidia
```
We might need the driver version from a newer Ubuntu version for it to work

---

### Post by jamesyuan on 2022-01-05
Hi, thank for your help.

Probably, I just wait for Ubuntu hwe update to cover this WIFI card. I tried some kernels, they are not compatible.

---

