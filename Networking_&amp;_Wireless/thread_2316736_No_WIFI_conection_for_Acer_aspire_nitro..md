---
title: "No WIFI conection for Acer aspire nitro."
date: 2016-03-10
forum: Networking &amp; Wireless
---

### Post by Johyn on 2016-03-10
Greetings all!

Here's the trouble, as stated above: nothin is displayed on the network apart from a useles 'windows' conection... I should mention that I'm on a workin wireless dungle and that I'm conectin thxs to a dual boot with window. Now, I'm unable to get the 'wireless info', no conection :???:, but I managed all that, if that may help:


```
johyn@johyn-Aspire-VN7-791G:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu DISTRIB_RELEASE=14.04 DISTRIB_CODENAME=trusty DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"


```
```
johyn@johyn-Aspire-VN7-791G:~$
lsusb
 Bus 004 Device 002: ID 8087:8000 Intel Corp. Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 003 Device 002: ID 8087:8008 Intel Corp. Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub Bus 001 Device 005: ID 04f2:b469 Chicony Electronics Co., Ltd Bus 001 Device 004: ID 06cb:7406 Synaptics, Inc. Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller Bus 001 Device 006: ID 04ca:3011 Lite-On Technology Corp. Bus 001 Device 002: ID 045e:0797 Microsoft Corp. Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub johyn@johyn-Aspire-VN7-791G:~$ lspci 00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06) 00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06) 00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06) 00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06) 00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05) 00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04) 00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05) 00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05) 00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5) 00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5) 00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05) 00:1f.0 ISA bridge: Intel Corporation HM86 Express LPC Controller (rev 05) 00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05) 00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05) 01:00.0 3D controller: NVIDIA Corporation Device 139a (rev a2) 07:00.0 Network controller: Qualcomm Atheros Device 003e (rev 20) 08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01) 

```
 
```
johyn@johyn-Aspire-VN7-791G:~$
lspci -k
 00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06) Subsystem: Acer Incorporated [ALI] Device 091d 00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06) Kernel driver in use: pcieport 00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06) Subsystem: Acer Incorporated [ALI] Device 091d Kernel driver in use: i915 00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06) Subsystem: Acer Incorporated [ALI] Device 091d Kernel driver in use: snd_hda_intel 00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05) Subsystem: Acer Incorporated [ALI] Device 091d Kernel driver in use: xhci_hcd 00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04) Subsystem: Acer Incorporated [ALI] Device 091d Kernel driver in use: mei_me 00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05) Subsystem: Acer Incorporated [ALI] Device 091d Kernel driver in use: ehci-pci 00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05) Subsystem: Acer Incorporated [ALI] Device 091d Kernel driver in use: snd_hda_intel 00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
Kernel driver in use: pcieport 00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5) Kernel driver in use: pcieport 00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05) Subsystem: Acer Incorporated [ALI] Device 091d Kernel driver in use: ehci-pci 00:1f.0 ISA bridge: Intel Corporation HM86 Express LPC Controller (rev 05) Subsystem: Acer Incorporated [ALI] Device 091d Kernel driver in use: lpc_ich 00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05) Subsystem: Acer Incorporated [ALI] Device 091d Kernel driver in use: ahci 00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05) Subsystem: Acer Incorporated [ALI] Device 091d 01:00.0 3D controller: NVIDIA Corporation Device 139a (rev a2) Subsystem: Acer Incorporated [ALI] Device 091d Kernel driver in use: nouveau 07:00.0 Network controller: Qualcomm Atheros Device 003e (rev 20) Subsystem: Lite-On Communications Inc Device 0804 08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01) Subsystem: Acer Incorporated [ALI] Device 091d Kernel driver in use: tg3 

```

