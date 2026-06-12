---
title: "Asus t100ha"
date: 2016-09-05
forum: Networking &amp; Wireless
---

### Post by zeran on 2016-09-05
Hello all First I speak through a translator , I have problems with my asus T100HA , the wireless card 're not detect sub lubuntu 16.04 ( no sound card , for that matter ) .
I put you under orders that have already been used .
Thank you for your help.

```

description: Ordinateur Bloc-notes
    produit: T100HAN (ASUS-TabletSKU)
    fabriquant: ASUSTeK COMPUTER INC.
    version: 1.0
    numéro de série: FCN0CV11M142506
    bits: 64 bits
    fonctionnalités: smbios-2.8 dmi-2.8 vsyscall32
    configuration: boot=normal chassis=notebook family=T sku=ASUS-TabletSKU uuid=EF4AC999-9D3A-4D2D-9680-06B9B401FB94
  *-core
       description: Carte mère
       produit: T100HAN
       fabriquant: ASUSTeK COMPUTER INC.
       identifiant matériel: 0
       version: 1.0
       numéro de série: BSN12345678901234567
       emplacement: MIDDLE
     *-firmware
          description: BIOS
          fabriquant: American Megatrends Inc.
          identifiant matériel: 0
          version: T100HAN.221
          date: 05/18/2016
          taille: 64KiB
          capacité: 6080KiB
          fonctionnalités: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int14serial int17printer acpi usb smartbattery biosbootspecification uefi
     *-memory
          description: Mémoire Système
          identifiant matériel: b
          emplacement: Carte mère
          taille: 4GiB
        *-bank:0
             description: DIMM DDR3 1600 MHz (0,6 ns)
             produit: Array1_PartNumber0
             fabriquant: A1_Manufacturer0
             identifiant matériel: 0
             numéro de série: A1_SerNum0
             emplacement: A1_DIMM0
             taille: 2GiB
             bits: 8 bits
             horloge: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM DDR3 1600 MHz (0,6 ns)
             produit: Array1_PartNumber1
             fabriquant: A1_Manufacturer1
             identifiant matériel: 1
             numéro de série: A1_SerNum1
             emplacement: A1_DIMM1
             taille: 2GiB
             bits: 8 bits
             horloge: 1600MHz (0.6ns)
     *-cache:0
          description: L1 cache
          identifiant matériel: 12
          emplacement: CPU Internal L1
          taille: 224KiB
          capacité: 224KiB
          fonctionnalités: internal write-back
          configuration: level=1
     *-cache:1
          description: L2 cache
          identifiant matériel: 13
          emplacement: CPU Internal L2
          taille: 2MiB
          capacité: 2MiB
          fonctionnalités: internal write-back unified
          configuration: level=2
     *-cpu
          description: CPU
          produit: Intel(R) Atom(TM) x5-Z8500  CPU @ 1.44GHz
          fabriquant: Intel Corp.
          identifiant matériel: 14
          information bus: cpu@0
          version: Intel(R) Atom(TM) x5-Z8500 CPU @ 1.44GHz
          emplacement: SOCKET 0
          taille: 1652MHz
          capacité: 2400MHz
          bits: 64 bits
          horloge: 80MHz
          fonctionnalités: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch epb tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat cpufreq
          configuration: cores=4 enabledcores=4 threads=4
     *-pci
          description: Host bridge
          produit: Intel Corporation
          fabriquant: Intel Corporation
          identifiant matériel: 100
          information bus: pci@0000:00:00.0
          version: 20
          bits: 32 bits
          horloge: 33MHz
          configuration: driver=iosf_mbi_pci
          ressources: irq:0
        *-display
             description: VGA compatible controller
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 2
             information bus: pci@0000:00:02.0
             version: 20
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             ressources: irq:310 mémoire:90000000-90ffffff mémoire:80000000-8fffffff portE/S:f000(taille=64)
        *-multimedia NON-RÉCLAMÉ
             description: Multimedia controller
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 3
             information bus: pci@0000:00:03.0
             version: 20
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pm msi cap_list
             configuration: latency=0
             ressources: mémoire:91000000-913fffff
        *-generic:0 NON-RÉCLAMÉ
             description: Non-VGA unclassified device
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: a
             information bus: pci@0000:00:0a.0
             version: 20
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pm cap_list
             configuration: latency=0
             ressources: mémoire:9183a000-9183afff
        *-generic:1
             description: Signal processing controller
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: b
             information bus: pci@0000:00:0b.0
             version: 20
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: msi pm cap_list
             configuration: driver=proc_thermal latency=0
             ressources: irq:311 mémoire:91839000-91839fff
        *-usb
             description: USB controller
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 14
             information bus: pci@0000:00:14.0
             version: 20
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             ressources: irq:115 mémoire:91800000-9180ffff
           *-usbhost:0
                produit: xHCI Host Controller
                fabriquant: Linux 4.4.0-31-generic xhci-hcd
                identifiant matériel: 0
                information bus: usb@2
                nom logique: usb2
                version: 4.04
                fonctionnalités: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
           *-usbhost:1
                produit: xHCI Host Controller
                fabriquant: Linux 4.4.0-31-generic xhci-hcd
                identifiant matériel: 1
                information bus: usb@1
                nom logique: usb1
                version: 4.04
                fonctionnalités: usb-2.00
                configuration: driver=hub slots=7 speed=480Mbit/s
              *-usb
                   description: Concentrateur USB
                   produit: USB2.0 Hub
                   fabriquant: Genesys Logic, Inc.
                   identifiant matériel: 3
                   information bus: usb@1:3
                   version: 32.98
                   fonctionnalités: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Périphérique USB générique
                      produit: 802.11 n WLAN
                      fabriquant: Ralink
                      identifiant matériel: 1
                      information bus: usb@1:3.1
                      version: 1.01
                      numéro de série: 1.0
                      fonctionnalités: usb-2.00
                      configuration: driver=rt2800usb maxpower=450mA speed=480Mbit/s
                 *-usb:1
                      description: Clavier
                      produit: ASUS HID Device
                      fabriquant: ASUS Tech Inc.
                      identifiant matériel: 3
                      information bus: usb@1:3.3
                      version: 0.11
                      fonctionnalités: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
        *-generic:2
             description: Encryption controller
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 1a
             information bus: pci@0000:00:1a.0
             version: 20
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             ressources: irq:312 mémoire:91700000-917fffff mémoire:91600000-916fffff
        *-isa
             description: ISA bridge
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 1f
             information bus: pci@0000:00:1f.0
             version: 20
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             ressources: irq:0
  *-network
       description: Interface réseau sans fil
       identifiant matériel: 1
       information bus: usb@1:3.1
       nom logique: wlxc4a81de76381
       numéro de série: c4:a8:1d:e7:63:81
       fonctionnalités: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=4.4.0-31-generic firmware=0.29 ip=192.168.1.85 link=yes multicast=yes wireless=IEEE 802.11bgn


```


