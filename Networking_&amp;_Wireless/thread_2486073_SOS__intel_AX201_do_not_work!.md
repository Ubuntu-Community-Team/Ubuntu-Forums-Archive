---
title: "SOS  intel AX201 do not work!"
date: 2023-04-19
forum: Networking &amp; Wireless
---

### Post by merhsia on 2023-04-19
I'm using ubuntu 20.04&#65292;with intel AX201&#65292;however&#65292;it don't work.
some information as follows
```

&#8203;*-network UNCLAIMED              description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: iomemory:600-5ff memory:6001114000-6001117fff
  *-network
       description: Ethernet interface
       product: Ethernet Controller I225-V
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 03
       serial: 7c:83:34:b9:27:28
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igc driverversion=6.1.0-1009-oem duplex=full firmware=1079:8770 ip=10.42.0.1 latency=0 link=yes multicast=yes port=twisted pair
       resources: irq:18 memory:80800000-808fffff memory:80900000-80903fff memory:80700000-807fffff
  *-network
       description: Ethernet interface
       product: Ethernet Controller I225-V
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 03
       serial: 7c:83:34:b9:27:29
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igc driverversion=6.1.0-1009-oem duplex=full firmware=1079:8770 ip=10.1.21.116 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:16 memory:80500000-805fffff memory:80600000-80603fff memory:80400000-804fffff
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.2 LTS
Release:	22.04
Codename:	jammy
Linux n100 6.1.0-1009-oem #9-Ubuntu SMP PREEMPT_DYNAMIC Fri Mar 31 09:59:10 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 3.5.0 present.


Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: AZW
	Product Name: EQ
	Version: Default string
	Serial Number: Default string
	UUID: 03000200-0400-0500-0006-000700080009
	Wake-up Type: Power Switch
	SKU Number: Default string
	Family: Default string


Invalid entry length (0). DMI table is broken! Stop.


00:00.0 Host bridge: Intel Corporation Device 461c
00:02.0 VGA compatible controller: Intel Corporation Device 46d1
00:14.0 USB controller: Intel Corporation Device 54ed
00:14.2 RAM memory: Intel Corporation Device 54ef
00:14.3 Network controller: Intel Corporation Device 54f0
00:15.0 Serial bus controller: Intel Corporation Device 54e8
00:15.1 Serial bus controller: Intel Corporation Device 54e9
00:16.0 Communication controller: Intel Corporation Device 54e0
00:17.0 SATA controller: Intel Corporation Device 54d3
00:1c.0 PCI bridge: Intel Corporation Device 54be
00:1d.0 PCI bridge: Intel Corporation Device 54b0
00:1d.2 PCI bridge: Intel Corporation Device 54b2
00:1e.0 Communication controller: Intel Corporation Device 54a8
00:1e.3 Serial bus controller: Intel Corporation Device 54ab
00:1f.0 ISA bridge: Intel Corporation Device 5481
00:1f.3 Audio device: Intel Corporation Device 54c8
00:1f.4 SMBus: Intel Corporation Device 54a3
00:1f.5 Serial bus controller: Intel Corporation Device 54a4
01:00.0 Ethernet controller: Intel Corporation Ethernet Controller I225-V (rev 03)
02:00.0 Ethernet controller: Intel Corporation Ethernet Controller I225-V (rev 03)
03:00.0 Non-Volatile memory controller: MAXIO Technology (Hangzhou) Ltd. NVMe SSD Controller MAP1202 (rev 01)
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 2717:5013 Xiaomi Inc. Mi Wireless Mouse
Bus 001 Device 004: ID 8087:0026 Intel Corp. AX201 Bluetooth
Bus 001 Device 002: ID 04d9:a0cd Holtek Semiconductor, Inc. USB Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by chili555 on 2023-04-19
> I'm using ubuntu 20.04&#65292;with intel AX201You are using an older Ubuntu version and its older kernel version with a very new wireless device. Please try:

```
sudo apt update
sudo apt install linux-generic-hwe-20.04
```

Reboot.

Is there any improvement?

Possibly useful: [https://askubuntu.com/questions/248914/what-is-hardware-enablement-hwe](https://askubuntu.com/questions/248914/what-is-hardware-enablement-hwe)

> Brand new hardware devices are released to the public always more frequently. And we want such hardware to be always working on Ubuntu, even if it has been released after an Ubuntu release. Six months (the time it takes for a new Ubuntu release to be made) is a very long period in the IT field. Hardware Enablement (HWE) is about that: catching up with the newest hardware technologies.

---

### Post by coffeecat on 2023-04-19
@merhsia, I've enclosed your various terminal outputs inside BBCode code tags. See how that restores the indented columns that you lost by posting as ordinary text. Please use code tags when posting terminal output, code, the contents of config files, and similar. There's a link in my sig if you need it. 

Also, when posting terminal output, please include the command(s) you used. Although experienced forum members can deduce what commands you likely used, it is best to be clear to avoid ambiguity, and also to see whether any commands you used need to be corrected/modified.

---

### Post by merhsia on 2023-04-20
I've-tried&#65292;but have no [COLOR=#000000]improvement.
Is there any more suggest?[/COLOR]

---

### Post by chili555 on 2023-04-20
> **merhsia said:**
> I've-tried&#65292;but have no [COLOR=#000000]improvement.
Is there any more suggest?[/COLOR]Let's see the result of:

```
lspci -nnk | grep 0280 -A3
sudo modprobe iwlwifi
sudo dmesg | grep iwl

