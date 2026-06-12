---
title: "NO Wifi on Acer Aspire Switch 10E"
date: 2016-08-28
forum: Networking &amp; Wireless
---

### Post by little.gray.rat on 2016-08-28
Hello, 

I have a problem with my netbook _Acer Aspire Switch 10E_. I was unable to install ubuntu 16 on it. So since yesterday I am still working on ubuntu 14.04 (64 bit). It seems to be OK, so I could install ubuntu on ssd and reboot. But the problem is I can not use the wifi. 

I followed the instructions on this link: [https://gist.github.com/franga2000/2154d09f864894b8fe84](https://gist.github.com/franga2000/2154d09f864894b8fe84). And tried to compile the driver with following repository: [https://github.com/SWW13/rtl8723as](https://github.com/SWW13/rtl8723as). It was not so helpful. 

Have anybody an idea how to fix the problem?

---

### Post by jeremy31 on 2016-08-28
*Thread moved to **Networking & Wireless**.*
See the wireless script link in my signature and post the results

Also post any result for ```
ls /sys/bus/sdio
```

---

### Post by little.gray.rat on 2016-08-28
Thank you for reply. Here is my wireless info and content of my sdio folder on device.


```

########## wireless info START ##########

Report from: 28 Aug 2016 17:50 CEST +0200

Booted last: 28 Aug 2016 17:48 CEST +0200

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.4.0-34-generic #53~14.04.1-Ubuntu SMP Wed Jul 27 16:56:40 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

##### lsusb #############################

Bus 002 Device 003: ID 18a5:024b Verbatim, Ltd 
Bus 002 Device 002: ID 0bda:0411 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 06cb:73f5 Synaptics, Inc. 
Bus 001 Device 002: ID 0bda:5411 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

toshiba_wmi            16384  0 
acer_wmi               20480  0 
snd_soc_rt5640        114688  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
snd_pcm               106496  4 snd_soc_rt5640,snd_soc_core,snd_soc_sst_mfld_platform,snd_pcm_dmaengine
wmi                    20480  2 toshiba_wmi,acer_wmi
video                  40960  2 i915,acer_wmi
sparse_keymap          16384  3 toshiba_wmi,acer_wmi,intel_hid

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

##### iwconfig ##########################

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       705     1  0 17:48 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0)

##### iwlist channels ###################

lo        no frequency information.

##### iwlist scan #######################

Sorry, try again.
lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1090 (alx)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[     6.375847] Modules linked in: toshiba_wmi acer_wmi intel_rapl  intel_powerclamp coretemp kvm_intel kvm irqbypass punit_atom_debug  crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul  glue_helper ablk_helper cryptd i915 joydev input_leds hid_multitouch  snd_intel_sst_acpi snd_intel_sst_core fdp_i2c snd_soc_sst_mfld_platform  fdp snd_soc_rt5640 i2c_hid rfcomm nci snd_soc_rl6231 drm_kms_helper nfc  snd_soc_core mei_txe bnep lpc_ich snd_compress ac97_bus mei  snd_pcm_dmaengine drm snd_pcm i2c_algo_bit processor_thermal_device  fb_sys_fops intel_soc_dts_iosf syscopyarea sysfillrect sysimgblt  snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device  snd_timer 8250_fintek wmi snd intel_hid dw_dmac video sparse_keymap  hci_uart dw_dmac_core btbcm btqca soundcore btintel bluetooth  i2c_designware_platform i2c_designware_core spi_pxa2xx_platform 8250_dw  nls_iso8859_1 pwm_lpss_platform pwm_lpss tpm_crb int3400_thermal  acpi_thermal_rel parport_pc soc_button_array ppdev acpi_pad  pinctrl_cherryview int3403_thermal int340x_thermal_zone lp mac_hid  parport hid_generic uas usb_storage usbhid hid mmc_block fjes sdhci_acpi  sdhci (repeated 2 times)

########## wireless info END ############


```


```

devices  drivers  drivers_autoprobe  drivers_probe  uevent

```

---

### Post by jeremy31 on 2016-08-28
Ok, lets see ```
ls /sys/bus/sdio/devices
```

---

### Post by little.gray.rat on 2016-08-28
The following folder /sys/bus/sdio/devices on Acer Aspire Switch 10E is empty. 
However, on my lenovo working laptop this folder is also empty but it has a wifi which works.

---

### Post by jeremy31 on 2016-08-28
Try ```
echo "blacklist toshiba_wmi" | sudo tee /etc/modprobe.d/toshiba_wmi.conf
```
Reboot

At some point Ubuntu must have detected a broadcom wireless card on the PCI bus along with an Atheros ethernet device but they don't show in lspci for some reason

---

### Post by little.gray.rat on 2016-08-28
After running your comment (adding toshiba wmi to "black list") the wifi didn't enabled. However toshiba wmi was removed from the list of moduls. 


```

##### lsmod #############################

acer_wmi               20480  0 
snd_soc_rt5640        114688  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
snd_pcm               106496  4 snd_soc_rt5640,snd_soc_core,snd_soc_sst_mfld_platform,snd_pcm_dmaengine
wmi                    20480  1 acer_wmi
video                  40960  2 i915,acer_wmi
sparse_keymap          16384  2 acer_wmi,intel_hid

```

after inserting the compiled modul from repository: (sudo modprobe r8723bs)

```

##### lsmod #############################

cfg80211              557056  1 r8723bs
acer_wmi               20480  0 
snd_soc_rt5640        114688  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
snd_pcm               106496  4 snd_soc_rt5640,snd_soc_core,snd_soc_sst_mfld_platform,snd_pcm_dmaengine
wmi                    20480  1 acer_wmi
video                  40960  2 i915,acer_wmi
sparse_keymap          16384  2 acer_wmi,intel_hid

```

but still nothing works. Any ideas?

---

### Post by jeremy31 on 2016-08-28
Does anything appear in ```
lspci
```

---

### Post by little.gray.rat on 2016-08-28
no, nothing at all...

---

### Post by jeremy31 on 2016-08-28
Can you do ```
dmesg > dmesg.txt
```
Then in your home folder find dmesg.txt and copy the contents and paste at paste.ubuntu.com and post a URL

I don't think you have the Realtek wireless unless there is something else going on with your install as a [bug report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1581711) in comment #21 shows what you should have had for a result of ls /sys/bus/sdio/devices if you had the Realtek

---

### Post by little.gray.rat on 2016-08-28
Please find the output of command below:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.4.0-34-generic (buildd@lgw01-52) (gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04.3) ) #53~14.04.1-Ubuntu SMP Wed Jul 27 16:56:40 UTC 2016 (Ubuntu 4.4.0-34.53~14.04.1-generic 4.4.15)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-34-generic.efi.signed root=UUID=8da10122-a675-4c11-aa1a-402cbb13a0ba ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: Legacy x87 FPU detected.
[    0.000000] x86/fpu: Using 'lazy' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000008efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000008f000-0x000000000008ffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000000090000-0x000000000009ffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000074181fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000074182000-0x00000000741a2fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000741a3000-0x00000000779a2fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000779a3000-0x0000000077a32fff] type 20
[    0.000000] BIOS-e820: [mem 0x0000000077a33000-0x000000007a4cefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007a4cf000-0x000000007a5cefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007a5cf000-0x000000007a60efff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007a60f000-0x000000007b3ddfff] usable
[    0.000000] BIOS-e820: [mem 0x000000007b3de000-0x000000007bcddfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007bcde000-0x000000007bffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000e3ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fea00000-0x00000000feafffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed01000-0x00000000fed01fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed03000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed06000-0x00000000fed06fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed08000-0x00000000fed09fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1cfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fedbffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.40 by INSYDE Corp.
[    0.000000] efi:  ACPI 2.0=0x7a60e014  ESRT=0x77a46718  SMBIOS=0x77a40000 
[    0.000000] esrt: Reserving ESRT space from 0x0000000077a46718 to 0x0000000077a46750.
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: Acer Aspire SW3-016/Gummi CHT, BIOS V1.12 12/25/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x7c000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 07E000000 mask FFE000000 uncachable
[    0.000000]   3 base 07D000000 mask FFF000000 uncachable
[    0.000000]   4 base 07C800000 mask FFF800000 uncachable
[    0.000000]   5 base 07C400000 mask FFFC00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] BRK [0x03003000, 0x03003fff] PGTABLE
[    0.000000] BRK [0x03004000, 0x03004fff] PGTABLE
[    0.000000] BRK [0x03005000, 0x03005fff] PGTABLE
[    0.000000] BRK [0x03006000, 0x03006fff] PGTABLE
[    0.000000] BRK [0x03007000, 0x03007fff] PGTABLE
[    0.000000] BRK [0x03008000, 0x03008fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x357b2000-0x36bd0fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x000000007A60E014 000024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 0x000000007A5D9188 0000D4 (v01 ACRSYS ACRPRDCT 00000003      01000013)
[    0.000000] ACPI: FACP 0x000000007A604000 00010C (v05 ACRSYS ACRPRDCT 00000003 1025 00040000)
[    0.000000] ACPI: DSDT 0x000000007A5E7000 017364 (v02 ACRSYS ACRPRDCT 00000003 1025 00040000)
[    0.000000] ACPI: FACS 0x000000007A566000 000040
[    0.000000] ACPI: UEFI 0x000000007A60D000 000236 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: MSDM 0x000000007A60C000 000055 (v03 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: UEFI 0x000000007A60B000 000042 (v01 ACRSYS ACRPRDCT 00000000 1025 00040000)
[    0.000000] ACPI: SSDT 0x000000007A606000 0042D9 (v01 ACRSYS ACRPRDCT 00001000 1025 00040000)
[    0.000000] ACPI: HPET 0x000000007A603000 000038 (v01 ACRSYS ACRPRDCT 00000003 1025 00040000)
[    0.000000] ACPI: LPIT 0x000000007A602000 000104 (v01 ACRSYS ACRPRDCT 00000003 1025 00040000)
[    0.000000] ACPI: APIC 0x000000007A601000 00006C (v03 ACRSYS ACRPRDCT 00000003 1025 00040000)
[    0.000000] ACPI: MCFG 0x000000007A600000 00003C (v01 ACRSYS ACRPRDCT 00000003 1025 00040000)
[    0.000000] ACPI: PRAM 0x000000007A5FF000 000030 (v01 ACRSYS ACRPRDCT 00000003 1025 00040000)
[    0.000000] ACPI: SSDT 0x000000007A5E6000 0005D0 (v01 ACRSYS ACRPRDCT 00000003 1025 00040000)
[    0.000000] ACPI: SSDT 0x000000007A5E2000 003AA1 (v01 ACRSYS ACRPRDCT 00000003 1025 00040000)
[    0.000000] ACPI: SSDT 0x000000007A5E1000 000058 (v01 ACRSYS ACRPRDCT 00000003 1025 00040000)
[    0.000000] ACPI: SSDT 0x000000007A5E0000 000763 (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: SSDT 0x000000007A5DF000 000290 (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: SSDT 0x000000007A5DE000 00017A (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: SSDT 0x000000007A5DD000 000432 (v01 ACRSYS ACRPRDCT 00001000 1025 00040000)
[    0.000000] ACPI: TPM2 0x000000007A5DC000 000034 (v03 ACRSYS ACRPRDCT 00000000 1025 00040000)
[    0.000000] ACPI: TCPA 0x000000007A5DB000 000032 (v02 ACRSYS ACRPRDCT 00000000 1025 00040000)
[    0.000000] ACPI: CSRT 0x000000007A605000 00014C (v00 ACRSYS ACRPRDCT 00000003 1025 00040000)
[    0.000000] ACPI: FPDT 0x000000007A5D8000 000044 (v01 ACRSYS ACRPRDCT 00000002 1025 00040000)
[    0.000000] ACPI: BGRT 0x000000007A5DA000 000038 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000007bffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x774bc000-0x774c0fff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x000000007bffffff]
[    0.000000]   Normal   empty
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000008efff]
[    0.000000]   node   0: [mem 0x0000000000090000-0x000000000009ffff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000001fffffff]
[    0.000000]   node   0: [mem 0x0000000020200000-0x0000000074181fff]
[    0.000000]   node   0: [mem 0x00000000741a3000-0x00000000779a2fff]
[    0.000000]   node   0: [mem 0x000000007a60f000-0x000000007b3ddfff]
[    0.000000]   node   0: [mem 0x000000007bcde000-0x000000007bffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000007bffffff]
[    0.000000] On node 0 totalpages: 493585
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 23 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7872 pages used for memmap
[    0.000000]   DMA32 zone: 489587 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0x7cc00000-0x7ebfffff
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-114
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0008f000-0x0008ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x74182000-0x741a2fff]
[    0.000000] PM: Registered nosave memory: [mem 0x779a3000-0x77a32fff]
[    0.000000] PM: Registered nosave memory: [mem 0x77a33000-0x7a4cefff]
[    0.000000] PM: Registered nosave memory: [mem 0x7a4cf000-0x7a5cefff]
[    0.000000] PM: Registered nosave memory: [mem 0x7a5cf000-0x7a60efff]
[    0.000000] PM: Registered nosave memory: [mem 0x7b3de000-0x7bcddfff]
[    0.000000] e820: [mem 0x7ec00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff880077200000 s98008 r8192 d28968 u524288
[    0.000000] pcpu-alloc: s98008 r8192 d28968 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 485626
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-34-generic.efi.signed root=UUID=8da10122-a675-4c11-aa1a-402cbb13a0ba ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 1853728K/1974340K available (8175K kernel code, 1292K rwdata, 3960K rodata, 1484K init, 1292K bss, 120612K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:1024 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: PIT calibration matches HPET. 1 loops
[    0.000000] tsc: Detected 1439.962 MHz processor
[    0.000051] Calibrating delay loop (skipped), value calculated using timer frequency.. 2879.92 BogoMIPS (lpj=5759848)
[    0.000061] pid_max: default: 32768 minimum: 301
[    0.000075] ACPI: Core revision 20150930
[    0.056754] ACPI: 9 ACPI AML tables successfully acquired and loaded
[    0.058736] Security Framework initialized
[    0.058745] Yama: becoming mindful.
[    0.058787] AppArmor: AppArmor initialized
[    0.059166] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.060448] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.061051] Mount-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.061066] Mountpoint-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.061584] Initializing cgroup subsys io
[    0.061598] Initializing cgroup subsys memory
[    0.061616] Initializing cgroup subsys devices
[    0.061624] Initializing cgroup subsys freezer
[    0.061632] Initializing cgroup subsys net_cls
[    0.061639] Initializing cgroup subsys perf_event
[    0.061646] Initializing cgroup subsys net_prio
[    0.061654] Initializing cgroup subsys hugetlb
[    0.061664] Initializing cgroup subsys pids
[    0.061703] CPU: Physical Processor ID: 0
[    0.061707] CPU: Processor Core ID: 0
[    0.061715] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.061719] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.067199] mce: CPU supports 6 MCE banks
[    0.067216] CPU0: Thermal monitoring enabled (TM1)
[    0.067223] process: using mwait in idle threads
[    0.067232] Last level iTLB entries: 4KB 48, 2MB 0, 4MB 0
[    0.067236] Last level dTLB entries: 4KB 256, 2MB 16, 4MB 16, 1GB 0
[    0.067760] Freeing SMP alternatives memory: 28K (ffffffff81eb7000 - ffffffff81ebe000)
[    0.076446] ftrace: allocating 32026 entries in 126 pages
[    0.101828] smpboot: Max logical packages: 1
[    0.101836] smpboot: APIC(0) Converting physical 0 to logical package 0
[    0.104105] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.143806] TSC deadline timer enabled
[    0.143816] smpboot: CPU0: Intel(R) Atom(TM) x5-Z8300  CPU @ 1.44GHz (family: 0x6, model: 0x4c, stepping: 0x3)
[    0.143859] Performance Events: PEBS fmt2+, 8-deep LBR, Silvermont events, full-width counters, Intel PMU driver.
[    0.143882] ... version:                3
[    0.143885] ... bit width:              40
[    0.143889] ... generic registers:      2
[    0.143892] ... value mask:             000000ffffffffff
[    0.143894] ... max period:             000000ffffffffff
[    0.143897] ... fixed-purpose events:   3
[    0.143899] ... event mask:             0000000700000003
[    0.146167] x86: Booting SMP configuration:
[    0.146174] .... node  #0, CPUs:      #1
[    0.154033] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.154330]  #2 #3
[    0.169831] x86: Booted up 1 node, 4 CPUs
[    0.169838] smpboot: Total of 4 processors activated (11519.69 BogoMIPS)
[    0.171068] devtmpfs: initialized
[    0.180716] evm: security.selinux
[    0.180722] evm: security.SMACK64
[    0.180724] evm: security.SMACK64EXEC
[    0.180727] evm: security.SMACK64TRANSMUTE
[    0.180729] evm: security.SMACK64MMAP
[    0.180732] evm: security.ima
[    0.180736] evm: security.capability
[    0.180899] PM: Registering ACPI NVS region [mem 0x0008f000-0x0008ffff] (4096 bytes)
[    0.180905] PM: Registering ACPI NVS region [mem 0x7a4cf000-0x7a5cefff] (1048576 bytes)
[    0.181145] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.181380] pinctrl core: initialized pinctrl subsystem
[    0.181674] RTC time: 19:38:24, date: 08/28/16
[    0.182043] NET: Registered protocol family 16
[    0.190583] cpuidle: using governor ladder
[    0.202597] cpuidle: using governor menu
[    0.202606] PCCT header not found.
[    0.202785] ACPI: bus type PCI registered
[    0.202791] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.202984] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.202991] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in E820
[    0.203007] PCI: Using configuration type 1 for base access
[    0.215704] ACPI: Added _OSI(Module Device)
[    0.215710] ACPI: Added _OSI(Processor Device)
[    0.215714] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.215717] ACPI: Added _OSI(Processor Aggregator Device)
[    0.252372] ACPI: Dynamic OEM Table Load:
[    0.252401] ACPI: SSDT 0xFFFF880073B71800 00057B (v01 PmRef  Cpu0Ist  00003000 INTL 20130117)
[    0.254651] ACPI: Dynamic OEM Table Load:
[    0.254669] ACPI: SSDT 0xFFFF880073BA2C00 0003A5 (v01 PmRef  Cpu0Cst  00003001 INTL 20130117)
[    0.257408] ACPI: Dynamic OEM Table Load:
[    0.257425] ACPI: SSDT 0xFFFF88007AC12000 00015F (v01 PmRef  ApIst    00003000 INTL 20130117)
[    0.259596] ACPI: Dynamic OEM Table Load:
[    0.259612] ACPI: SSDT 0xFFFF880073BFE240 00008D (v01 PmRef  ApCst    00003000 INTL 20130117)
[    0.263821] ACPI: Interpreter enabled
[    0.263841] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150930/hwxface-580)
[    0.263856] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150930/hwxface-580)
[    0.263866] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20150930/hwxface-580)
[    0.263898] ACPI: (supports S0 S4 S5)
[    0.263904] ACPI: Using IOAPIC for interrupt routing
[    0.263986] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.265942] ACPI: Power Resource [USBC] (on)
[    0.267199] ACPI: Power Resource [WWPR] (off)
[    0.268009] ACPI: Power Resource [WWPR] (off)
[    0.269245] ACPI: Power Resource [WWPR] (off)
[    0.270044] ACPI: Power Resource [WWPR] (off)
[    0.270929] ACPI: Power Resource [WWPR] (off)
[    0.281246] ACPI: Power Resource [CLK3] (on)
[    0.281369] ACPI: Power Resource [CLK4] (on)
[    0.281612] ACPI: Power Resource [P28T] (off)
[    0.281720] ACPI: Power Resource [P18D] (off)
[    0.283109] ACPI: Power Resource [CLK2] (on)
[    0.283586] ACPI: Power Resource [P18T] (off)
[    0.285652] ACPI: Power Resource [CLK0] (on)
[    0.285773] ACPI: Power Resource [CLK1] (on)
[    0.292726] ACPI: Power Resource [ID3C] (on)
[    0.292916] ACPI: Power Resource [P12T] (off)
[    0.299681] ACPI: Power Resource [P28X] (off)
[    0.299801] ACPI: Power Resource [P18X] (off)
[    0.299914] ACPI: Power Resource [P12X] (off)
[    0.300039] ACPI: Power Resource [P28P] (off)
[    0.300152] ACPI: Power Resource [P18P] (off)
[    0.300270] ACPI: Power Resource [P19X] (off)
[    0.300382] ACPI: Power Resource [P06X] (off)
[    0.300518] ACPI: Power Resource [P3P3] (off)
[    0.300639] ACPI: Power Resource [P28W] (off)
[    0.300757] ACPI: Power Resource [P18W] (off)
[    0.300880] ACPI: Power Resource [P12W] (off)
[    0.300992] ACPI: Power Resource [P33W] (off)
[    0.301113] ACPI: Power Resource [P33X] (off)
[    0.308001] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.308017] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.308569] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.308605] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.309507] PCI host bridge to bus 0000:00
[    0.309517] pci_bus 0000:00: root bus resource [io  0x0070-0x0077]
[    0.309524] pci_bus 0000:00: root bus resource [io  0x0000-0x006f window]
[    0.309529] pci_bus 0000:00: root bus resource [io  0x0078-0x0cf7 window]
[    0.309534] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.309539] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.309544] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff window]
[    0.309549] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000fffff window]
[    0.309554] pci_bus 0000:00: root bus resource [mem 0x20000000-0x201fffff window]
[    0.309559] pci_bus 0000:00: root bus resource [mem 0x7cc00001-0x7ec00000 window]
[    0.309564] pci_bus 0000:00: root bus resource [mem 0x80000000-0xdfffffff window]
[    0.309571] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.309591] pci 0000:00:00.0: [8086:2280] type 00 class 0x060000
[    0.309890] pci 0000:00:02.0: [8086:22b0] type 00 class 0x030000
[    0.309938] pci 0000:00:02.0: reg 0x10: [mem 0x90000000-0x90ffffff 64bit]
[    0.309956] pci 0000:00:02.0: reg 0x18: [mem 0x80000000-0x8fffffff 64bit pref]
[    0.309968] pci 0000:00:02.0: reg 0x20: [io  0x1000-0x103f]
[    0.310234] pci 0000:00:03.0: [8086:22b8] type 00 class 0x048000
[    0.310267] pci 0000:00:03.0: reg 0x10: [mem 0x91000000-0x913fffff]
[    0.310550] pci 0000:00:0b.0: [8086:22dc] type 00 class 0x118000
[    0.310596] pci 0000:00:0b.0: reg 0x10: [mem 0x91818000-0x91818fff 64bit]
[    0.310915] pci 0000:00:14.0: [8086:22b5] type 00 class 0x0c0330
[    0.310969] pci 0000:00:14.0: reg 0x10: [mem 0x91800000-0x9180ffff 64bit]
[    0.311067] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.311344] pci 0000:00:1a.0: [8086:2298] type 00 class 0x108000
[    0.311387] pci 0000:00:1a.0: reg 0x10: [mem 0x91700000-0x917fffff]
[    0.311403] pci 0000:00:1a.0: reg 0x14: [mem 0x91600000-0x916fffff]
[    0.311494] pci 0000:00:1a.0: PME# supported from D0 D3hot
[    0.311792] pci 0000:00:1f.0: [8086:229c] type 00 class 0x060100
[    0.322712] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.322908] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.323078] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.323248] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.323421] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.323596] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.323765] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.323938] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.327851] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.327860] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.327866] vgaarb: loaded
[    0.327869] vgaarb: bridge control possible 0000:00:02.0
[    0.328510] SCSI subsystem initialized
[    0.328651] libata version 3.00 loaded.
[    0.328723] ACPI: bus type USB registered
[    0.328778] usbcore: registered new interface driver usbfs
[    0.328808] usbcore: registered new interface driver hub
[    0.328865] usbcore: registered new device driver usb
[    0.329488] PCI: Using ACPI for IRQ routing
[    0.332264] PCI: pci_cache_line_size set to 64 bytes
[    0.332307] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.332315] e820: reserve RAM buffer [mem 0x0008f000-0x0008ffff]
[    0.332320] e820: reserve RAM buffer [mem 0x74182000-0x77ffffff]
[    0.332324] e820: reserve RAM buffer [mem 0x779a3000-0x77ffffff]
[    0.332328] e820: reserve RAM buffer [mem 0x7b3de000-0x7bffffff]
[    0.332650] NetLabel: Initializing
[    0.332655] NetLabel:  domain hash size = 128
[    0.332658] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.332686] NetLabel:  unlabeled traffic allowed by default
[    0.332891] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.332903] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.334980] clocksource: Switched to clocksource hpet
[    0.351076] AppArmor: AppArmor Filesystem Enabled
[    0.351274] pnp: PnP ACPI init
[    0.351499] system 00:00: [io  0x0680-0x069f] has been reserved
[    0.351506] system 00:00: [io  0x0400-0x047f] has been reserved
[    0.351512] system 00:00: [io  0x0500-0x05fe] has been reserved
[    0.351524] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.356588] system 00:01: [mem 0x9183a000-0x9183afff] has been reserved
[    0.356597] system 00:01: [mem 0x91838000-0x91838fff] has been reserved
[    0.356603] system 00:01: [mem 0x91836000-0x91836fff] has been reserved
[    0.356609] system 00:01: [mem 0x91825000-0x91825fff] has been reserved
[    0.356614] system 00:01: [mem 0x91823000-0x91823fff] has been reserved
[    0.356620] system 00:01: [mem 0x91821000-0x91821fff] has been reserved
[    0.356625] system 00:01: [mem 0x9181f000-0x9181ffff] has been reserved
[    0.356631] system 00:01: [mem 0x9181d000-0x9181dfff] has been reserved
[    0.356637] system 00:01: [mem 0x9181b000-0x9181bfff] has been reserved
[    0.356642] system 00:01: [mem 0x91819000-0x91819fff] has been reserved
[    0.356648] system 00:01: [mem 0x91834000-0x91834fff] has been reserved
[    0.356654] system 00:01: [mem 0x91832000-0x91832fff] has been reserved
[    0.356660] system 00:01: [mem 0x91830000-0x91830fff] has been reserved
[    0.356665] system 00:01: [mem 0x9182e000-0x9182efff] has been reserved
[    0.356671] system 00:01: [mem 0x9182c000-0x9182cfff] has been reserved
[    0.356677] system 00:01: [mem 0x9182a000-0x9182afff] has been reserved
[    0.356683] system 00:01: [mem 0x91828000-0x91828fff] has been reserved
[    0.356688] system 00:01: [mem 0x91826000-0x91826fff] has been reserved
[    0.356697] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.357035] system 00:02: [mem 0xe0000000-0xefffffff] could not be reserved
[    0.357042] system 00:02: [mem 0xfea00000-0xfeafffff] has been reserved
[    0.357049] system 00:02: [mem 0xfed01000-0xfed01fff] has been reserved
[    0.357054] system 00:02: [mem 0xfed03000-0xfed03fff] has been reserved
[    0.357060] system 00:02: [mem 0xfed06000-0xfed06fff] has been reserved
[    0.357065] system 00:02: [mem 0xfed08000-0xfed09fff] has been reserved
[    0.357071] system 00:02: [mem 0xfed80000-0xfedbffff] could not be reserved
[    0.357077] system 00:02: [mem 0xfed1c000-0xfed1cfff] has been reserved
[    0.357082] system 00:02: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.357091] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.357523] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.358416] pnp: PnP ACPI: found 4 devices
[    0.369741] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.369768] pci_bus 0000:00: resource 4 [io  0x0070-0x0077]
[    0.369776] pci_bus 0000:00: resource 5 [io  0x0000-0x006f window]
[    0.369782] pci_bus 0000:00: resource 6 [io  0x0078-0x0cf7 window]
[    0.369787] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff window]
[    0.369792] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff window]
[    0.369797] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff window]
[    0.369802] pci_bus 0000:00: resource 10 [mem 0x000e0000-0x000fffff window]
[    0.369807] pci_bus 0000:00: resource 11 [mem 0x20000000-0x201fffff window]
[    0.369812] pci_bus 0000:00: resource 12 [mem 0x7cc00001-0x7ec00000 window]
[    0.369817] pci_bus 0000:00: resource 13 [mem 0x80000000-0xdfffffff window]
[    0.369904] NET: Registered protocol family 2
[    0.370303] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.370412] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.370521] TCP: Hash tables configured (established 16384 bind 16384)
[    0.370591] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.370621] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.370744] NET: Registered protocol family 1
[    0.370795] pci 0000:00:02.0: Video device with shadowed ROM
[    0.372751] PCI: CLS 64 bytes, default 64
[    0.372898] Trying to unpack rootfs image as initramfs...
[    1.103562] Freeing initrd memory: 20604K (ffff8800357b2000 - ffff880036bd1000)
[    1.104036] Scanning for low memory corruption every 60 seconds
[    1.105144] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    1.105222] audit: initializing netlink subsys (disabled)
[    1.105267] audit: type=2000 audit(1472413105.096:1): initialized
[    1.106131] Initialise system trusted keyring
[    1.106437] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.110893] zbud: loaded
[    1.111431] VFS: Disk quotas dquot_6.6.0
[    1.111533] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.112325] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    1.113057] fuse init (API version 7.23)
[    1.113457] Key type big_key registered
[    1.113502] Allocating IMA MOK and blacklist keyrings.
[    1.114878] Key type asymmetric registered
[    1.114886] Asymmetric key parser 'x509' registered
[    1.115034] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    1.115147] io scheduler noop registered
[    1.115154] io scheduler deadline registered (default)
[    1.115243] io scheduler cfq registered
[    1.115560] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.115581] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.115686] efifb: probing for efifb
[    1.115726] efifb: framebuffer at 0x80000000, mapped to 0xffffc90000800000, using 4032k, total 4032k
[    1.115730] efifb: mode is 1280x800x32, linelength=5120, pages=1
[    1.115733] efifb: scrolling: redraw
[    1.115737] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.116012] Console: switching to colour frame buffer device 160x50
[    1.116060] fb0: EFI VGA frame buffer device
[    1.116088] intel_idle: MWAIT substates: 0x33000020
[    1.116093] intel_idle: v0.4.1 model 0x4C
[    1.116096] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.116822] ACPI: AC Adapter [ADP1] (on-line)
[    1.117019] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.117029] ACPI: Power Button [PWRB]
[    1.117151] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    1.171088] ACPI: Lid Switch [LID]
[    1.171214] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.171223] ACPI: Power Button [PWRF]
[    1.177517] thermal LNXTHERM:00: registered as thermal_zone0
[    1.177525] ACPI: Thermal Zone [TZ00] (0 C)
[    1.177630] GHES: HEST is not enabled!
[    1.178095] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.198533] serial8250: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.208085] Linux agpgart interface v0.103
[    1.234466] brd: module loaded
[    1.245407] loop: module loaded
[    1.246019] libphy: Fixed MDIO Bus: probed
[    1.246028] tun: Universal TUN/TAP device driver, 1.6
[    1.246031] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.246756] PPP generic driver version 2.4.2
[    1.247298] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.247319] ehci-pci: EHCI PCI platform driver
[    1.247352] ehci-platform: EHCI generic platform driver
[    1.247403] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.247416] ohci-pci: OHCI PCI platform driver
[    1.247452] ohci-platform: OHCI generic platform driver
[    1.247484] uhci_hcd: USB Universal Host Controller Interface driver
[    1.247854] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.247872] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    1.249056] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00109810
[    1.249075] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.249298] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.249305] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.249310] usb usb1: Product: xHCI Host Controller
[    1.249314] usb usb1: Manufacturer: Linux 4.4.0-34-generic xhci-hcd
[    1.249318] usb usb1: SerialNumber: 0000:00:14.0
[    1.250465] hub 1-0:1.0: USB hub found
[    1.250504] hub 1-0:1.0: 7 ports detected
[    1.252451] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.252465] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    1.252584] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    1.252591] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.252596] usb usb2: Product: xHCI Host Controller
[    1.252600] usb usb2: Manufacturer: Linux 4.4.0-34-generic xhci-hcd
[    1.252604] usb usb2: SerialNumber: 0000:00:14.0
[    1.253698] hub 2-0:1.0: USB hub found
[    1.253734] hub 2-0:1.0: 6 ports detected
[    1.255593] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.786859] i8042: Can't read CTR while initializing i8042
[    1.786872] i8042: probe of i8042 failed with error -5
[    1.787426] mousedev: PS/2 mouse device common for all mice
[    1.788806] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.788872] rtc_cmos 00:03: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.788896] i2c /dev entries driver
[    1.789091] device-mapper: uevent: version 1.0.3
[    1.789408] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: dm-devel@redhat.com
[    1.789445] Intel P-state driver initializing.
[    1.790375] ledtrig-cpu: registered to indicate activity on CPUs
[    1.790386] EFI Variables Facility v0.08 2004-May-17
[    1.821364] NET: Registered protocol family 10
[    1.823425] NET: Registered protocol family 17
[    1.823455] Key type dns_resolver registered
[    1.825005] microcode: CPU0 sig=0x406c3, pf=0x1, revision=0x35e
[    1.825155] microcode: CPU1 sig=0x406c3, pf=0x1, revision=0x35e
[    1.825431] microcode: CPU2 sig=0x406c3, pf=0x1, revision=0x35e
[    1.825553] microcode: CPU3 sig=0x406c3, pf=0x1, revision=0x35e
[    1.825821] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.826804] registered taskstats version 1
[    1.826830] Loading compiled-in X.509 certificates
[    1.828921] Loaded X.509 cert 'Build time autogenerated kernel key: 7e3faad6ffddb09bc2ef8e9405d93eb823ff40d4'
[    1.828971] zswap: loaded using pool lzo/zbud
[    1.836757] Key type trusted registered
[    1.849974] Key type encrypted registered
[    1.849998] AppArmor: AppArmor sha1 policy hashing enabled
[    1.850006] ima: No TPM chip found, activating TPM-bypass!
[    1.850070] evm: HMAC attrs: 0x1
[    1.850898]   Magic number: 12:713:648
[    1.851111] acpi LNXCPU:01: hash matches
[    1.851494] rtc_cmos 00:03: setting system clock to 2016-08-28 19:38:25 UTC (1472413105)
[    1.851929] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.851933] EDD information not available.
[    1.852370] PM: Hibernation image not present or could not be loaded.
[    1.855439] Freeing unused kernel memory: 1484K (ffffffff81d44000 - ffffffff81eb7000)
[    1.855446] Write protecting the kernel read-only data: 12288k
[    1.856938] Freeing unused kernel memory: 4K (ffff8800027ff000 - ffff880002800000)
[    1.858019] Freeing unused kernel memory: 136K (ffff880002bde000 - ffff880002c00000)
[    1.898192] systemd-udevd[135]: starting version 204
[    1.939231] sdhci: Secure Digital Host Controller Interface driver
[    1.939238] sdhci: Copyright(c) Pierre Ossman
[    1.943707] sdhci-acpi 80860F14:00: No vmmc regulator found
[    1.943715] sdhci-acpi 80860F14:00: No vqmmc regulator found
[    1.948466] mmc0: SDHCI controller on ACPI [80860F14:00] using ADMA
[    1.948881] sdhci-acpi 80860F14:03: failed to setup card detect gpio
[    1.949899] sdhci-acpi 80860F14:03: No vmmc regulator found
[    1.949903] sdhci-acpi 80860F14:03: No vqmmc regulator found
[    1.954066] mmc1: SDHCI controller on ACPI [80860F14:03] using ADMA
[    1.959458] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    2.005807] usb 2-1: new SuperSpeed USB device number 2 using xhci_hcd
[    2.032329] usb 2-1: New USB device found, idVendor=0bda, idProduct=0411
[    2.032337] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.032342] usb 2-1: Product: 4-Port USB 3.0 Hub
[    2.032346] usb 2-1: Manufacturer: Generic
[    2.040823] hub 2-1:1.0: USB hub found
[    2.042158] hub 2-1:1.0: 4 ports detected
[    2.088538] mmc0: MAN_BKOPS_EN bit is not set
[    2.103587] tsc: Refined TSC clocksource calibration: 1439.953 MHz
[    2.103616] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x14c18e756e4, max_idle_ns: 440795259570 ns
[    2.120860] mmc0: new HS200 MMC card at address 0001
[    2.126765] mmcblk0: mmc0:0001 HBG4e\x05 29.1 GiB 
[    2.127094] mmcblk0boot0: mmc0:0001 HBG4e\x05 partition 1 4.00 MiB
[    2.127885] mmcblk0boot1: mmc0:0001 HBG4e\x05 partition 2 4.00 MiB
[    2.128923] mmcblk0rpmb: mmc0:0001 HBG4e\x05 partition 3 4.00 MiB
[    2.133081]  mmcblk0: p1 p2 p3 p4
[    2.191032] usb 1-1: new high-speed USB device number 2 using xhci_hcd
[    2.390554] usb 1-1: New USB device found, idVendor=0bda, idProduct=5411
[    2.390562] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.390566] usb 1-1: Product: 4-Port USB 2.0 Hub
[    2.390570] usb 1-1: Manufacturer: Generic
[    2.392124] hub 1-1:1.0: USB hub found
[    2.393855] hub 1-1:1.0: 4 ports detected
[    2.459841] usb 2-1.1: new SuperSpeed USB device number 3 using xhci_hcd
[    2.478218] usb 2-1.1: New USB device found, idVendor=18a5, idProduct=024b
[    2.478227] usb 2-1.1: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[    2.478232] usb 2-1.1: Product: SSD
[    2.478236] usb 2-1.1: Manufacturer: Verbatim
[    2.478240] usb 2-1.1: SerialNumber: 511140715250C00046
[    2.491233] usbcore: registered new interface driver usb-storage
[    2.500119] scsi host0: uas
[    2.500290] usbcore: registered new interface driver uas
[    2.501434] scsi 0:0:0:0: Direct-Access     Verbatim USB External SSD 0    PQ: 0 ANSI: 6
[    2.502465] sd 0:0:0:0: [sda] 250069680 512-byte logical blocks: (128 GB/119 GiB)
[    2.502555] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.502835] sd 0:0:0:0: [sda] Write Protect is off
[    2.502843] sd 0:0:0:0: [sda] Mode Sense: 43 00 00 00
[    2.503110] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.505824]  sda: sda1 sda2 < sda5 sda6 > sda3 sda4
[    2.605917] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.687983] usb 1-1.3: new full-speed USB device number 3 using xhci_hcd
[    2.809118] usb 1-1.3: New USB device found, idVendor=06cb, idProduct=73f5
[    2.809140] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.809146] usb 1-1.3: Product: ITE Device(8910)
[    2.809151] usb 1-1.3: Manufacturer: ITE Tech. Inc.
[    2.824456] hidraw: raw HID events driver (C) Jiri Kosina
[    2.925087] usbcore: registered new interface driver usbhid
[    2.925093] usbhid: USB HID core driver
[    2.929951] hid-generic 0003:06CB:73F5.0001: ignoring exceeding usage max
[    2.931271] input: ITE Tech. Inc. ITE Device(8910) as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1.3/1-1.3:1.0/0003:06CB:73F5.0001/input/input3
[    2.990431] hid-generic 0003:06CB:73F5.0001: input,hiddev0,hidraw0: USB HID v1.10 Keyboard [ITE Tech. Inc. ITE Device(8910)] on usb-0000:00:14.0-1.3/input0
[    3.104599] clocksource: Switched to clocksource tsc
[    7.692868] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.832211] random: init urandom read with 73 bits of entropy available
[    7.894180] init: plymouth-upstart-bridge main process (208) terminated with status 1
[    7.894217] init: plymouth-upstart-bridge main process ended, respawning
[    7.912637] init: plymouth-upstart-bridge main process (218) terminated with status 1
[    7.912667] init: plymouth-upstart-bridge main process ended, respawning
[    7.927327] init: plymouth-upstart-bridge main process (221) terminated with status 1
[    7.927365] init: plymouth-upstart-bridge main process ended, respawning
[    8.372189] random: nonblocking pool is initialized
[    8.983387] systemd-udevd[339]: starting version 204
[    9.128323] lp: driver loaded but no devices found
[    9.150097] ppdev: user-space parallel port driver
[    9.166676] wmi: Mapper loaded
[    9.206182] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.279785] [drm] Initialized drm 1.1.0 20060810
[    9.330103] 8086228A:00: ttyS4 at MMIO 0x91822000 (irq = 39, base_baud = 2764800) is a 16550A
[    9.330680] 8086228A:01: ttyS5 at MMIO 0x91820000 (irq = 40, base_baud = 2764800) is a 16550A
[    9.404646] Bluetooth: Core ver 2.21
[    9.404740] NET: Registered protocol family 31
[    9.404745] Bluetooth: HCI device and connection manager initialized
[    9.404754] Bluetooth: HCI socket layer initialized
[    9.404761] Bluetooth: L2CAP socket layer initialized
[    9.404775] Bluetooth: SCO socket layer initialized
[    9.434877] Bluetooth: HCI UART driver ver 2.3
[    9.434885] Bluetooth: HCI UART protocol H4 registered
[    9.434888] Bluetooth: HCI UART protocol BCSP registered
[    9.434891] Bluetooth: HCI UART protocol LL registered
[    9.434894] Bluetooth: HCI UART protocol ATH3K registered
[    9.434896] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    9.435092] Bluetooth: HCI UART protocol Intel registered
[    9.435141] Bluetooth: HCI UART protocol BCM registered
[    9.435145] Bluetooth: HCI UART protocol QCA registered
[    9.455015] [drm] Memory usable by graphics device = 2048M
[    9.455075] checking generic (80000000 3f0000) vs hw (80000000 10000000)
[    9.455080] fb: switching to inteldrmfb from EFI VGA
[    9.455142] Console: switching to colour dummy device 80x25
[    9.455548] [drm] Replacing VGA console driver
[    9.457984] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    9.457991] [drm] Driver supports precise vblank timestamp query.
[    9.458085] [drm:intel_parse_bios [i915]] *ERROR* Unable to parse MIPI Sequence Block v3+
[    9.582036] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.585643] [drm:pwm_setup_backlight [i915]] *ERROR* Failed to own the pwm chip
[    9.594957] ------------[ cut here ]------------
[    9.595046] WARNING: CPU: 1 PID: 357 at /build/linux-lts-xenial-Hu9lgy/linux-lts-xenial-4.4.0/drivers/gpu/drm/i915/intel_display.c:690 chv_calc_dpll_params+0x97/0xb0 [i915]()
[    9.595050] WARN_ON(clock->n == 0 || clock->p == 0)
[    9.595053] Modules linked in: snd_intel_sst_acpi(+) snd_intel_sst_core snd_soc_sst_mfld_platform snd_soc_core mei_txe(+) lpc_ich(+) snd_compress mei ac97_bus snd_pcm_dmaengine snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi 8250_fintek snd_seq hci_uart snd_seq_device snd_timer btbcm btqca btintel dw_dmac(+) intel_hid sparse_keymap dw_dmac_core bluetooth i915(+) i2c_designware_platform(+) i2c_designware_core snd nls_iso8859_1 soundcore 8250_dw pwm_lpss_platform pwm_lpss spi_pxa2xx_platform video tpm_crb drm_kms_helper drm int3400_thermal acpi_thermal_rel soc_button_array i2c_algo_bit fb_sys_fops syscopyarea int3403_thermal sysfillrect acpi_pad pinctrl_cherryview sysimgblt parport_pc wmi processor_thermal_device mac_hid ppdev int340x_thermal_zone intel_soc_dts_iosf lp parport hid_generic usbhid hid uas usb_storage mmc_block fjes sdhci_acpi sdhci
[    9.595153] CPU: 1 PID: 357 Comm: systemd-udevd Not tainted 4.4.0-34-generic #53~14.04.1-Ubuntu
[    9.595157] Hardware name: Acer Aspire SW3-016/Gummi CHT, BIOS V1.12 12/25/2015
[    9.595160]  0000000000000000 ffff880075b5f6c8 ffffffff813d438c ffff880075b5f710
[    9.595166]  ffffffffc02f1fe8 ffff880075b5f700 ffffffff8107d776 ffff880072e51400
[    9.595172]  0000000000000000 ffff880072180000 0000000000000000 0000000000000000
[    9.595177] Call Trace:
[    9.595189]  [<ffffffff813d438c>] dump_stack+0x63/0x87
[    9.595197]  [<ffffffff8107d776>] warn_slowpath_common+0x86/0xc0
[    9.595201]  [<ffffffff8107d7fc>] warn_slowpath_fmt+0x4c/0x50
[    9.595263]  [<ffffffffc0286657>] chv_calc_dpll_params+0x97/0xb0 [i915]
[    9.595323]  [<ffffffffc0286e5c>] i9xx_get_pipe_config+0x61c/0x660 [i915]
[    9.595385]  [<ffffffffc02c62d1>] ? pwm_setup_backlight+0xe1/0x100 [i915]
[    9.595447]  [<ffffffffc02940d7>] intel_modeset_setup_hw_state+0xa7/0xe90 [i915]
[    9.595508]  [<ffffffffc0296984>] intel_modeset_init+0x8d4/0x1280 [i915]
[    9.595570]  [<ffffffffc02ce70e>] i915_driver_load+0x7ee/0xef0 [i915]
[    9.595577]  [<ffffffff8102c666>] ? __switch_to+0x1d6/0x570
[    9.595584]  [<ffffffff817f34c9>] ? __schedule+0x359/0x980
[    9.595591]  [<ffffffff81526bb7>] ? get_device+0x17/0x20
[    9.595597]  [<ffffffff8152c7f5>] ? klist_class_dev_get+0x15/0x20
[    9.595603]  [<ffffffff817eae68>] ? klist_node_init+0x38/0x50
[    9.595607]  [<ffffffff817eaef0>] ? klist_add_tail+0x20/0x50
[    9.595611]  [<ffffffff81528680>] ? device_add+0x270/0x610
[    9.595649]  [<ffffffffc01351b7>] drm_dev_register+0xa7/0xb0 [drm]
[    9.595676]  [<ffffffffc013766f>] drm_get_pci_dev+0x8f/0x1f0 [drm]
[    9.595729]  [<ffffffffc02141e4>] i915_pci_probe+0x34/0x50 [i915]
[    9.595734]  [<ffffffff81422b25>] local_pci_probe+0x45/0xa0
[    9.595739]  [<ffffffff81423fd1>] pci_device_probe+0xe1/0x130
[    9.595745]  [<ffffffff8152b83b>] driver_probe_device+0x21b/0x470
[    9.595749]  [<ffffffff8152bb15>] __driver_attach+0x85/0x90
[    9.595754]  [<ffffffff8152ba90>] ? driver_probe_device+0x470/0x470
[    9.595758]  [<ffffffff815296dd>] bus_for_each_dev+0x5d/0x90
[    9.595763]  [<ffffffff8152b1ce>] driver_attach+0x1e/0x20
[    9.595767]  [<ffffffff8152ad30>] bus_add_driver+0x1d0/0x290
[    9.595772]  [<ffffffff8152c510>] driver_register+0x60/0xe0
[    9.595777]  [<ffffffff814224dc>] __pci_register_driver+0x4c/0x50
[    9.595804]  [<ffffffffc01378b0>] drm_pci_init+0xe0/0x110 [drm]
[    9.595808]  [<ffffffffc033c000>] ? 0xffffffffc033c000
[    9.595861]  [<ffffffffc033c094>] i915_init+0x94/0x9b [i915]
[    9.595867]  [<ffffffff8100213d>] do_one_initcall+0xcd/0x1f0
[    9.595873]  [<ffffffff811c0af6>] ? __vunmap+0xa6/0xf0
[    9.595879]  [<ffffffff811dbf3d>] ? kmem_cache_alloc_trace+0x1ad/0x220
[    9.595886]  [<ffffffff81180f87>] ? do_init_module+0x27/0x1d2
[    9.595890]  [<ffffffff81180fc0>] do_init_module+0x60/0x1d2
[    9.595896]  [<ffffffff8110224c>] load_module+0x141c/0x1b00
[    9.595901]  [<ffffffff810fea40>] ? __symbol_put+0x40/0x40
[    9.595907]  [<ffffffff81203571>] ? kernel_read+0x41/0x60
[    9.595912]  [<ffffffff81102afe>] SYSC_finit_module+0x7e/0xa0
[    9.595918]  [<ffffffff81102b3e>] SyS_finit_module+0xe/0x10
[    9.595923]  [<ffffffff817f7376>] entry_SYSCALL_64_fastpath+0x16/0x75
[    9.595934] ---[ end trace 52c1a5962c25f863 ]---
[    9.671533] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.671540] Bluetooth: BNEP filters: protocol multicast
[    9.671550] Bluetooth: BNEP socket layer initialized
[    9.677309] input: ITE Tech. Inc. ITE Device(8910) Touchpad as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1.3/1-1.3:1.1/0003:06CB:73F5.0002/input/input4
[    9.678017] hid-multitouch 0003:06CB:73F5.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [ITE Tech. Inc. ITE Device(8910)] on usb-0000:00:14.0-1.3/input1
[    9.678698] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.684477] acpi device:29: registered as cooling_device4
[    9.685901] acpi device:2a: registered as cooling_device5
[    9.692401] acpi device:2b: registered as cooling_device6
[    9.699428] acpi device:2c: registered as cooling_device7
[    9.703913] acpi device:2d: registered as cooling_device8
[    9.705054] acpi device:2e: registered as cooling_device9
[    9.708814] acpi device:2f: registered as cooling_device10
[    9.710188] Bluetooth: RFCOMM TTY layer initialized
[    9.710206] Bluetooth: RFCOMM socket layer initialized
[    9.710222] Bluetooth: RFCOMM ver 1.11
[    9.712214] acpi device:30: registered as cooling_device11
[    9.713730] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    9.714479] [drm] Initialized i915 1.6.0 20151010 for 0000:00:02.0 on minor 0
[    9.715453] dw_dmac INTL9C60:00: DesignWare DMA Controller, 8 channels
[    9.716732] dw_dmac INTL9C60:01: DesignWare DMA Controller, 8 channels
[    9.791052] audit: type=1400 audit(1472413113.438:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=535 comm="apparmor_parser"
[    9.791067] audit: type=1400 audit(1472413113.438:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=535 comm="apparmor_parser"
[    9.792883] audit: type=1400 audit(1472413113.438:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=535 comm="apparmor_parser"
[    9.813288] intel_sst_acpi 808622A8:00: No matching machine driver found
[    9.843235] fbcon: inteldrmfb (fb0) is primary device
[    9.843421] Console: switching to colour frame buffer device 160x50
[    9.843477] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    9.980231] i2c_designware 808622C1:06: I2C bus managed by PUNIT
[   10.078988] i2c_designware 808622C1:06: punit semaphore timed out, resetting
[   10.079009] i2c_designware 808622C1:06: PUNIT SEM: 2
[   10.079013] ------------[ cut here ]------------
[   10.079027] WARNING: CPU: 1 PID: 384 at /build/linux-lts-xenial-Hu9lgy/linux-lts-xenial-4.4.0/drivers/i2c/busses/i2c-designware-baytrail.c:112 baytrail_i2c_acquire+0x128/0x1d0 [i2c_designware_platform]()
[   10.079030] Modules linked in: rfcomm bnep joydev hid_multitouch input_leds snd_intel_sst_acpi snd_intel_sst_core snd_soc_sst_mfld_platform snd_soc_core mei_txe lpc_ich snd_compress mei ac97_bus snd_pcm_dmaengine snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi 8250_fintek snd_seq hci_uart snd_seq_device snd_timer btbcm btqca btintel dw_dmac intel_hid sparse_keymap dw_dmac_core bluetooth i915 i2c_designware_platform(+) i2c_designware_core snd nls_iso8859_1 soundcore 8250_dw pwm_lpss_platform pwm_lpss spi_pxa2xx_platform video tpm_crb drm_kms_helper drm int3400_thermal acpi_thermal_rel soc_button_array i2c_algo_bit fb_sys_fops syscopyarea int3403_thermal sysfillrect acpi_pad pinctrl_cherryview sysimgblt parport_pc wmi processor_thermal_device mac_hid ppdev int340x_thermal_zone intel_soc_dts_iosf lp parport hid_generic usbhid hid uas usb_storage mmc_block fjes sdhci_acpi sdhci
[   10.079124] CPU: 1 PID: 384 Comm: systemd-udevd Tainted: G        W       4.4.0-34-generic #53~14.04.1-Ubuntu
[   10.079127] Hardware name: Acer Aspire SW3-016/Gummi CHT, BIOS V1.12 12/25/2015
[   10.079131]  0000000000000000 ffff88007512fa60 ffffffff813d438c 0000000000000000
[   10.079137]  ffffffffc01a3708 ffff88007512fa98 ffffffff8107d776 ffff880072ec7018
[   10.079143]  00000000fffee4df 00000000fffee4c6 ffff88007ad20810 0000000000000000
[   10.079148] Call Trace:
[   10.079160]  [<ffffffff813d438c>] dump_stack+0x63/0x87
[   10.079167]  [<ffffffff8107d776>] warn_slowpath_common+0x86/0xc0
[   10.079172]  [<ffffffff8107d86a>] warn_slowpath_null+0x1a/0x20
[   10.079178]  [<ffffffffc01a28a8>] baytrail_i2c_acquire+0x128/0x1d0 [i2c_designware_platform]
[   10.079185]  [<ffffffffc01e9223>] i2c_dw_init+0x23/0x360 [i2c_designware_core]
[   10.079191]  [<ffffffffc01e95b2>] i2c_dw_probe+0x52/0x170 [i2c_designware_core]
[   10.079197]  [<ffffffffc01a246c>] dw_i2c_plat_probe+0x1bc/0x3d0 [i2c_designware_platform]
[   10.079205]  [<ffffffff8152da6b>] platform_drv_probe+0x3b/0xa0
[   10.079210]  [<ffffffff8152b83b>] driver_probe_device+0x21b/0x470
[   10.079215]  [<ffffffff8152bb15>] __driver_attach+0x85/0x90
[   10.079220]  [<ffffffff8152ba90>] ? driver_probe_device+0x470/0x470
[   10.079224]  [<ffffffff815296dd>] bus_for_each_dev+0x5d/0x90
[   10.079229]  [<ffffffff8152b1ce>] driver_attach+0x1e/0x20
[   10.079233]  [<ffffffff8152ad30>] bus_add_driver+0x1d0/0x290
[   10.079238]  [<ffffffffc01ef000>] ? 0xffffffffc01ef000
[   10.079242]  [<ffffffff8152c510>] driver_register+0x60/0xe0
[   10.079247]  [<ffffffff8152d9a6>] __platform_driver_register+0x36/0x40
[   10.079253]  [<ffffffffc01ef017>] dw_i2c_init_driver+0x17/0x1000 [i2c_designware_platform]
[   10.079259]  [<ffffffff8100213d>] do_one_initcall+0xcd/0x1f0
[   10.079266]  [<ffffffff811dbf3d>] ? kmem_cache_alloc_trace+0x1ad/0x220
[   10.079272]  [<ffffffff81180f87>] ? do_init_module+0x27/0x1d2
[   10.079277]  [<ffffffff81180fc0>] do_init_module+0x60/0x1d2
[   10.079282]  [<ffffffff8110224c>] load_module+0x141c/0x1b00
[   10.079287]  [<ffffffff810fea40>] ? __symbol_put+0x40/0x40
[   10.079293]  [<ffffffff81203571>] ? kernel_read+0x41/0x60
[   10.079299]  [<ffffffff81102afe>] SYSC_finit_module+0x7e/0xa0
[   10.079304]  [<ffffffff81102b3e>] SyS_finit_module+0xe/0x10
[   10.079311]  [<ffffffff817f7376>] entry_SYSCALL_64_fastpath+0x16/0x75
[   10.079315] ---[ end trace 52c1a5962c25f864 ]---
[   10.079319] i2c_designware 808622C1:06: couldn't acquire bus ownership
[   10.079356] i2c_designware: probe of 808622C1:06 failed with error -110
[   10.120824] nfc: nfc_init: NFC Core ver 0.1
[   10.121305] SSE version of gcm_enc/dec engaged.
[   10.126450] NET: Registered protocol family 39
[   10.213215] input: ELAN1001:00 04F3:20E9 as /devices/pci0000:00/808622C1:05/i2c-12/i2c-ELAN1001:00/0018:04F3:20E9.0003/input/input7
[   10.213721] hid-multitouch 0018:04F3:20E9.0003: input,hidraw2: I2C HID v1.00 Device [ELAN1001:00 04F3:20E9] on i2c-ELAN1001:00
[   10.274005] audit: type=1400 audit(1472413113.918:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=612 comm="apparmor_parser"
[   10.274022] audit: type=1400 audit(1472413113.918:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=612 comm="apparmor_parser"
[   10.274033] audit: type=1400 audit(1472413113.918:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=612 comm="apparmor_parser"
[   10.275470] audit: type=1400 audit(1472413113.922:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=612 comm="apparmor_parser"
[   10.275487] audit: type=1400 audit(1472413113.922:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=612 comm="apparmor_parser"
[   10.276239] audit: type=1400 audit(1472413113.922:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=612 comm="apparmor_parser"
[   10.305635] acer_wmi: Acer Laptop ACPI-WMI Extras
[   10.305751] acer_wmi: Function bitmap for Communication Button: 0x801
[   10.411312] intel_rapl: Found RAPL domain package
[   10.411320] intel_rapl: Found RAPL domain core
[   10.423087] acer_wmi: Enabling Launch Manager failed: 0xe4 - 0x0
[   10.436622] input: Acer WMI hotkeys as /devices/virtual/input/input9
[   10.439219] input: Acer BMA150 accelerometer as /devices/virtual/input/input10
[   10.611216] init: failsafe main process (639) killed by TERM signal
[   10.703368] audit: type=1400 audit(1472413114.350:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=733 comm="apparmor_parser"
[   10.994358] ------------[ cut here ]------------
[   10.994445] WARNING: CPU: 0 PID: 4 at /build/linux-lts-xenial-Hu9lgy/linux-lts-xenial-4.4.0/drivers/gpu/drm/i915/intel_sideband.c:200 vlv_dpio_read+0x6e/0x80 [i915]()
[   10.994449] DPIO read pipe A reg 0x8134 == 0xffffffff
[   10.994452] Modules linked in: intel_rapl intel_powerclamp coretemp acer_wmi kvm_intel kvm irqbypass punit_atom_debug crct10dif_pclmul crc32_pclmul fdp_i2c fdp i2c_hid nci snd_soc_rt5640 aesni_intel nfc snd_soc_rl6231 aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd rfcomm bnep joydev hid_multitouch input_leds snd_intel_sst_acpi snd_intel_sst_core snd_soc_sst_mfld_platform snd_soc_core mei_txe lpc_ich snd_compress mei ac97_bus snd_pcm_dmaengine snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi 8250_fintek snd_seq hci_uart snd_seq_device snd_timer btbcm btqca btintel dw_dmac intel_hid sparse_keymap dw_dmac_core bluetooth i915 i2c_designware_platform i2c_designware_core snd nls_iso8859_1 soundcore 8250_dw pwm_lpss_platform pwm_lpss spi_pxa2xx_platform video tpm_crb drm_kms_helper drm int3400_thermal acpi_thermal_rel soc_button_array i2c_algo_bit fb_sys_fops syscopyarea int3403_thermal sysfillrect acpi_pad pinctrl_cherryview sysimgblt parport_pc wmi processor_thermal_device mac_hid ppdev int340x_thermal_zone intel_soc_dts_iosf lp parport hid_generic usbhid hid uas usb_storage mmc_block fjes sdhci_acpi sdhci
[   10.994582] CPU: 0 PID: 4 Comm: kworker/0:0 Tainted: G        W       4.4.0-34-generic #53~14.04.1-Ubuntu
[   10.994586] Hardware name: Acer Aspire SW3-016/Gummi CHT, BIOS V1.12 12/25/2015
[   10.994606] Workqueue: events output_poll_execute [drm_kms_helper]
[   10.994611]  0000000000000000 ffff880073933aa8 ffffffff813d438c ffff880073933af0
[   10.994617]  ffffffffc02f6b90 ffff880073933ae0 ffffffff8107d776 0000000000008134
[   10.994622]  0000000000000000 ffff880072180000 0000000000008004 0000000000008000
[   10.994628] Call Trace:
[   10.994640]  [<ffffffff813d438c>] dump_stack+0x63/0x87
[   10.994649]  [<ffffffff8107d776>] warn_slowpath_common+0x86/0xc0
[   10.994653]  [<ffffffff8107d7fc>] warn_slowpath_fmt+0x4c/0x50
[   10.994714]  [<ffffffffc029ed7e>] vlv_dpio_read+0x6e/0x80 [i915]
[   10.994763]  [<ffffffffc0286da2>] i9xx_get_pipe_config+0x562/0x660 [i915]
[   10.994802]  [<ffffffffc013e2bd>] ? drm_property_unreference_blob+0xad/0xb0 [drm]
[   10.994851]  [<ffffffffc0282dff>] intel_modeset_check_state+0x2cf/0x8e0 [i915]
[   10.994901]  [<ffffffffc028e8b7>] intel_atomic_commit+0x5d7/0x640 [i915]
[   10.994936]  [<ffffffffc014c467>] drm_atomic_commit+0x37/0x60 [drm]
[   10.994955]  [<ffffffffc01b435d>] restore_fbdev_mode+0x22d/0x260 [drm_kms_helper]
[   10.994987]  [<ffffffffc014aca7>] ? drm_modeset_lock_all_ctx+0x97/0xb0 [drm]
[   10.995003]  [<ffffffffc01b6403>] drm_fb_helper_restore_fbdev_mode_unlocked+0x33/0x80 [drm_kms_helper]
[   10.995018]  [<ffffffffc01b647c>] drm_fb_helper_set_par+0x2c/0x50 [drm_kms_helper]
[   10.995034]  [<ffffffffc01b6382>] drm_fb_helper_hotplug_event+0xa2/0xf0 [drm_kms_helper]
[   10.995088]  [<ffffffffc02a428e>] intel_fbdev_output_poll_changed+0x1e/0x30 [i915]
[   10.995101]  [<ffffffffc01a95d7>] drm_kms_helper_hotplug_event+0x27/0x30 [drm_kms_helper]
[   10.995115]  [<ffffffffc01a96ad>] output_poll_execute+0x6d/0x1d0 [drm_kms_helper]
[   10.995122]  [<ffffffff81095970>] process_one_work+0x150/0x3f0
[   10.995128]  [<ffffffff810960ea>] worker_thread+0x11a/0x470
[   10.995133]  [<ffffffff81095fd0>] ? rescuer_thread+0x310/0x310
[   10.995138]  [<ffffffff8109b849>] kthread+0xc9/0xe0
[   10.995142]  [<ffffffff8109b780>] ? kthread_park+0x60/0x60
[   10.995149]  [<ffffffff817f770f>] ret_from_fork+0x3f/0x70
[   10.995154]  [<ffffffff8109b780>] ? kthread_park+0x60/0x60
[   10.995202] ---[ end trace 52c1a5962c25f865 ]---
[   10.997257] ------------[ cut here ]------------
[   10.997351] WARNING: CPU: 0 PID: 4 at /build/linux-lts-xenial-Hu9lgy/linux-lts-xenial-4.4.0/drivers/gpu/drm/i915/intel_sideband.c:200 vlv_dpio_read+0x6e/0x80 [i915]()
[   10.997355] DPIO read pipe A reg 0x8000 == 0xffffffff
[   10.997358] Modules linked in: intel_rapl intel_powerclamp coretemp acer_wmi kvm_intel kvm irqbypass punit_atom_debug crct10dif_pclmul crc32_pclmul fdp_i2c fdp i2c_hid nci snd_soc_rt5640 aesni_intel nfc snd_soc_rl6231 aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd rfcomm bnep joydev hid_multitouch input_leds snd_intel_sst_acpi snd_intel_sst_core snd_soc_sst_mfld_platform snd_soc_core mei_txe lpc_ich snd_compress mei ac97_bus snd_pcm_dmaengine snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi 8250_fintek snd_seq hci_uart snd_seq_device snd_timer btbcm btqca btintel dw_dmac intel_hid sparse_keymap dw_dmac_core bluetooth i915 i2c_designware_platform i2c_designware_core snd nls_iso8859_1 soundcore 8250_dw pwm_lpss_platform pwm_lpss spi_pxa2xx_platform video tpm_crb drm_kms_helper drm int3400_thermal acpi_thermal_rel soc_button_array i2c_algo_bit fb_sys_fops syscopyarea int3403_thermal sysfillrect acpi_pad pinctrl_cherryview sysimgblt parport_pc wmi processor_thermal_device mac_hid ppdev int340x_thermal_zone intel_soc_dts_iosf lp parport hid_generic usbhid hid uas usb_storage mmc_block fjes sdhci_acpi sdhci
[   10.997488] CPU: 0 PID: 4 Comm: kworker/0:0 Tainted: G        W       4.4.0-34-generic #53~14.04.1-Ubuntu
[   10.997491] Hardware name: Acer Aspire SW3-016/Gummi CHT, BIOS V1.12 12/25/2015
[   10.997514] Workqueue: events output_poll_execute [drm_kms_helper]
[   10.997518]  0000000000000000 ffff880073933aa8 ffffffff813d438c ffff880073933af0
[   10.997524]  ffffffffc02f6b90 ffff880073933ae0 ffffffff8107d776 0000000000008000
[   10.997529]  0000000000000000 ffff880072180000 0000000000008004 0000000000008000
[   10.997535] Call Trace:
[   10.997549]  [<ffffffff813d438c>] dump_stack+0x63/0x87
[   10.997557]  [<ffffffff8107d776>] warn_slowpath_common+0x86/0xc0
[   10.997562]  [<ffffffff8107d7fc>] warn_slowpath_fmt+0x4c/0x50
[   10.997611]  [<ffffffffc029ed7e>] vlv_dpio_read+0x6e/0x80 [i915]
[   10.997659]  [<ffffffffc0286db3>] i9xx_get_pipe_config+0x573/0x660 [i915]
[   10.997701]  [<ffffffffc013e2bd>] ? drm_property_unreference_blob+0xad/0xb0 [drm]
[   10.997750]  [<ffffffffc0282dff>] intel_modeset_check_state+0x2cf/0x8e0 [i915]
[   10.997799]  [<ffffffffc028e8b7>] intel_atomic_commit+0x5d7/0x640 [i915]
[   10.997830]  [<ffffffffc014c467>] drm_atomic_commit+0x37/0x60 [drm]
[   10.997846]  [<ffffffffc01b435d>] restore_fbdev_mode+0x22d/0x260 [drm_kms_helper]
[   10.997877]  [<ffffffffc014aca7>] ? drm_modeset_lock_all_ctx+0x97/0xb0 [drm]
[   10.997893]  [<ffffffffc01b6403>] drm_fb_helper_restore_fbdev_mode_unlocked+0x33/0x80 [drm_kms_helper]
[   10.997908]  [<ffffffffc01b647c>] drm_fb_helper_set_par+0x2c/0x50 [drm_kms_helper]
[   10.997924]  [<ffffffffc01b6382>] drm_fb_helper_hotplug_event+0xa2/0xf0 [drm_kms_helper]
[   10.997972]  [<ffffffffc02a428e>] intel_fbdev_output_poll_changed+0x1e/0x30 [i915]
[   10.997985]  [<ffffffffc01a95d7>] drm_kms_helper_hotplug_event+0x27/0x30 [drm_kms_helper]
[   10.997999]  [<ffffffffc01a96ad>] output_poll_execute+0x6d/0x1d0 [drm_kms_helper]
[   10.998006]  [<ffffffff81095970>] process_one_work+0x150/0x3f0
[   10.998011]  [<ffffffff810960ea>] worker_thread+0x11a/0x470
[   10.998016]  [<ffffffff81095fd0>] ? rescuer_thread+0x310/0x310
[   10.998021]  [<ffffffff8109b849>] kthread+0xc9/0xe0
[   10.998026]  [<ffffffff8109b780>] ? kthread_park+0x60/0x60
[   10.998035]  [<ffffffff817f770f>] ret_from_fork+0x3f/0x70
[   10.998039]  [<ffffffff8109b780>] ? kthread_park+0x60/0x60
[   10.998043] ---[ end trace 52c1a5962c25f866 ]---
[   11.003776] ------------[ cut here ]------------
[   11.003853] WARNING: CPU: 0 PID: 4 at /build/linux-lts-xenial-Hu9lgy/linux-lts-xenial-4.4.0/drivers/gpu/drm/i915/intel_sideband.c:200 vlv_dpio_read+0x6e/0x80 [i915]()
[   11.003857] DPIO read pipe A reg 0x8004 == 0xffffffff
[   11.003860] Modules linked in: intel_rapl intel_powerclamp coretemp acer_wmi kvm_intel kvm irqbypass punit_atom_debug crct10dif_pclmul crc32_pclmul fdp_i2c fdp i2c_hid nci snd_soc_rt5640 aesni_intel nfc snd_soc_rl6231 aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd rfcomm bnep joydev hid_multitouch input_leds snd_intel_sst_acpi snd_intel_sst_core snd_soc_sst_mfld_platform snd_soc_core mei_txe lpc_ich snd_compress mei ac97_bus snd_pcm_dmaengine snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi 8250_fintek snd_seq hci_uart snd_seq_device snd_timer btbcm btqca btintel dw_dmac intel_hid sparse_keymap dw_dmac_core bluetooth i915 i2c_designware_platform i2c_designware_core snd nls_iso8859_1 soundcore 8250_dw pwm_lpss_platform pwm_lpss spi_pxa2xx_platform video tpm_crb drm_kms_helper drm int3400_thermal acpi_thermal_rel soc_button_array i2c_algo_bit fb_sys_fops syscopyarea int3403_thermal sysfillrect acpi_pad pinctrl_cherryview sysimgblt parport_pc wmi processor_thermal_device mac_hid ppdev int340x_thermal_zone intel_soc_dts_iosf lp parport hid_generic usbhid hid uas usb_storage mmc_block fjes sdhci_acpi sdhci
[   11.003990] CPU: 0 PID: 4 Comm: kworker/0:0 Tainted: G        W       4.4.0-34-generic #53~14.04.1-Ubuntu
[   11.003993] Hardware name: Acer Aspire SW3-016/Gummi CHT, BIOS V1.12 12/25/2015
[   11.004013] Workqueue: events output_poll_execute [drm_kms_helper]
[   11.004017]  0000000000000000 ffff880073933aa8 ffffffff813d438c ffff880073933af0
[   11.004023]  ffffffffc02f6b90 ffff880073933ae0 ffffffff8107d776 0000000000008004
[   11.004029]  0000000000000000 ffff880072180000 0000000000008004 00000000ffffffff
[   11.004035] Call Trace:
[   11.004047]  [<ffffffff813d438c>] dump_stack+0x63/0x87
[   11.004056]  [<ffffffff8107d776>] warn_slowpath_common+0x86/0xc0
[   11.004061]  [<ffffffff8107d7fc>] warn_slowpath_fmt+0x4c/0x50
[   11.004110]  [<ffffffffc029ed7e>] vlv_dpio_read+0x6e/0x80 [i915]
[   11.004158]  [<ffffffffc0286dc4>] i9xx_get_pipe_config+0x584/0x660 [i915]
[   11.004198]  [<ffffffffc013e2bd>] ? drm_property_unreference_blob+0xad/0xb0 [drm]
[   11.004247]  [<ffffffffc0282dff>] intel_modeset_check_state+0x2cf/0x8e0 [i915]
[   11.004295]  [<ffffffffc028e8b7>] intel_atomic_commit+0x5d7/0x640 [i915]
[   11.004327]  [<ffffffffc014c467>] drm_atomic_commit+0x37/0x60 [drm]
[   11.004342]  [<ffffffffc01b435d>] restore_fbdev_mode+0x22d/0x260 [drm_kms_helper]
[   11.004373]  [<ffffffffc014aca7>] ? drm_modeset_lock_all_ctx+0x97/0xb0 [drm]
[   11.004389]  [<ffffffffc01b6403>] drm_fb_helper_restore_fbdev_mode_unlocked+0x33/0x80 [drm_kms_helper]
[   11.004404]  [<ffffffffc01b647c>] drm_fb_helper_set_par+0x2c/0x50 [drm_kms_helper]
[   11.004419]  [<ffffffffc01b6382>] drm_fb_helper_hotplug_event+0xa2/0xf0 [drm_kms_helper]
[   11.004467]  [<ffffffffc02a428e>] intel_fbdev_output_poll_changed+0x1e/0x30 [i915]
[   11.004481]  [<ffffffffc01a95d7>] drm_kms_helper_hotplug_event+0x27/0x30 [drm_kms_helper]
[   11.004494]  [<ffffffffc01a96ad>] output_poll_execute+0x6d/0x1d0 [drm_kms_helper]
[   11.004501]  [<ffffffff81095970>] process_one_work+0x150/0x3f0
[   11.004506]  [<ffffffff810960ea>] worker_thread+0x11a/0x470
[   11.004511]  [<ffffffff81095fd0>] ? rescuer_thread+0x310/0x310
[   11.004516]  [<ffffffff8109b849>] kthread+0xc9/0xe0
[   11.004521]  [<ffffffff8109b780>] ? kthread_park+0x60/0x60
[   11.004529]  [<ffffffff817f770f>] ret_from_fork+0x3f/0x70
[   11.004533]  [<ffffffff8109b780>] ? kthread_park+0x60/0x60
[   11.004586] ---[ end trace 52c1a5962c25f867 ]---
[   11.006623] ------------[ cut here ]------------
[   11.006705] WARNING: CPU: 0 PID: 4 at /build/linux-lts-xenial-Hu9lgy/linux-lts-xenial-4.4.0/drivers/gpu/drm/i915/intel_sideband.c:200 vlv_dpio_read+0x6e/0x80 [i915]()
[   11.006709] DPIO read pipe A reg 0x8008 == 0xffffffff
[   11.006712] Modules linked in: intel_rapl intel_powerclamp coretemp acer_wmi kvm_intel kvm irqbypass punit_atom_debug crct10dif_pclmul crc32_pclmul fdp_i2c fdp i2c_hid nci snd_soc_rt5640 aesni_intel nfc snd_soc_rl6231 aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd rfcomm bnep joydev hid_multitouch input_leds snd_intel_sst_acpi snd_intel_sst_core snd_soc_sst_mfld_platform snd_soc_core mei_txe lpc_ich snd_compress mei ac97_bus snd_pcm_dmaengine snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi 8250_fintek snd_seq hci_uart snd_seq_device snd_timer btbcm btqca btintel dw_dmac intel_hid sparse_keymap dw_dmac_core bluetooth i915 i2c_designware_platform i2c_designware_core snd nls_iso8859_1 soundcore 8250_dw pwm_lpss_platform pwm_lpss spi_pxa2xx_platform video tpm_crb drm_kms_helper drm int3400_thermal acpi_thermal_rel soc_button_array i2c_algo_bit fb_sys_fops syscopyarea int3403_thermal sysfillrect acpi_pad pinctrl_cherryview sysimgblt parport_pc wmi processor_thermal_device mac_hid ppdev int340x_thermal_zone intel_soc_dts_iosf lp parport hid_generic usbhid hid uas usb_storage mmc_block fjes sdhci_acpi sdhci
[   11.006844] CPU: 0 PID: 4 Comm: kworker/0:0 Tainted: G        W       4.4.0-34-generic #53~14.04.1-Ubuntu
[   11.006847] Hardware name: Acer Aspire SW3-016/Gummi CHT, BIOS V1.12 12/25/2015
[   11.006869] Workqueue: events output_poll_execute [drm_kms_helper]
[   11.006873]  0000000000000000 ffff880073933aa8 ffffffff813d438c ffff880073933af0
[   11.006879]  ffffffffc02f6b90 ffff880073933ae0 ffffffff8107d776 0000000000008008
[   11.006885]  0000000000000000 ffff880072180000 0000000000008004 00000000000000ff
[   11.006890] Call Trace:
[   11.006903]  [<ffffffff813d438c>] dump_stack+0x63/0x87
[   11.006912]  [<ffffffff8107d776>] warn_slowpath_common+0x86/0xc0
[   11.006917]  [<ffffffff8107d7fc>] warn_slowpath_fmt+0x4c/0x50
[   11.006966]  [<ffffffffc029ed7e>] vlv_dpio_read+0x6e/0x80 [i915]
[   11.007014]  [<ffffffffc0286dd9>] i9xx_get_pipe_config+0x599/0x660 [i915]
[   11.007058]  [<ffffffffc013e2bd>] ? drm_property_unreference_blob+0xad/0xb0 [drm]
[   11.007107]  [<ffffffffc0282dff>] intel_modeset_check_state+0x2cf/0x8e0 [i915]
[   11.007156]  [<ffffffffc028e8b7>] intel_atomic_commit+0x5d7/0x640 [i915]
[   11.007187]  [<ffffffffc014c467>] drm_atomic_commit+0x37/0x60 [drm]
[   11.007202]  [<ffffffffc01b435d>] restore_fbdev_mode+0x22d/0x260 [drm_kms_helper]
[   11.007233]  [<ffffffffc014aca7>] ? drm_modeset_lock_all_ctx+0x97/0xb0 [drm]
[   11.007249]  [<ffffffffc01b6403>] drm_fb_helper_restore_fbdev_mode_unlocked+0x33/0x80 [drm_kms_helper]
[   11.007264]  [<ffffffffc01b647c>] drm_fb_helper_set_par+0x2c/0x50 [drm_kms_helper]
[   11.007280]  [<ffffffffc01b6382>] drm_fb_helper_hotplug_event+0xa2/0xf0 [drm_kms_helper]
[   11.007328]  [<ffffffffc02a428e>] intel_fbdev_output_poll_changed+0x1e/0x30 [i915]
[   11.007341]  [<ffffffffc01a95d7>] drm_kms_helper_hotplug_event+0x27/0x30 [drm_kms_helper]
[   11.007355]  [<ffffffffc01a96ad>] output_poll_execute+0x6d/0x1d0 [drm_kms_helper]
[   11.007362]  [<ffffffff81095970>] process_one_work+0x150/0x3f0
[   11.007367]  [<ffffffff810960ea>] worker_thread+0x11a/0x470
[   11.007372]  [<ffffffff81095fd0>] ? rescuer_thread+0x310/0x310
[   11.007377]  [<ffffffff8109b849>] kthread+0xc9/0xe0
[   11.007381]  [<ffffffff8109b780>] ? kthread_park+0x60/0x60
[   11.007389]  [<ffffffff817f770f>] ret_from_fork+0x3f/0x70
[   11.007393]  [<ffffffff8109b780>] ? kthread_park+0x60/0x60
[   11.007497] ---[ end trace 52c1a5962c25f868 ]---
[   11.009543] ------------[ cut here ]------------
[   11.009630] WARNING: CPU: 0 PID: 4 at /build/linux-lts-xenial-Hu9lgy/linux-lts-xenial-4.4.0/drivers/gpu/drm/i915/intel_sideband.c:200 vlv_dpio_read+0x6e/0x80 [i915]()
[   11.009634] DPIO read pipe A reg 0x800c == 0xffffffff
[   11.009637] Modules linked in: intel_rapl intel_powerclamp coretemp acer_wmi kvm_intel kvm irqbypass punit_atom_debug crct10dif_pclmul crc32_pclmul fdp_i2c fdp i2c_hid nci snd_soc_rt5640 aesni_intel nfc snd_soc_rl6231 aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd rfcomm bnep joydev hid_multitouch input_leds snd_intel_sst_acpi snd_intel_sst_core snd_soc_sst_mfld_platform snd_soc_core mei_txe lpc_ich snd_compress mei ac97_bus snd_pcm_dmaengine snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi 8250_fintek snd_seq hci_uart snd_seq_device snd_timer btbcm btqca btintel dw_dmac intel_hid sparse_keymap dw_dmac_core bluetooth i915 i2c_designware_platform i2c_designware_core snd nls_iso8859_1 soundcore 8250_dw pwm_lpss_platform pwm_lpss spi_pxa2xx_platform video tpm_crb drm_kms_helper drm int3400_thermal acpi_thermal_rel soc_button_array i2c_algo_bit fb_sys_fops syscopyarea int3403_thermal sysfillrect acpi_pad pinctrl_cherryview sysimgblt parport_pc wmi processor_thermal_device mac_hid ppdev int340x_thermal_zone intel_soc_dts_iosf lp parport hid_generic usbhid hid uas usb_storage mmc_block fjes sdhci_acpi sdhci
[   11.009767] CPU: 0 PID: 4 Comm: kworker/0:0 Tainted: G        W       4.4.0-34-generic #53~14.04.1-Ubuntu
[   11.009770] Hardware name: Acer Aspire SW3-016/Gummi CHT, BIOS V1.12 12/25/2015
[   11.009791] Workqueue: events output_poll_execute [drm_kms_helper]
[   11.009796]  0000000000000000 ffff880073933aa8 ffffffff813d438c ffff880073933af0
[   11.009802]  ffffffffc02f6b90 ffff880073933ae0 ffffffff8107d776 000000000000800c
[   11.009807]  0000000000000000 ffff880072180000 00000000ffffffff 00000000000000ff
[   11.009813] Call Trace:
[   11.009825]  [<ffffffff813d438c>] dump_stack+0x63/0x87
[   11.009833]  [<ffffffff8107d776>] warn_slowpath_common+0x86/0xc0
[   11.009838]  [<ffffffff8107d7fc>] warn_slowpath_fmt+0x4c/0x50
[   11.009887]  [<ffffffffc029ed7e>] vlv_dpio_read+0x6e/0x80 [i915]
[   11.009936]  [<ffffffffc0286dea>] i9xx_get_pipe_config+0x5aa/0x660 [i915]
[   11.009979]  [<ffffffffc013e2bd>] ? drm_property_unreference_blob+0xad/0xb0 [drm]
[   11.010028]  [<ffffffffc0282dff>] intel_modeset_check_state+0x2cf/0x8e0 [i915]
[   11.010077]  [<ffffffffc028e8b7>] intel_atomic_commit+0x5d7/0x640 [i915]
[   11.010108]  [<ffffffffc014c467>] drm_atomic_commit+0x37/0x60 [drm]
[   11.010124]  [<ffffffffc01b435d>] restore_fbdev_mode+0x22d/0x260 [drm_kms_helper]
[   11.010154]  [<ffffffffc014aca7>] ? drm_modeset_lock_all_ctx+0x97/0xb0 [drm]
[   11.010170]  [<ffffffffc01b6403>] drm_fb_helper_restore_fbdev_mode_unlocked+0x33/0x80 [drm_kms_helper]
[   11.010186]  [<ffffffffc01b647c>] drm_fb_helper_set_par+0x2c/0x50 [drm_kms_helper]
[   11.010201]  [<ffffffffc01b6382>] drm_fb_helper_hotplug_event+0xa2/0xf0 [drm_kms_helper]
[   11.010249]  [<ffffffffc02a428e>] intel_fbdev_output_poll_changed+0x1e/0x30 [i915]
[   11.010263]  [<ffffffffc01a95d7>] drm_kms_helper_hotplug_event+0x27/0x30 [drm_kms_helper]
[   11.010276]  [<ffffffffc01a96ad>] output_poll_execute+0x6d/0x1d0 [drm_kms_helper]
[   11.010283]  [<ffffffff81095970>] process_one_work+0x150/0x3f0
[   11.010288]  [<ffffffff810960ea>] worker_thread+0x11a/0x470
[   11.010293]  [<ffffffff81095fd0>] ? rescuer_thread+0x310/0x310
[   11.010298]  [<ffffffff8109b849>] kthread+0xc9/0xe0
[   11.010303]  [<ffffffff8109b780>] ? kthread_park+0x60/0x60
[   11.010310]  [<ffffffff817f770f>] ret_from_fork+0x3f/0x70
[   11.010315]  [<ffffffff8109b780>] ? kthread_park+0x60/0x60
[   11.010318] ---[ end trace 52c1a5962c25f869 ]---
[   11.014521] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in base.adjusted_mode.crtc_clock (expected 72500, found 18125)
[   11.014577] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in port_clock (expected 72500, found 18125)
[   11.014582] ------------[ cut here ]------------
[   11.014632] WARNING: CPU: 0 PID: 4 at /build/linux-lts-xenial-Hu9lgy/linux-lts-xenial-4.4.0/drivers/gpu/drm/i915/intel_display.c:12810 intel_modeset_check_state+0x573/0x8e0 [i915]()
[   11.014635] pipe state doesn't match!
[   11.014637] Modules linked in: intel_rapl intel_powerclamp coretemp acer_wmi kvm_intel kvm irqbypass punit_atom_debug crct10dif_pclmul crc32_pclmul fdp_i2c fdp i2c_hid nci snd_soc_rt5640 aesni_intel nfc snd_soc_rl6231 aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd rfcomm bnep joydev hid_multitouch input_leds snd_intel_sst_acpi snd_intel_sst_core snd_soc_sst_mfld_platform snd_soc_core mei_txe lpc_ich snd_compress mei ac97_bus snd_pcm_dmaengine snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi 8250_fintek snd_seq hci_uart snd_seq_device snd_timer btbcm btqca btintel dw_dmac intel_hid sparse_keymap dw_dmac_core bluetooth i915 i2c_designware_platform i2c_designware_core snd nls_iso8859_1 soundcore 8250_dw pwm_lpss_platform pwm_lpss spi_pxa2xx_platform video tpm_crb drm_kms_helper drm int3400_thermal acpi_thermal_rel soc_button_array i2c_algo_bit fb_sys_fops syscopyarea int3403_thermal sysfillrect acpi_pad pinctrl_cherryview sysimgblt parport_pc wmi processor_thermal_device mac_hid ppdev int340x_thermal_zone intel_soc_dts_iosf lp parport hid_generic usbhid hid uas usb_storage mmc_block fjes sdhci_acpi sdhci
[   11.014765] CPU: 0 PID: 4 Comm: kworker/0:0 Tainted: G        W       4.4.0-34-generic #53~14.04.1-Ubuntu
[   11.014768] Hardware name: Acer Aspire SW3-016/Gummi CHT, BIOS V1.12 12/25/2015
[   11.014788] Workqueue: events output_poll_execute [drm_kms_helper]
[   11.014793]  0000000000000000 ffff880073933b50 ffffffff813d438c ffff880073933b98
[   11.014799]  ffffffffc02f1fe8 ffff880073933b88 ffffffff8107d776 ffff880072f1c400
[   11.014804]  ffff88007541b000 ffff8800754cfb48 ffff880072e51400 ffff8800721fec00
[   11.014810] Call Trace:
[   11.014824]  [<ffffffff813d438c>] dump_stack+0x63/0x87
[   11.014832]  [<ffffffff8107d776>] warn_slowpath_common+0x86/0xc0
[   11.014837]  [<ffffffff8107d7fc>] warn_slowpath_fmt+0x4c/0x50
[   11.014886]  [<ffffffffc02830a3>] intel_modeset_check_state+0x573/0x8e0 [i915]
[   11.014935]  [<ffffffffc028e8b7>] intel_atomic_commit+0x5d7/0x640 [i915]
[   11.014981]  [<ffffffffc014c467>] drm_atomic_commit+0x37/0x60 [drm]
[   11.014996]  [<ffffffffc01b435d>] restore_fbdev_mode+0x22d/0x260 [drm_kms_helper]
[   11.015027]  [<ffffffffc014aca7>] ? drm_modeset_lock_all_ctx+0x97/0xb0 [drm]
[   11.015043]  [<ffffffffc01b6403>] drm_fb_helper_restore_fbdev_mode_unlocked+0x33/0x80 [drm_kms_helper]
[   11.015058]  [<ffffffffc01b647c>] drm_fb_helper_set_par+0x2c/0x50 [drm_kms_helper]
[   11.015073]  [<ffffffffc01b6382>] drm_fb_helper_hotplug_event+0xa2/0xf0 [drm_kms_helper]
[   11.015121]  [<ffffffffc02a428e>] intel_fbdev_output_poll_changed+0x1e/0x30 [i915]
[   11.015135]  [<ffffffffc01a95d7>] drm_kms_helper_hotplug_event+0x27/0x30 [drm_kms_helper]
[   11.015148]  [<ffffffffc01a96ad>] output_poll_execute+0x6d/0x1d0 [drm_kms_helper]
[   11.015155]  [<ffffffff81095970>] process_one_work+0x150/0x3f0
[   11.015160]  [<ffffffff810960ea>] worker_thread+0x11a/0x470
[   11.015165]  [<ffffffff81095fd0>] ? rescuer_thread+0x310/0x310
[   11.015170]  [<ffffffff8109b849>] kthread+0xc9/0xe0
[   11.015175]  [<ffffffff8109b780>] ? kthread_park+0x60/0x60
[   11.015182]  [<ffffffff817f770f>] ret_from_fork+0x3f/0x70
[   11.015186]  [<ffffffff8109b780>] ? kthread_park+0x60/0x60
[   11.015246] ---[ end trace 52c1a5962c25f86a ]---
[   13.657954] init: plymouth-upstart-bridge main process ended, respawning
[   13.677291] init: plymouth-upstart-bridge main process (1147) terminated with status 1
[   13.677335] init: plymouth-upstart-bridge main process ended, respawning
[   17.032375] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   17.101129] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)

```

---

### Post by jeremy31 on 2016-08-28
See the [bug reporting guide](https://ubuntuforums.org/showthread.php?t=1011078) and file a bug report against package linux as the kernel is having a lot of issues with the video modules.  This is likely part of the reason wifi isn't working

---