I want to clarify that I currently have wifi with wifi dongle but I am operating the wireless internet.

---

### Post by praseodym on 2016-09-05
Please show:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by zeran on 2016-09-06
[COLOR=#212121][FONT=arial]thank you for your help, here are commands

[/FONT][/COLOR]

for lspci -nnk | grep -iA2 net
```
benj@benj-T100HAN:~$ lspci -nnk | grep -iA2 netbenj@benj-T100HAN:~$ 


```

for lsusb

```
benj@benj-T100HAN:~$ lsusbBus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0b05:1807 ASUSTek Computer, Inc. 
Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 005: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

for lsmod

```
benj@benj-T100HAN:~$ lsmodModule                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  0
ccm                    20480  0
arc4                   16384  0
rt2800usb              28672  0
rt2x00usb              24576  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              737280  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              565248  2 mac80211,rt2x00lib
crc_ccitt              16384  1 rt2800lib
hid_multitouch         20480  0
asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
intel_rapl             20480  0
binfmt_misc            20480  1
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             172032  0
nls_iso8859_1          16384  1
kvm                   540672  1 kvm_intel
irqbypass              16384  1 kvm
punit_atom_debug       16384  0
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
joydev                 20480  0
input_leds             16384  0
mei_txe                20480  0
mei                    98304  1 mei_txe
lpc_ich                24576  0
processor_thermal_device    16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
snd_intel_sst_acpi     16384  0
snd_intel_sst_core     73728  1 snd_intel_sst_acpi
snd_soc_sst_mfld_platform    90112  1 snd_intel_sst_core
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_pcm               106496  4 snd_soc_rt5640,snd_soc_core,snd_soc_sst_mfld_platform,snd_pcm_dmaengine
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
8250_fintek            16384  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
intel_hid              16384  0
sparse_keymap          16384  2 intel_hid,asus_wmi
dw_dmac                16384  0
dw_dmac_core           24576  1 dw_dmac
snd                    81920  8 snd_soc_core,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_soc_sst_mfld_platform,snd_seq_device,snd_compress
i2c_designware_platform    16384  0
i2c_designware_core    20480  1 i2c_designware_platform
soundcore              16384  1 snd
pwm_lpss_platform      16384  0
pwm_lpss               16384  1 pwm_lpss_platform
spi_pxa2xx_platform    24576  0
8250_dw                16384  0
tpm_crb                16384  0
soc_button_array       16384  0
mac_hid                16384  0
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
int3403_thermal        16384  0
int340x_thermal_zone    16384  2 processor_thermal_device,int3403_thermal
acpi_pad               20480  0
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
mmc_block              36864  6
i915                 1265664  6
i2c_algo_bit           16384  1 i915
drm_kms_helper        147456  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  8 i915,drm_kms_helper
wmi                    20480  1 asus_wmi
video                  40960  2 i915,asus_wmi
i2c_hid                20480  0
hid                   118784  5 i2c_hid,hid_multitouch,hid_generic,usbhid
fjes                   28672  0
sdhci_acpi             16384  0
sdhci                  45056  1 sdhci_acpi
pinctrl_cherryview     32768  13

```

for iwconfig

```
benj@benj-T100HAN:~$ iwconfiglo        no wireless extensions.

```

and for rfkill list

```
benj@benj-T100HAN:~$ rfkill list
benj@benj-T100HAN:~$ 
```

---

### Post by praseodym on 2016-09-06
Lets check
```
pccardctl info
lspci -nnk
```
Also check the BIOS/UEFI if it can be activated there

---

### Post by zeran on 2016-09-06
for  pccardctl info
```
benj@benj-T100HAN:~$ pccardctl info
            benj@benj-T100HAN:~$

```


for lspci -nnk

```

00:00.0 Host bridge [0600]: Intel Corporation Device [8086:2280] (rev 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1bdd]
	Kernel driver in use: iosf_mbi_pci
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:22b0] (rev 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1bdd]
	Kernel driver in use: i915
	Kernel modules: i915
00:03.0 Multimedia controller [0480]: Intel Corporation Device [8086:22b8] (rev 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1bdd]
00:0a.0 Non-VGA unclassified device [0000]: Intel Corporation Device [8086:22d8] (rev 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1bdd]
00:0b.0 Signal processing controller [1180]: Intel Corporation Device [8086:22dc] (rev 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1bdd]
	Kernel driver in use: proc_thermal
	Kernel modules: processor_thermal_device
00:14.0 USB controller [0c03]: Intel Corporation Device [8086:22b5] (rev 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1bdd]
	Kernel driver in use: xhci_hcd
00:1a.0 Encryption controller [1080]: Intel Corporation Device [8086:2298] (rev 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1bdd]
	Kernel driver in use: mei_txe
	Kernel modules: mei_txe
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:229c] (rev 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1bdd]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich
benj@benj-T100HAN:~$ 



```

bios for it does not give me the choice unfortunately but I think asus bios hides a director but I're not discovered or

---

