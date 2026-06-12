---
title: "How can i permanently deactivate defect wifi card?"
date: 2019-07-08
forum: Networking &amp; Wireless
---

### Post by julz224 on 2019-07-08
Hi
i have installed a Lubuntu 19.04 on a old Dell Inspiron 6000 Notebook.
(L)Ubuntu runs pretty well (if installed with the LAN-Adapter), but if i want to install/configure my wifi card i ll get into trouble ...

I installed lubuntu first only with wifi ... i selected wifi as the default network card while the installation (via PXE) ... everything went fine ... downloading the packages ... installing lubuntu ... all fine ... but after finishing the installation and after the reboot i cant start lubuntu, because it runs into an infinite loop and stucks while booting up. i got this errors:
```

[  60.277072] Call Trace:
[  60.277072] Modules linked in: ;););)(PX)   # <- And yeah ... there are smylies!
[  60.277072] BUG: unable to handle kernel paging request at 000100fd
[  60.277072] #PF error: [normal kernel read fault]
[  60.277072] *pdpt = 000000002d18f001 *pde = 0000000000000000
[  60.277072] Thread overran stack, or stack corrupted
[  60.277072] Oops: 000 [#582] SMP PTI
[  60.277072] CPU: 0 PID: 574 Comm: wpa_supplicant Teinted: G           W             5.0.0-20-generic #21-Ubuntu
[  60.277072] Hardware name: Dell Inc. Inspiron 6000                               /0UF414, BIOS A09 09/28/2005
[  60.277072] EIP: print_modules+0x33/0xa1
[  60.277072] Code: <pretty long lane with hexadecimal digits like 83 ec 1c a1 14 00.........>
[  60.277072] EAX: 0000000B EBX: 000100fd ECX: 00000000 EDX: 00000000
[  60.277072] ESI:  c5b847b2 EDI: 000100fd EBP: ed0f5080 ESP: ed0f5060
[  60.277072] DS: 007b ES: 007b GS: 00e0 SS: 0068 EFLAGS: 00010007
[  60.277072] CR0: 80050033 CR2: 000100fd CR3: 2d1b2000 CR4: 000006f0
[  60.277072] 
[  60.277072] .... and all again ....
```

Ok i thought installing lubuntu with the LAN-Adapter is more stable. and it was. now its running pretty well.
but now if i want to install network-manager, wpa_supplicant, wicd, wicd-daemon or something like that ... all what touches the wifi card ... i run into the same loop like on the installation above and get stuck.

My wifi adapter was identified as: Qualcomm Atheros AR5212/5213/2414 Wireless Network Adapter

Is there a way how i can deactivate/remove the wifi card ... so that the hardware will not be touched from ubuntu, so i can install the network-manager without running into a loop?
is there anything i can else do to repair this error?
the wificard was running fine on windows 7

thank you

---

### Post by praseodym on 2019-07-08
BIOS/UEFI? Can you start with a live-usb or DVD and show the output of
```

lspci -nnk
lsusb
lsmod
```

---

### Post by julz224 on 2019-07-09
As you can see in the Output above ... yes its a BIOS.
I'm not at home till friday, but then i will post the output of the commands above.

