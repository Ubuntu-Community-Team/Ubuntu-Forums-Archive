---
title: "[Ubuntu 14.04] Hotspot created, cannot connect to it"
date: 2014-12-18
forum: Networking &amp; Wireless
---

### Post by OmegaBowser on 2014-12-18
Hi,

I'm running on Ubuntu 14.04 32-bit on my laptop HP Elitebook 8540p, connected to Internet by Ethernet.
Since I don't have any router at home, I used to use my PC as a router on Windows (which worked without any problem). 
But since I've passed on Linux, I cannot see or even connect manually to the hotspot I created with the Ubuntu "network-manager".
I've followed many tutorials, with and without command lines, none of them gave me any success...

I don't know what to do know, do you have any advice ?

Thanks you! :)

---

### Post by sbnwl on 2014-12-18
Hope you come across [this]("http://ubuntuforums.org/showthread.php?t=2165035") also..
Report back if it works...

---

### Post by OmegaBowser on 2014-12-18
Hi sbnwl, thanks for the answer.
When I try to launch ap-hotspot, I'm obtaining this message:
"***Your wireless card or driver does not support Access Point mode***"

****But what I don't understand, is that I **CAN** create hotspot on Windows. Isn't it using AP mode too?

---

### Post by sbnwl on 2014-12-18
That's strange. Which wireless card is this?

Tell the output of:
```
lspci | grep ireless
```

and this:
```
uname -a
```

and this also:
```
cat /etc/lsb-release
```

---

### Post by OmegaBowser on 2014-12-18
> lspci | grep ireless

Don't you mean "grep wireless"? For both of these, it ***returns absolutely nothing***.

> uname -a

"***Linux omegabowser-HP-EliteBook-8540p 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:44 UTC 2014 i686 i686 i686 GNU/Linux***" 

> cat /etc/lsb-release

"
***DISTRIB_ID=Ubuntu******DISTRIB_RELEASE=14.04***
***DISTRIB_CODENAME=trusty***
[I][B]DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"
[/B][/I]"

I just tested again on Windows with Connectify, it's all success, hotspot created and connected with my tablet and smartphone. (Both Samsung Galaxy)

---

### Post by sbnwl on 2014-12-19
> Don't you mean "grep wireless"? For both of these, it ***returns absolutely nothing***.

I meant it for Wireless/wireless both..

Okay get the output of:
```
lspci
```

And this also:
```
sudo lshw -c network
```

Also look into:
```
lsmod
```

---