```
Thanks.

---

### Post by merhsia on 2023-04-22
when input  # lspci -nnk | grep 0280 -A3
it shows 
```

00:14.3 Network controller [0280]: Intel Corporation Device [8086:54f0]
	DeviceName: Onboard - Ethernet
	Subsystem: Intel Corporation Device [8086:0244]
	Kernel modules: iwlwifi

```
when input  # sudo modprobe iwlwifi
it shows nothing
when input  # sudo dmesg | grep iwl
it shows
```

[    2.187211] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[    2.194029] iwlwifi: No config found for PCI dev 54f0/0244, rev=0x370, rfid=0x10c000
[    2.194045] iwlwifi: probe of 0000:00:14.3 failed with error -22

```

looking for your help.[COLOR=#000000]Thanks.[/COLOR]

---

### Post by chili555 on 2023-04-22
Please see the same issue here: [https://askubuntu.com/questions/1459856/intel-alder-lake-n100-wifi-and-bluetooth-issues](https://askubuntu.com/questions/1459856/intel-alder-lake-n100-wifi-and-bluetooth-issues) and also: [https://community.intel.com/t5/Wireless/AX101-Ubuntu-22-04-or-22-10-driver/td-p/1468063](https://community.intel.com/t5/Wireless/AX101-Ubuntu-22-04-or-22-10-driver/td-p/1468063)

> No config found for PCI dev 54f0/0244, rev=0x370, rfid=0x10c000I suggest that you try a live session of Ubuntu 23.04 to see if it works there. If it does not work, and I suspect it will not, I'd get an inexpensive USB wireless and wait for a kernel update.

I regret that I haven't a better suggestion.

---

### Post by merhsia on 2023-04-22
Thank you for your help!I have seen all the two issues.And they have the same output code with me.
I'm seeing that their hardware is Intel AX101&#65292;and have no support on the intel website here:[https://www.intel.com/content/www/us/en/support/articles/000005511/wireless.html](https://www.intel.com/content/www/us/en/support/articles/000005511/wireless.html)
My device is Intel AX201,and it is supported on the website list.Why i have the same trouble with them?

---

### Post by chili555 on 2023-04-23
The device can call itself AX201 or AX101 or Giraffe; however, if it is:

```
Network controller [0280]: Intel Corporation Device [8086:[COLOR="#FF0000"]54f0[/COLOR]]
	DeviceName: Onboard - Ethernet
	Subsystem: Intel Corporation Device [8086:[COLOR="#FF0000"]0244[/COLOR]]
```...then no configuration exists in the iwlwifi driver at this time. The common element is:```
 iwlwifi: No config found for PCI dev [COLOR="#FF0000"]54f0[/COLOR]/[COLOR="#FF0000"]0244[/COLOR], rev=0x370, rfid=0x10c000
```

---

### Post by jeremy31 on 2023-04-23
I found a possible fix but it will take some kernel patching [https://askubuntu.com/a/1462190](https://askubuntu.com/a/1462190)

---

### Post by chili555 on 2023-04-23
> **jeremy31 said:**
> I found a possible fix but it will take some kernel patching [https://askubuntu.com/a/1462190](https://askubuntu.com/a/1462190)The driver can be patched and installed; please check here: [https://askubuntu.com/questions/1356118/ax210-wifi-not-working-on-ubuntu21-04/1356136#1356136](https://askubuntu.com/questions/1356118/ax210-wifi-not-working-on-ubuntu21-04/1356136#1356136) However, it utilizes iwlwifi-backport-dkms. Do you think it will install correctly on the kernel version @merhsia is using?

> 6.1.0-1009-oem Would the driver work correctly in Ubuntu 23.04 using 6.2.0-xx?

---

### Post by jeremy31 on 2023-04-23
I think the 5.15 or 5.19 kernel could be fixed by patching the backport-iwlwifi or kernel source code.  I have no idea about kernels 6 and higher

---

### Post by #&amp;thj^% on 2023-04-23
> **jeremy31 said:**
>  I have no idea about kernels 6 and higher

I played with it about 3 weeks ago, and it was a no go OOTB.(6.2.0-20-generic)
This is kind of funny, but Intel claims it should work with kernels 6.1 and above: [https://community.intel.com/t5/Wireless/Intel-WiFi-6-AX201-160MHz-rev-01-does-t-work-at-all-Linux/m-p/1461767](https://community.intel.com/t5/Wireless/Intel-WiFi-6-AX201-160MHz-rev-01-does-t-work-at-all-Linux/m-p/1461767)
Maybe next kernel upgrade?

---

### Post by jeremy31 on 2023-04-23
If you want to try my patched module check first ```
mokutil --sb
```
As Secure Boot will need to be disabled then in terminal ```
sudo mv /lib/modules/6.1.0-1009-oem/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko /lib/modules/6.1.0-1009-oem/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko.bak
cd /lib/modules/6.1.0-1009-oem/kernel/drivers/net/wireless/intel/iwlwifi/
sudo wget https://gitlab.com/jeremy53561/iwlwifi-test/-/raw/main/iwlwifi.ko
echo "options iwlwifi disable_11ax=true| sudo tee /etc/modprobe.d/iwlopt.conf
```
Reboot

---