EDIT:
```
root@Dell-Inspiron-6000:/home/julian# lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
        Subsystem: Dell Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [1028:0188]
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port [8086:2591] (rev 03)
        Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
        Subsystem: Dell 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI [1028:0188]
        Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
        Subsystem: Dell 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI [1028:0188]
        Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
        Subsystem: Dell 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI [1028:0188]
        Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
        Subsystem: Dell 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI [1028:0188]
        Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
        Subsystem: Dell 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [1028:0188]
        Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
        Subsystem: Dell Inspiron 6000 laptop [1028:0188]
        Kernel driver in use: snd_intel8x0
        Kernel modules: snd_intel8x0
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
        Subsystem: Dell 82801FBM (ICH6M) LPC Interface Bridge [1028:0188]
        Kernel driver in use: lpc_ich
        Kernel modules: intel_rng, lpc_ich
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
        Subsystem: Dell 82801FBM (ICH6M) SATA Controller [1028:0188]
        Kernel driver in use: ata_piix
        Kernel modules: ahci, pata_acpi
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV370/M22 [Mobility Radeon X300] [1002:5460]
        Subsystem: Dell RV370/M22 [Mobility Radeon X300] [1028:2003]
        Kernel driver in use: radeon
        Kernel modules: radeonfb, radeon
03:00.0 Ethernet controller [0200]: Broadcom Inc. and subsidiaries BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
        Subsystem: Dell Inspiron 6000 laptop [1028:0188]
        Kernel driver in use: b44
        Kernel modules: b44
03:01.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b3)
        Subsystem: Dell Inspiron 6000 laptop [1028:0188]
        Kernel driver in use: yenta_cardbus
        Kernel modules: yenta_socket
03:01.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 08)
        Subsystem: Dell Inspiron 6000 laptop [1028:0188]
        Kernel driver in use: firewire_ohci
        Kernel modules: firewire_ohci
03:01.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 17)
        Subsystem: Dell Inspiron 6000 laptop [1028:0188]
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci_pci
[B]03:03.0 Ethernet controller [0200]: Qualcomm Atheros AR5212/5213/2414 Wireless Network Adapter [168c:0013] (rev 01)
        Subsystem: Gigabyte Technology Co., Ltd GN-WIAG02 [1458:e911]
        Kernel driver in use: ath5k
        Kernel modules: ath5k[/B]

```
```
root@Dell-Inspiron-6000:/home/julian# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
```
root@Dell-Inspiron-6000:/home/julian# lsmod
Module                  Size  Used by
rfcomm                 65536  4
bnep                   24576  2
arc4                   16384  2
ath5k                 139264  0
radeon               1388544  7
dell_laptop            20480  0
ath                    24576  1 ath5k
btusb                  49152  0
snd_intel8x0           40960  2
ledtrig_audio          16384  1 dell_laptop
mac80211              716800  1 ath5k
dell_smbios            24576  1 dell_laptop
btrtl                  20480  1 btusb
snd_ac97_codec        110592  1 snd_intel8x0
dell_wmi_descriptor    20480  1 dell_smbios
ttm                    90112  1 radeon
btbcm                  16384  1 btusb
ac97_bus               16384  1 snd_ac97_codec
wmi                    28672  2 dell_wmi_descriptor,dell_smbios
btintel                24576  1 btusb
drm_kms_helper        159744  1 radeon
dcdbas                 20480  1 dell_smbios
snd_pcm                90112  2 snd_ac97_codec,snd_intel8x0
cfg80211              585728  3 mac80211,ath,ath5k
bluetooth             483328  29 btrtl,btintel,bnep,btbcm,rfcomm,btusb
dell_smm_hwmon         16384  0
drm                   376832  10 radeon,ttm,drm_kms_helper
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                61440  2 snd_seq_midi_event,snd_seq_midi
i2c_algo_bit           16384  1 radeon
fb_sys_fops            16384  1 drm_kms_helper
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
pcmcia                 57344  0
joydev                 24576  0
ecdh_generic           32768  1 bluetooth
syscopyarea            16384  1 drm_kms_helper
snd_timer              32768  2 snd_seq,snd_pcm
input_leds             16384  0
yenta_socket           40960  0
serio_raw              20480  0
mac_hid                16384  0
sysfillrect            16384  1 drm_kms_helper
pcmcia_rsrc            24576  1 yenta_socket
sysimgblt              16384  1 drm_kms_helper
pcmcia_core            28672  3 yenta_socket,pcmcia,pcmcia_rsrc
snd                    69632  11 snd_seq,snd_ac97_codec,snd_timer,snd_rawmidi,snd_intel8x0,snd_seq_device,snd_pcm
soundcore              16384  1 snd
sch_fq_codel           20480  6
parport_pc             32768  0
ppdev                  24576  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               32768  1 ip_tables
autofs4                45056  2
gpio_ich               16384  0
b44                    32768  0
pata_acpi              16384  0
sdhci_pci              40960  0
firewire_ohci          36864  0
ahci                   36864  0
cqhci                  28672  1 sdhci_pci
psmouse               139264  0
ssb                    61440  1 b44
firewire_core          57344  1 firewire_ohci
lpc_ich                24576  0
libahci                32768  1 ahci
sdhci                  53248  1 sdhci_pci
mii                    16384  1 b44
crc_itu_t              16384  1 firewire_core
video                  45056  1 dell_laptop

```

---

### Post by praseodym on 2019-07-13
Ok, please run the wireless script from the sticky thread and show the outputs. Any chance updating your BIOS? Or resetting it to default settings?

---

### Post by julz224 on 2019-07-13
Its already the last BIOS version ... its an old laptop.
Is there a way to connect to a WLAN with a GUI somewhere?
I dont want to install the network-manager again because of the loop/freeze while installation...

Here the output from the script:
[http://paste.ubuntu.com/p/2ZJjpKynPW/](http://paste.ubuntu.com/p/2ZJjpKynPW/)

---

### Post by praseodym on 2019-07-13
There are three networks with the same ESSID "WLAN-24". Are you using a repeater? Try

```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

---

### Post by TheFu on 2019-07-13
So, I'm unclear.  Do you want to try and get the wifi working or do you want to never see it again as the title says?

To disable the onboard wifi, go into the computer BIOS and disable it.  Simple.  Then the OS will never see it again.  If the wifi isn't AC compatible, it is probably time to get a cheap-O USB wifi dongle for $12 that is AC.  Pick one that is well supported by Linux so you don't have to fight with it.  Just plug it in and use.

---

### Post by julz224 on 2019-07-14
Yes, i have 3 access points with the same ESSID.
i try the wifi to get work, but it wasn't possible to install a network-manager, wicd or something without getting into a loop.
so i want to deactivate my wifi card to get not into trouble with this.
but with the tipp deactivating wifi in the bios (so simple -.-) i was able to install successfully network-manager and wicd so now after activating wifi in bios again ... all runs fine for now.

---

### Post by TheFu on 2019-07-14
a) if this is solved, please use the "thread tools" button near the top to mark it that way.

b) I wouldn't leave NM and wicd on the same machine.  Probably need to purge one of them.  Don't want too many cooks trying to manage networking. Bad things happen.

---