### Post by OmegaBowser on 2014-12-19
> lspci

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GT216M [NVS 5100M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation GT216 HDMI Audio Controller (rev a1)
44:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
45:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
46:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 06)
46:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 25)
46:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 14)
46:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 14)
46:06.4 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev bb)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```


> [COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -c network[/FONT][/COLOR]

```
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: b4:99:ba:e4:c3:45
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.12-3 ip=193.11.106.227 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:51 memory:d7500000-d751ffff memory:d752a000-d752afff ioport:6020(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:44:00.0
       logical name: wlan0
       version: 35
       serial: 18:3d:a2:2c:43:b4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-43-generic firmware=9.221.4.1 build 25532 ip=10.42.0.1 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:53 memory:d3300000-d3301fff

```

> lsmod

```
Module                  Size  Used byipt_MASQUERADE         12760  1 
xt_conntrack           12664  1 
ipt_REJECT             12485  2 
xt_tcpudp              12756  4 
iptable_filter         12706  1 
nf_nat_h323            17419  0 
nf_conntrack_h323      62817  1 nf_nat_h323
nf_nat_pptp            12926  0 
nf_nat_proto_gre       12865  1 nf_nat_pptp
nf_conntrack_pptp      14628  1 nf_nat_pptp
nf_conntrack_proto_gre    14021  1 nf_conntrack_pptp
nf_nat_tftp            12420  0 
nf_conntrack_tftp      12953  1 nf_nat_tftp
nf_nat_sip             16997  0 
nf_conntrack_sip       23655  1 nf_nat_sip
nf_nat_irc             12606  0 
nf_conntrack_irc       13249  1 nf_nat_irc
nf_nat_ftp             12645  0 
nf_conntrack_ftp       14056  1 nf_nat_ftp
iptable_nat            12867  1 
nf_conntrack_ipv4      14492  2 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_nat_ipv4            13095  1 iptable_nat
nf_nat                 20861  10 nf_nat_ftp,nf_nat_irc,nf_nat_sip,ipt_MASQUERADE,nf_nat_proto_gre,nf_nat_h323,nf_nat_ipv4,nf_nat_pptp,nf_nat_tftp,iptable_nat
nf_conntrack           83685  19 nf_nat_ftp,nf_nat_irc,nf_nat_sip,nf_conntrack_proto_gre,ipt_MASQUERADE,nf_nat,nf_nat_h323,nf_nat_ipv4,nf_nat_pptp,nf_nat_tftp,xt_conntrack,nf_conntrack_ftp,nf_conntrack_irc,nf_conntrack_sip,iptable_nat,nf_conntrack_h323,nf_conntrack_ipv4,nf_conntrack_pptp,nf_conntrack_tftp
ip_tables              17987  2 iptable_filter,iptable_nat
x_tables               22067  6 ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ipt_REJECT
pci_stub               12550  1 
vboxpci                22896  0 
vboxnetadp             25636  0 
vboxnetflt             27291  0 
vboxdrv               299807  3 vboxnetadp,vboxnetflt,vboxpci
dm_crypt               22589  0 
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm
binfmt_misc            13140  1 
pata_pcmcia            16945  1 
arc4                   12536  2 
snd_hda_codec_hdmi     45440  4 
iwldvm                214950  0 
mac80211              546051  1 iwldvm
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
videodev              108503  2 uvcvideo,videobuf2_core
hp_wmi                 13702  0 
mxm_wmi                12893  0 
sparse_keymap          13708  1 hp_wmi
intel_powerclamp       14239  0 
coretemp               13195  0 
kvm_intel             132651  0 
kvm                   388310  1 kvm_intel
pcmcia                 51828  1 pata_pcmcia
crc32_pclmul           12967  0 
aesni_intel            18156  0 
aes_i586               16995  1 aesni_intel
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
gf128mul               14503  2 lrw,xts
ablk_helper            13357  1 aesni_intel
cryptd                 15578  1 ablk_helper
r852                   17722  0 
joydev                 17101  0 
sm_common              16772  1 r852
snd_seq_midi           13132  0 
snd_hda_codec_idt      48978  1 
snd_seq_midi_event     14475  1 snd_seq_midi
nand                   58760  2 r852,sm_common
nand_ecc               13136  1 nand
serio_raw              13230  0 
snd_rawmidi            25135  1 snd_seq_midi
nand_bch               13067  1 nand
nvidia               9704610  51 
bch                    17197  1 nand_bch
intel_ips              18217  0 
snd_hda_intel          42730  5 
iwlwifi               152049  1 iwldvm
yenta_socket           40201  0 
snd_hda_codec         164067  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
lpc_ich                16864  0 
r592                   17711  0 
pcmcia_rsrc            18319  1 yenta_socket
snd_hwdep              13272  1 snd_hda_codec
nand_ids                8547  1 nand
cfg80211              409394  3 iwlwifi,mac80211,iwldvm
mtd                    52813  2 nand,sm_common
snd_pcm                85501  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
memstick               16174  1 r592
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
mei_me                 18195  0 
snd_timer              28584  2 snd_pcm,snd_seq
drm                   244037  2 nvidia
mei                    66737  1 mei_me
snd                    60939  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
wmi                    18673  2 hp_wmi,mxm_wmi
tpm_infineon           17164  0 
hp_accel               25756  0 
parport_pc             31981  1 
mac_hid                13037  0 
lis3lv02d              19500  1 hp_accel
input_polldev          13648  1 lis3lv02d
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47070  0 
hid                    87604  2 hid_generic,usbhid
e1000e                223034  0 
psmouse                91357  0 
ahci                   25579  2 
firewire_ohci          35529  0 
libahci                27214  1 ahci
sdhci_pci              18535  0 
firewire_core          61867  1 firewire_ohci
ptp                    18445  1 e1000e
sdhci                  37779  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
pps_core               18799  1 ptp
video                  18903  0 



```

---

### Post by sbnwl on 2014-12-19
I fear the old problem has not been addressed yet in the new kernel.

[http://askubuntu.com/questions/319838/failed-to-set-interface-wlan0-into-ap-mode-intel-centrino-n1000-wireless](http://askubuntu.com/questions/319838/failed-to-set-interface-wlan0-into-ap-mode-intel-centrino-n1000-wireless)
[http://askubuntu.com/questions/477057/wifi-hotspot-configuration](http://askubuntu.com/questions/477057/wifi-hotspot-configuration)

Cannot say much for now.

---

