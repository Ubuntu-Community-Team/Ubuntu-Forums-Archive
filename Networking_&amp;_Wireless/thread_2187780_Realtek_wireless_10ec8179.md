---
title: "Realtek wireless 10ec:8179"
date: 2013-11-13
forum: Networking &amp; Wireless
---

### Post by PsykoMantis on 2013-11-13
Hi, i have a big problem and i need to solve it really fast!

I have a notebook HP my connection work with Ethernet but my wifi is not seen by ubuntu. I don't know how to do. 

I'm posting a list of command that help you guys...

[B]$ uname -r -m
[/B]```
3.8.0-33-generic x86_64


```

**$ sudo lshw -c network**

```
  

*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:4000(size=256) memory:c3500000-c3503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 07
       serial: a0:48:1c:12:ae:93
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8101 driverversion=1.024.00-NAPI duplex=full ip=192.168.1.221 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:c3404000-c3404fff memory:c3400000-c3403fff memory:9fb00000-9fb0ffff


```

**$ iwconfig**

```

eth0      no wireless extensions.

lo        no wireless extensions.


```
[B]
$ lspci -vnn | grep -i net -A 8[/B]

```
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:197d]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    I/O ports at 4000 [size=256]
    Memory at c3500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
--
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1970]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    I/O ports at 3000 [size=256]
    Memory at c3404000 (64-bit, prefetchable) [size=4K]
    Memory at c3400000 (64-bit, prefetchable) [size=16K]
    [virtual] Expansion ROM at 9fb00000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+


```

**$  rfkill list**   -> none

[B]
$ nm-tool[/B]
```
NetworkManager Tool

State: connected (global)

- Device: eth0  [Connessione via cavo 1] ---------------------------------------
  Type:              Wired
  Driver:            r8101
  State:             connected
  Default:           yes
  HW Address:        A0:48:1C:12:AE:93

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.221
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


```

**$ cat  /etc/network/interfaces**
```

auto lo
iface lo inet loopback
```

**$ lsmod**
```

Module                  Size  Used by
r8101                 111980  0 
rfcomm                 47864  0 
bnep                   18258  2 
bluetooth             247165  10 rfcomm,bnep
parport_pc             28284  0 
ppdev                  17113  0 
nls_iso8859_1          12713  1 
fglrx                6728820  224 
snd_hda_codec_hdmi     37463  1 
snd_hda_codec_realtek    79916  1 
uvcvideo               82214  0 
coretemp               13596  0 
kvm_intel             137899  0 
videobuf2_core         40785  1 uvcvideo
kvm                   455932  1 kvm_intel
snd_hda_intel          44339  5 
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
videodev              130053  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13056  1 uvcvideo
snd_hwdep              13668  1 snd_hda_codec
ghash_clmulni_intel    13259  0 
snd_pcm               102477  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
aesni_intel            55495  0 
ablk_helper            13597  1 aesni_intel
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lrw                    13294  1 aesni_intel
snd_seq_midi_event     14899  1 snd_seq_midi
i915                  620571  2 
psmouse                97873  0 
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
aes_x86_64             17255  1 aesni_intel
xts                    12922  1 aesni_intel
gf128mul               14951  2 lrw,xts
videobuf2_memops       13202  1 videobuf2_vmalloc
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17613  0 
hid_waltop             13064  0 
serio_raw              13215  0 
drm_kms_helper         49597  1 i915
drm                   287564  3 i915,drm_kms_helper
mei                    41820  0 
snd                    69533  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_wmi                 18092  0 
hp_accel               26012  0 
sparse_keymap          13890  1 hp_wmi
soundcore              12680  1 snd
lis3lv02d              20200  1 hp_accel
input_polldev          13896  1 lis3lv02d
wmi                    19256  1 hp_wmi
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
amd_iommu_v2           19198  1 fglrx
lpc_ich                17144  0 
microcode              23017  0 
i2c_algo_bit           13564  1 i915
video                  19652  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_generic            12540  0 
usbhid                 47346  0 
hid                   105826  3 hid_waltop,hid_generic,usbhid
ahci                   25879  3 
libahci                31606  1 ahci


```