```
johyn@johyn-Aspire-VN7-791G:~$ 
sudo lshw -C network
 [sudo] password for johyn:   *-network UNCLAIMED            description: Network controller       product: Qualcomm Atheros       vendor: Qualcomm Atheros       physical id: 0       bus info: pci@0000:07:00.0       version: 20       width: 64 bits       clock: 33MHz       capabilities: pm msi pciexpress cap_list       configuration: latency=0       resources: memory:d1400000-d15fffff  *-network       description: Ethernet interface       product: NetLink BCM57780 Gigabit Ethernet PCIe       vendor: Broadcom Corporation       physical id: 0       bus info: pci@0000:08:00.0       logical name: eth0       version: 01       serial: 30:65:ec:85:58:e2       size: 10Mbit/s       capacity: 1Gbit/s       width: 64 bits
       clock: 33MHz       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s       resources: irq:33 memory:d1600000-d160ffff 


```
```
johyn@johyn-Aspire-VN7-791G:~$ lsmod 
Module                  Size  Used by snd_hda_codec_hdmi     53248  1 snd_hda_codec_realtek    81920  1 snd_hda_codec_generic    69632  1 snd_hda_codec_realtek rtsx_usb_ms            20480  0 memstick               20480  1 rtsx_usb_ms joydev                 20480  0 acer_wmi               20480  0 sparse_keymap          16384  1 acer_wmi snd_seq_midi           16384  0 snd_seq_midi_event     16384  1 snd_seq_midi snd_hda_intel          32768  5 snd_rawmidi            32768  1 snd_seq_midi snd_hda_controller     32768  1 snd_hda_intel snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_cont roller snd_hwdep              20480  1 snd_hda_codec snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller intel_rapl             20480  0 iosf_mbi               16384  1 intel_rapl x86_pkg_temp_thermal    16384  0 intel_powerclamp       20480  0 coretemp               16384  0 kvm_intel             151552  0 kvm                   479232  1 kvm_intel crct10dif_pclmul       16384  0 uvcvideo               90112  0 crc32_pclmul           16384  0 ghash_clmulni_intel    16384  0 videobuf2_vmalloc      16384  1 uvcvideo videobuf2_memops       16384  1 videobuf2_vmalloc videobuf2_core         53248  1 uvcvideo v4l2_common            16384  1 videobuf2_core videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core media                  24576  2 uvcvideo,videodev aesni_intel           172032  1 snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi aes_x86_64             20480  1 aesni_intel snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi lrw                    16384  1 aesni_intel snd_timer              32768  2 snd_pcm,snd_seq gf128mul               16384  1 lrw glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper i915                 1048576  4 hid_multitouch         20480  0 snd                    86016  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmid i,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device serio_raw              16384  0 nouveau              1368064  1 btusb                  40960  0 mei_me                 20480  0 mei                    90112  1 mei_me mxm_wmi                16384  1 nouveau lpc_ich                24576  0 ttm                    94208  1 nouveau drm_kms_helper        126976  2 i915,nouveau soundcore              16384  2 snd,snd_hda_codec drm                   344064  8 ttm,i915,drm_kms_helper,nouveau shpchp                 40960  0 ie31200_edac           16384  0 edac_core              53248  1 ie31200_edac i2c_algo_bit           16384  2 i915,nouveau wmi                    20480  3 acer_wmi,mxm_wmi,nouveau video                  20480  3 i915,acer_wmi,nouveau soc_button_array       16384  0 mac_hid                16384  0 rfcomm                 69632  8 bnep                   20480  2 bluetooth             491520  22 bnep,btusb,rfcomm nls_iso8859_1          16384  1 parport_pc             32768  0 ppdev                  20480  0 lp                     20480  0 parport                45056  3 lp,ppdev,parport_pc rtsx_usb_sdmmc         28672  0 rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms hid_generic            16384  0 usbhid                 53248  0 hid                   110592  3 hid_multitouch,hid_generic,usbhid broadcom               20480  0 tg3                   167936  0 ahci                   36864  3 ptp                    20480  1 tg3 libahci                32768  1 ahci pps_core               20480  1 ptp 


```

```
johyn@johyn-Aspire-VN7-791G:~$
 ifconfigncap:Ethernet  HWaddr 30:65:ec:85:58:e2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1          RX packets:0 errors:0 dropped:0 overruns:0 frame:0          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 txqueuelen:1000           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)          Interrupt:19 
lo        Link encap:Local Loopback            inet addr:127.0.0.1  Mask:255.0.0.0          inet6 addr: ::1/128 Scope:Host          UP LOOPBACK RUNNING  MTU:65536  Metric:1          RX packets:177 errors:0 dropped:0 overruns:0 frame:0          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 txqueuelen:0           RX bytes:12753 (12.7 KB)  TX bytes:12753 (12.7 KB)


```
```
johyn@johyn-Aspire-VN7-791G:~$
 sudo iwlist scan
 eth0      Interface doesn't support scanning.
lo        Interface doesn't support scanning.

```

```
johyn@johyn-Aspire-VN7-791G:~$
 uname -r -m
3.19.0-25-generic x86_64 johyn@johyn-Aspire-VN7-791G:~$ cat /etc/network/interfaces # interfaces(5) file used by ifup(8) and ifdown(8) auto lo iface lo inet loopback johyn@johyn-Aspire-VN7-791G:~$ nm-tool
NetworkManager Tool
State: disconnected
- Device: eth0 ----------------------------------------------------------------  Type:              Wired  Driver:            tg3  State:             unavailable  Default:           no  HW Address:        30:65:EC:85:58:E2
  Capabilities:    Carrier Detect:  yes
  Wired Properties    Carrier:         off

```

```
johyn@johyn-Aspire-VN7-791G:~$
 sudo rfkill list ft blocked: no Hard blocked: no 1: acer-wireless: Wireless LAN Soft blocked: no Hard blocked: no
```

---

### Post by tonip2 on 2016-04-18
Hi Johyn, 

You can try this:
[http://askubuntu.com/questions/66142...s-168c003e-dev]("http://askubuntu.com/questions/661424/ubuntu-14-04-wireless-not-working-no-network-interface-atheros-168c003e-dev")

---

### Post by Bucky Ball on 2016-04-18
That link requires that you be online to perform the steps. If there is anyway to get online with a cable please do so as no matter how you go about fixing this, getting online with a cable is probably going to make the job a lot easier.

Getting online will also make it much easier for us to help you as your terminal output is not holding format in the code tags and is difficult to work out ...

---

### Post by utnubu4 on 2016-04-19
This may solve the issue and it does not require an internet connection [https://wiki.archlinux.org/index.php?title=Network_configuration&redirect=no#Broadcom_BCM57780](https://wiki.archlinux.org/index.php?title=Network_configuration&redirect=no#Broadcom_BCM57780)

---

### Post by Bucky Ball on 2016-04-19
> **utnubu4 said:**
> This may solve the issue and it does not require an internet connection [https://wiki.archlinux.org/index.php?title=Network_configuration&redirect=no#Broadcom_BCM57780](https://wiki.archlinux.org/index.php?title=Network_configuration&redirect=no#Broadcom_BCM57780)

Ok, let's make this clear. The OP is looking for help with wireless on Ubuntu. You have provided a link to get wired working in Arch Linux. :-k

See below. The wireless card is unclaimed and unused, no driver installed. This is a rough translation of the original poster's code from 'sudo lshw -C network'.

```
*-network UNCLAIMED
            description: Network controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 20       width: 64 bits       clock: 33MHz
       capabilities: pm msi pciexpress cap_list       configuration: latency=0
       resources: memory:d1400000-d15fffff  *-network
```

Hopefully we are now all on the same page. :)

---

