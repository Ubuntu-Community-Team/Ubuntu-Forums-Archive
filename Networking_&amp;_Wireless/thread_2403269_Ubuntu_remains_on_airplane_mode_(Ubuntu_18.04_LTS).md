---
title: "Ubuntu remains on airplane mode (Ubuntu 18.04 LTS) on startup"
date: 2018-10-09
forum: Networking &amp; Wireless
---

### Post by heryckluiz on 2018-10-09
I hope you guys help me,

Every time i start up my laptop, it remains on airplane mode and its persistent, 

i've make some searchs (like this [https://ubuntuforums.org/showthread.php?t=2392109&highlight=start+airplane+mode](https://ubuntuforums.org/showthread.php?t=2392109&highlight=start+airplane+mode)) and doesnt work.

the only solution that works is press the hardware button during the boot and in some point it works (like now).

rfkill doesnt work either.

---

### Post by DuckHook on 2018-10-09
*Thread moved to **Networking & Wireless** as the more appropriate forum.*

---

### Post by superkid333 on 2018-10-10
I would like to see the output of "rfkill list all" if you can. If your wifi device shows "hard block: yes" then you need to try to turn it on using a hardware switch. 

Depending on your computer it may be Fn + F11, F12 or another Function key. It may be turned off in bios, so check that. 

I just went through the same issue, and posted a possible solution here, but it may be specific to my machine:
[https://ubuntuforums.org/showthread.php?t=2403364](https://ubuntuforums.org/showthread.php?t=2403364)

We probably need to see the output of a few commands to determine the computer you're using and the network card/driver. 

if you can show us:
lsmod
lspci
sudo lshw -C network

That will give us a decent starting ground.

---

### Post by heryckluiz on 2018-10-10
hi, good evening.

thanks for your time and help.

Follow as you request:

```
                         rfkill list all
 [sudo] senha para heryck:  
 0: phy0: Wireless LAN
     Soft blocked: no
     Hard blocked: yes

  
```

```
lsmod
 Module                  Size  Used by
 snd_hda_codec_hdmi     49152  1
 uvcvideo               86016  0
 videobuf2_vmalloc      16384  1 uvcvideo
 videobuf2_memops       16384  1 videobuf2_vmalloc
 videobuf2_v4l2         24576  1 uvcvideo
 videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
 videodev              184320  3 uvcvideo,videobuf2_core,videobuf2_v4l2
 media                  40960  2 uvcvideo,videodev
 intel_rapl             20480  0
 x86_pkg_temp_thermal    16384  0
 intel_powerclamp       16384  0
 coretemp               16384  0
 kvm                   598016  0
 irqbypass              16384  1 kvm
 crct10dif_pclmul       16384  0
 crc32_pclmul           16384  0
 ghash_clmulni_intel    16384  0
 pcbc                   16384  0
 aesni_intel           188416  0
 aes_x86_64             20480  1 aesni_intel
 crypto_simd            16384  1 aesni_intel
 glue_helper            16384  1 aesni_intel
 cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
 intel_cstate           20480  0
 intel_rapl_perf        16384  0
 snd_hda_codec_realtek   106496  1
 snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
 arc4                   16384  2
 snd_hda_intel          40960  4
 snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
 ath9k                 151552  0
 snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
 snd_hwdep              20480  1 snd_hda_codec
 ath9k_common           36864  1 ath9k
 hp_wmi                 16384  0
 ath9k_hw              471040  2 ath9k,ath9k_common
 snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
 sparse_keymap          16384  1 hp_wmi
 ath                    28672  3 ath9k_hw,ath9k,ath9k_common
 snd_seq_midi           16384  0
 wmi_bmof               16384  0
 snd_seq_midi_event     16384  1 snd_seq_midi
 input_leds             16384  0
 mac80211              778240  1 ath9k
 joydev                 24576  0
 snd_rawmidi            32768  1 snd_seq_midi
 serio_raw              16384  0
 snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              32768  2 snd_seq,snd_pcm
 cfg80211              622592  4 mac80211,ath9k,ath,ath9k_common
 snd                    81920  19 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
 lpc_ich                24576  0
 mei_me                 40960  0
 mei                    90112  1 mei_me
 shpchp                 36864  0
 soundcore              16384  1 snd
 soc_button_array       16384  0
 hp_wireless            16384  0
 mac_hid                16384  0
 sch_fq_codel           20480  2
 parport_pc             36864  0
 ppdev                  20480  0
 lp                     20480  0
 parport                49152  3 lp,parport_pc,ppdev
 ip_tables              28672  0
 x_tables               40960  1 ip_tables
 autofs4                40960  2
 hid_generic            16384  0
 usbhid                 49152  0
 i915                 1617920  10
 i2c_algo_bit           16384  1 i915
 drm_kms_helper        172032  1 i915
 syscopyarea            16384  1 drm_kms_helper
 sysfillrect            16384  1 drm_kms_helper
 sysimgblt              16384  1 drm_kms_helper
 fb_sys_fops            16384  1 drm_kms_helper
 psmouse               147456  0
 drm                   401408  5 i915,drm_kms_helper
 ahci                   36864  1
 libahci                32768  1 ahci
 r8169                  86016  0
 mii                    16384  1 r8169
 wmi                    24576  2 wmi_bmof,hp_wmi
 i2c_hid                20480  0
 hid                   118784  3 i2c_hid,hid_generic,usbhid
 video                  45056  1 i915
  
```

```
lspci
 00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
 00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
 00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
 00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
 00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
 00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
 00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
 00:1c.1 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 2 (rev e4)
 00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
 00:1c.5 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 6 (rev e4)
 00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
 00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
 00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
 00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
 08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
 09:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
  
```

```
                          *-network                  
        descrição: Ethernet interface
        produto: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
        fabricante: Realtek Semiconductor Co., Ltd.
        ID físico: 0
        informações do barramento: pci@0000:08:00.0
        nome lógico: enp8s0
        versão: 07
        serial: 8c:dc:d4:c2:de:3a
        tamanho: 10Mbit/s
        capacidade: 100Mbit/s
        largura: 64 bits
        clock: 33MHz
        capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuração: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
        recursos: irq:41 porta de E/S:3000(tamanho=256) memória:b2600000-b2600fff memória:b2400000-b2403fff
   *-network DESABILITADO
        descrição: Interface sem fio
        produto: AR9485 Wireless Network Adapter
        fabricante: Qualcomm Atheros
        ID físico: 0
        informações do barramento: pci@0000:09:00.0
        nome lógico: wlo1
        versão: 01
        serial: 5c:c9:d3:46:25:3c
        largura: 64 bits
        clock: 33MHz
        capacidades: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
        configuração: broadcast=yes driver=ath9k driverversion=4.15.0-36-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
        recursos: irq:16 memória:b2500000-b257ffff memória:b2580000-b258ffff
  
```

so, can you help me?

---

### Post by heryckluiz on 2018-10-15
up

---