**$ lspci**
```

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 Display controller: Advanced Micro Devices [AMD] nee ATI Device 6660
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8179 (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)


```

thanks in advance....i hope that someone can help me";)

---

### Post by chili555 on 2013-11-13
First, this is not your wireless: RTL8101E/RTL8102E; this is: Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8179] (rev 01)

Second, here is your quick fix: [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281)>  
If this is your device, it is covered by the very new driver rtl8188ee:

Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8179] 
Post back if you get stuck.

---

### Post by PsykoMantis on 2013-11-14
thanks for the reply...here the output of the procedure. I'm sorry for the language that is not english and for the mistake of the card!
**lspci -nn**
```

00:00.0 Host bridge [0600]: Intel Corporation Ivy Bridge DRAM Controller [8086:0154] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Ivy Bridge PCI Express Root Port [8086:0151] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation Panther Point USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1c.2 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 3 [8086:1e14] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e59] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)
01:00.0 Display controller [0380]: Advanced Micro Devices [AMD] nee ATI Device [1002:6660]
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8179] (rev 01)
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)


```


**$ sudo apt-get install linux-headers-generic build-essential**
```

[sudo] password for francesco: 
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Il seguente pacchetto è stato installato automaticamente e non è più richiesto:
  thunderbird-globalmenu
Usare "apt-get autoremove" per rimuoverli.
I seguenti pacchetti saranno inoltre installati:
  dpkg-dev g++ g++-4.6 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libdpkg-perl libstdc++6-4.6-dev
  libtimedate-perl linux-headers-3.2.0-56 linux-headers-3.2.0-56-generic
Pacchetti suggeriti:
  debian-keyring g++-multilib g++-4.6-multilib gcc-4.6-doc
  libstdc++6-4.6-dbg libstdc++6-4.6-doc
I seguenti pacchetti NUOVI saranno installati:
  build-essential dpkg-dev g++ g++-4.6 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libstdc++6-4.6-dev libtimedate-perl linux-headers-3.2.0-56
  linux-headers-3.2.0-56-generic linux-headers-generic
0 aggiornati, 13 installati, 0 da rimuovere e 142 non aggiornati.
È necessario scaricare 22,1 MB di archivi.
Dopo quest'operazione, verranno occupati 96,2 MB di spazio su disco.
Continuare [S/n]? s
Scaricamento di:1 http://it.archive.ubuntu.com/ubuntu/ precise/main libstdc++6-4.6-dev amd64 4.6.3-1ubuntu5 [1660 kB]
Scaricamento di:2 http://it.archive.ubuntu.com/ubuntu/ precise/main g++-4.6 amd64 4.6.3-1ubuntu5 [6954 kB]
Scaricamento di:3 http://it.archive.ubuntu.com/ubuntu/ precise/main g++ amd64 4:4.6.3-1ubuntu5 [1442 B]
Scaricamento di:4 http://it.archive.ubuntu.com/ubuntu/ precise/main libtimedate-perl all 1.2000-1 [41,6 kB]
Scaricamento di:5 http://it.archive.ubuntu.com/ubuntu/ precise-updates/main libdpkg-perl all 1.16.1.2ubuntu7.2 [180 kB]
Scaricamento di:6 http://it.archive.ubuntu.com/ubuntu/ precise-updates/main dpkg-dev all 1.16.1.2ubuntu7.2 [469 kB]
Scaricamento di:7 http://it.archive.ubuntu.com/ubuntu/ precise-updates/main build-essential amd64 11.5ubuntu2.1 [5816 B]
Scaricamento di:8 http://it.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-diff-perl all 1.19.02-2 [50,7 kB]
Scaricamento di:9 http://it.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-diff-xs-perl amd64 0.04-2build2 [12,4 kB]
Scaricamento di:10 http://it.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-merge-perl all 0.08-2 [12,7 kB]
Scaricamento di:11 http://it.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-56 all 3.2.0-56.86 [11,7 MB]
Scaricamento di:12 http://it.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-56-generic amd64 3.2.0-56.86 [978 kB]
Scaricamento di:13 http://it.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-generic amd64 3.2.0.56.66 [2250 B]
Recuperati 22,1 MB in 29s (752 kB/s)                                      
Selezionato il pacchetto libstdc++6-4.6-dev non precedentemente selezionato.
(Lettura del database... 176422 file e directory attualmente installati.)
Estrazione di libstdc++6-4.6-dev (da .../libstdc++6-4.6-dev_4.6.3-1ubuntu5_amd64.deb)...
Selezionato il pacchetto g++-4.6 non precedentemente selezionato.
Estrazione di g++-4.6 (da .../g++-4.6_4.6.3-1ubuntu5_amd64.deb)...
Selezionato il pacchetto g++ non precedentemente selezionato.
Estrazione di g++ (da .../g++_4%3a4.6.3-1ubuntu5_amd64.deb)...
Selezionato il pacchetto libtimedate-perl non precedentemente selezionato.
Estrazione di libtimedate-perl (da .../libtimedate-perl_1.2000-1_all.deb)...
Selezionato il pacchetto libdpkg-perl non precedentemente selezionato.
Estrazione di libdpkg-perl (da .../libdpkg-perl_1.16.1.2ubuntu7.2_all.deb)...
Selezionato il pacchetto dpkg-dev non precedentemente selezionato.
Estrazione di dpkg-dev (da .../dpkg-dev_1.16.1.2ubuntu7.2_all.deb)...
Selezionato il pacchetto build-essential non precedentemente selezionato.
Estrazione di build-essential (da .../build-essential_11.5ubuntu2.1_amd64.deb)...
Selezionato il pacchetto libalgorithm-diff-perl non precedentemente selezionato.
Estrazione di libalgorithm-diff-perl (da .../libalgorithm-diff-perl_1.19.02-2_all.deb)...
Selezionato il pacchetto libalgorithm-diff-xs-perl non precedentemente selezionato.
Estrazione di libalgorithm-diff-xs-perl (da .../libalgorithm-diff-xs-perl_0.04-2build2_amd64.deb)...
Selezionato il pacchetto libalgorithm-merge-perl non precedentemente selezionato.
Estrazione di libalgorithm-merge-perl (da .../libalgorithm-merge-perl_0.08-2_all.deb)...
Selezionato il pacchetto linux-headers-3.2.0-56 non precedentemente selezionato.
Estrazione di linux-headers-3.2.0-56 (da .../linux-headers-3.2.0-56_3.2.0-56.86_all.deb)...
Selezionato il pacchetto linux-headers-3.2.0-56-generic non precedentemente selezionato.
Estrazione di linux-headers-3.2.0-56-generic (da .../linux-headers-3.2.0-56-generic_3.2.0-56.86_amd64.deb)...
Selezionato il pacchetto linux-headers-generic non precedentemente selezionato.
Estrazione di linux-headers-generic (da .../linux-headers-generic_3.2.0.56.66_amd64.deb)...
Elaborazione dei trigger per man-db...
Configurazione di libtimedate-perl (1.2000-1)...
Configurazione di libdpkg-perl (1.16.1.2ubuntu7.2)...
Configurazione di dpkg-dev (1.16.1.2ubuntu7.2)...
Configurazione di libalgorithm-diff-perl (1.19.02-2)...
Configurazione di libalgorithm-diff-xs-perl (0.04-2build2)...
Configurazione di libalgorithm-merge-perl (0.08-2)...
Configurazione di linux-headers-3.2.0-56 (3.2.0-56.86)...
Configurazione di linux-headers-3.2.0-56-generic (3.2.0-56.86)...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-56-generic /boot/vmlinuz-3.2.0-56-generic
Configurazione di linux-headers-generic (3.2.0.56.66)...
Configurazione di libstdc++6-4.6-dev (4.6.3-1ubuntu5)...
Configurazione di g++-4.6 (4.6.3-1ubuntu5)...
Configurazione di g++ (4:4.6.3-1ubuntu5)...
update-alternatives: viene usato /usr/bin/g++ per fornire /usr/bin/c++ (c++) in modalità automatica.
Configurazione di build-essential (11.5ubuntu2.1)...




```

**make clean**
```
 
Generating local configuration database from kernel ... done.

```

 **make defconfig-rtlwifi**
```

cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c
cc   conf.o zconf.tab.o   -o conf
#
# configuration written to .config
#

```

 **make**
```

make[5]: "conf" è aggiornato.
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/compat/main.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/compat/compat-3.9.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/compat/backport-3.10.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/compat/backport-3.11.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/compat/compat.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/base.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/cam.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/core.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/debug.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/efuse.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/ps.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rc.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/regd.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/stats.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/pci.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/usb.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtlwifi.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8188ee/dm.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8188ee/fw.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8188ee/hw.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8188ee/led.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8188ee/phy.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8188ee/pwrseq.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8188ee/pwrseqcmd.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8188ee/rf.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8188ee/sw.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8188ee/table.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8188ee/trx.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192c/main.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192c/dm_common.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192c/phy_common.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192ce/dm.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192ce/hw.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192ce/led.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192ce/phy.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192ce/rf.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192ce/sw.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192ce/table.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192ce/trx.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192cu/dm.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192cu/hw.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192cu/led.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192cu/mac.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192cu/phy.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192cu/rf.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192cu/sw.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192cu/table.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192cu/trx.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192de/dm.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192de/fw.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192de/hw.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192de/led.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192de/phy.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192de/rf.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192de/sw.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192de/table.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192de/trx.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192se/dm.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192se/fw.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192se/hw.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192se/led.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192se/phy.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192se/rf.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192se/sw.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192se/table.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192se/trx.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/dm.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/fw.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/hal_btc.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/hal_bt_coexist.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/hw.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/led.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/phy.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/pwrseq.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/pwrseqcmd.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/rf.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/sw.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/table.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/trx.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/main.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/status.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/sta_info.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/wep.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/wpa.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/scan.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/offchannel.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/ht.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/agg-tx.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/agg-rx.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/vht.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/ibss.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/iface.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/rate.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/michael.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/tkip.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/aes_ccm.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/aes_cmac.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/cfg.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/rx.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/spectmgmt.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/tx.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/key.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/util.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/wme.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/event.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/chan.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/trace.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/mlme.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/debugfs.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/debugfs_sta.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/debugfs_netdev.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/debugfs_key.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/pm.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/mac80211.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/core.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/sysfs.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/radiotap.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/util.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/reg.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/scan.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/nl80211.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/mlme.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/ibss.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/sme.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/chan.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/ethtool.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/mesh.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/ap.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/trace.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/debugfs.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/wext-compat.o
  CC [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/wext-sme.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/cfg80211.o
  Building modules, stage 2.
  MODPOST 11 modules
  CC      /home/francesco/Scrivania/backports-3.11-rc3-1/compat/compat.mod.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/compat/compat.ko
  CC      /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.mod.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
  CC      /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.mod.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
  CC      /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.mod.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
  CC      /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.mod.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
  CC      /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.mod.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
  CC      /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.mod.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
  CC      /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.mod.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
  CC      /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtlwifi.mod.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtlwifi.ko
  CC      /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/mac80211.mod.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/mac80211.ko
  CC      /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/cfg80211.mod.o
  LD [M]  /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/cfg80211.ko


```
[B]
sudo make install[/B]
```

  Building modules, stage 2.
  MODPOST 11 modules
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/compat/compat.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtlwifi.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/mac80211.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/cfg80211.ko
Can't read private key
  DEPMOD  3.8.0-33-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.

Your backported driver modules should be installed now.
Reboot.



```
** sudo modprobe rtl8188ee** -> NONE

Ubuntu still not see the card....what should i do? 
I haven't run the following code after the error 

> If the message logs say you need firmware:
  dmesg | grep rtl
  Download and install it with: 
  wget [http://mirror.pnl.gov/ubuntu//pool/main/l/linux-firmware/linux-firmware_1.106_all.deb](http://mirror.pnl.gov/ubuntu//pool/main/l/linux-firmware/linux-firmware_1.106_all.deb)
sudo dpkg -i linux*.deb 
sudo modprobe -r rtl8188ee && sudo modprobe rtl8188ee


thanks again for your patience and time.

---

### Post by chili555 on 2013-11-14
It appears you have made a few changes to your kernel along the way. In post #1, you said:> $ uname -r -m
Code:

[COLOR="#FF0000"]3.**8**.0-33-generic [/COLOR]x86_64

But then one of the updates you downloaded was:> linux-headers-3.[COLOR="#FF0000"]2[/COLOR].0-56-genericPlease reboot so that you have a clean slate and compile again:```
cd Scrivania/backports-3.11-rc3-1/
make clean
make defconfig-rtlwifi
make
sudo make install
sudo modprobe rtl8188ee
```Please do not post the entire output unless it results in an error.

---

### Post by PsykoMantis on 2013-11-14
Ok i don't know why, but it's 8 if i run uname -rm... now i've rebooted and it was all ok before sudo make install!

**$ sudo make install**
```
  Building modules, stage 2.
  MODPOST 11 modules
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/compat/compat.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/drivers/net/wireless/rtlwifi/rtlwifi.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/net/mac80211/mac80211.ko
Can't read private key
  INSTALL /home/francesco/Scrivania/backports-3.11-rc3-1/net/wireless/cfg80211.ko
Can't read private key
  DEPMOD  3.8.0-33-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.

Your backported driver modules should be installed now.
Reboot.


```
[B]
$sudo modprobe rtl8188ee[/B] -> none


thank you very much...

---

### Post by chili555 on 2013-11-14
> $sudo modprobe rtl8188ee -> none

Is that what it actually says? Or does it say some other error? Or does it say this:> chili@Think410:~$ sudo modprobe rtl8188ee
[sudo] password for chili: 
chili@Think410:~$ 
If the command prompt simply pops back, that means the module was loaded without error or warning; exactly what we want! Confirm:```
lsmod | grep rtl
```Now proceed with the firmware step.

If there was some other error or message, please post it.

---

### Post by PsykoMantis on 2013-11-14
With *-> none* i meant that the command popped  back.

I've done the firmware step, now the light of the wifi appeared and here the result of
 
(BEFORE firmware step)
**lsmod | grep rtl**
```

rtl8188ee             137586  0 
rtlwifi               120562  1 rtl8188ee
mac80211              555015  2 rtl8188ee,rtlwifi
cfg80211              549566  2 rtlwifi,mac80211
compat                 15085  4 rtl8188ee,rtlwifi,mac80211,cfg80211


```

**dmesg | grep rtl**
```
[    9.414340] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[    9.600395] rtlwifi: Firmware rtlwifi/rtl8188efw.bin not available
[ 2416.454393] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[ 2416.458023] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 2416.458210] rtlwifi: wireless switch is on

```

Now i'm writing with my wi-fi on :P
in what title can i change this thread to help people find this discussion?

_**THANK YOU SO MUCH**_  you are a real kind soul!!!!

> ps
just because i want to learn and if i not disturb you too much, can you explain to me what we have done? and what was the problem and the right resolution? all this work wasn't really easy to understand to me!

---

### Post by chili555 on 2013-11-14
> 

Now i'm writing with my wi-fi on :P
in what title can i change this thread to help people find this discussion?

_**THANK YOU SO MUCH**_  you are a real kind soul!!!!Awesome! Glad it's working. I suggest you edit the title of the thread to [SOLVED]Realtek wireless 10ec:8179.

Please refer back to the link I gave you. Don't forget you will need to recompile after you reboot after each newer kernel version. Please retain the files and instructions for that time.

---

