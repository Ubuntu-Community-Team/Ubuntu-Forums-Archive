---
title: "Broadcom 57762 Wired Network"
date: 2014-02-28
forum: Networking &amp; Wireless
---

### Post by markus9 on 2014-02-28
I tried to install a Ubuntu Server 13.10 install as base for a XBMC on my Intel NUC DC3217BY System.
Install used the wireless network Connection, but for full hd streaming i want to use wired network.

As this system has no builtin ethernet i connected a Apple thunderbolt to gbit ethernet device. It is detected as a broadcom 57762 device in lspci but i think that no driver is running for this device because ifconfig only shows the wifi connection and lo.

Is there any way to get this device running. Broadcom says that the driver should be part of the kernel, but it does not work.

Thank you for your help!

---

### Post by chili555 on 2014-02-28
You kept a secret of the best part! How about running:```
lspci -nn 
```Post the line about the thunderbolt to ethernet device. We need details!

---

### Post by markus9 on 2014-02-28
sorry, i am a total linux newbie... :-)

lspci -nn:

07:00.0 PCI bridge [0604]: Intel Corporation DSL3510 Thunderbolt Controller [Cactus Ridge] [8086:1549]
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57762 Gigabit Ethernet PCIe [14e4:1682]

ifconfig: (wlan is a Intel wireless lan mini pcie module)

lo        Link encap:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:65536  Metrik:1
          RX-Pakete:32 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:32 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX-Bytes:2480 (2.4 KB)  TX-Bytes:2480 (2.4 KB)
wlan0     Link encap:Ethernet  Hardware Adresse 24:77:03:18:0d:9c
          inet Adresse:192.168.1.147  Bcast:192.168.255.255  Maske:255.255.0.0
          inet6-Adresse: fe80::2677:3ff:fe18:d9c/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX-Pakete:248 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:169 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX-Bytes:22375 (22.3 KB)  TX-Bytes:30487 (30.4 KB)


There is one strange thing, there is a broadcom tg3 driver module loaded (from the broadcom website, installed with make install), lsmod lists it:
[EMAIL="xxx@xbmc-nuc:~$"]xxx@xbmc-nuc:~$[/EMAIL] lsmod
Module                  Size  Used by
ctr                    13193  2
ccm                    17856  2
nls_iso8859_1          12713  1
arc4                   12573  2
intel_rapl             19228  0
x86_pkg_temp_thermal    14269  0
intel_powerclamp       19031  0
iwldvm                243417  0
coretemp               17728  0
mac80211              654074  1 iwldvm
kvm_intel             144426  0
kvm                   468181  1 kvm_intel
i915                  816909  1
iwlwifi               179720  1 iwldvm
crct10dif_pclmul       14250  0
snd_hda_codec_hdmi     46898  1
snd_hda_intel          57222  0
crc32_pclmul           13160  0
snd_hda_codec         199156  2 snd_hda_codec_hdmi,snd_hda_intel
ghash_clmulni_intel    13259  0
snd_hwdep              13613  1 snd_hda_codec
cryptd                 20530  1 ghash_clmulni_intel
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
drm_kms_helper         53224  1 i915
drm                   308397  2 i915,drm_kms_helper
cfg80211              509407  3 iwlwifi,mac80211,iwldvm
snd_page_alloc         18798  2 snd_pcm,snd_hda_intel
snd_timer              30038  1 snd_pcm
i2c_algo_bit           13564  1 i915
microcode              23788  0
snd                    69754  6 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_hda_codec,snd_hda_intel
mei_me                 18578  0
soundcore              12680  1 snd
mei                    82749  1 mei_me
lpc_ich                21163  0
video                  19859  1 i915
mac_hid                13253  0
lp                     17799  0
parport                42481  1 lp
hid_generic            12548  0
usbhid                 53067  0
hid                   106254  2 hid_generic,usbhid
usb_storage            66714  3
tg3                   174880  0
ahci                   30063  0
ptp                    18980  1 tg3
libahci                32277  1 ahci
pps_core               19381  1 ptp

xxx[EMAIL="xxx@xbmc-nuc:~$"]@xbmc-nuc:~$[/EMAIL] modinfo tg3
filename:       /lib/modules/3.13.5-031305-generic/updates/tg3.ko
firmware:       tigon/tg3_tso5.bin
firmware:       tigon/tg3_tso.bin
firmware:       tigon/tg3.bin
version:        3.133d
license:        GPL
description:    Broadcom Tigon3 ethernet driver
author:         David S. Miller ([EMAIL="davem@redhat.com"]davem@redhat.com[/EMAIL]) and Jeff Garzik ([EMAIL="jgarzik@pobox.com"]jgarzik@pobox.com[/EMAIL])
srcversion:     AD5651827B21B625C2A2BE9
alias:          pci:v0000106Bd00001645sv*sd*bc*sc*i*
alias:          pci:v0000173Bd000003EAsv*sd*bc*sc*i*
alias:          pci:v0000173Bd000003EBsv*sd*bc*sc*i*
alias:          pci:v0000173Bd000003E9sv*sd*bc*sc*i*
alias:          pci:v0000173Bd000003E8sv*sd*bc*sc*i*
alias:          pci:v00001148d00004500sv*sd*bc*sc*i*
alias:          pci:v00001148d00004400sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B3sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B7sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001641sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001683sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001642sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016F3sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001643sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001687sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001686sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001682sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000165Fsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001657sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B6sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B2sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B4sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001682sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B0sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B5sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B1sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001656sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001665sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001655sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001691sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001694sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001690sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001692sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001692sv00001025sd00000612bc*sc*i*
alias:          pci:v000014E4d00001692sv00001025sd00000601bc*sc*i*
alias:          pci:v000014E4d000016A0sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001699sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001689sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001688sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001680sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001681sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000165Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001684sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001698sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001713sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001712sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016DDsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000166Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000166Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00001679sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001678sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001669sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001668sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000167Fsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001693sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001693sv000017AAsd00003056bc*sc*i*
alias:          pci:v000014E4d0000169Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000169Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00001674sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001673sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000167Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001672sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000167Asv*sd*bc*sc*i*
alias:          pci:v000014E4d000016FEsv*sd*bc*sc*i*
alias:          pci:v000014E4d000016FDsv*sd*bc*sc*i*
alias:          pci:v000014E4d000016F7sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001601sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001600sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000167Esv*sd*bc*sc*i*
alias:          pci:v000014E4d0000167Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001677sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001676sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000165Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00001659sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000166Esv*sd*bc*sc*i*
alias:          pci:v000014E4d00001649sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000170Esv*sd*bc*sc*i*
alias:          pci:v000014E4d0000170Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000169Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000169Csv*sd*bc*sc*i*
alias:          pci:v000014E4d00001696sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016C7sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016C6sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016A8sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016A7sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016A6sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000165Esv*sd*bc*sc*i*
alias:          pci:v000014E4d0000165Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001654sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001653sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000164Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001648sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001647sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001646sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001645sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001644sv*sd*bc*sc*i*
depends:        ptp
vermagic:       3.13.5-031305-generic SMP mod_unload modversions
parm:           tg3_debug:Tigon3 bitmapped debugging message enable value (int)
parm:           tg3_disable_eee:Disable Energy Efficient Ethernet (EEE) support (int)

---

### Post by chili555 on 2014-02-28
> alias: pci:v0000[COLOR="#FF0000"]14E4[/COLOR]d0000[COLOR="#FF0000"]1682[/COLOR]sv*sd*bc*sc*i*As you can see, the driver tg3 claims your device. Let's see if the logs tell us why it isn't working as expected:```
dmesg | grep -e tg3 -e eth
```Thanks.

---

### Post by markus9 on 2014-02-28
[EMAIL="xxx@xbmc-nuc:~$"]xxx@xbmc-nuc:~$[/EMAIL] dmesg | grep -e tg3 -e eth
[    1.979374] tg3.c:v3.134 (Sep 16, 2013)
[    2.048162] tg3 0000:08:00.0 eth0: Tigon3 [partno(BCM957762) rev 57766000] (PCI Express) MAC address 68:5b:35:ac:36:0f
[    2.049123] tg3 0000:08:00.0 eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    2.050092] tg3 0000:08:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.051048] tg3 0000:08:00.0 eth0: dma_rwctrl[00000001] dma_mask[64-bit]

Switch LEDs are on for the port...

---

### Post by chili555 on 2014-02-28
> tg3 0000:08:00.0 [COLOR="#FF0000"]eth0[/COLOR]: Tigon3 [partno(BCM957762)This suggests you have a wireless interface eth0. If you ask the wireless to disconnect from Network Manager, and attach the ethernet, do you get an eth0?```
ifconfig
```And does it at least try to connect?

---

### Post by markus9 on 2014-02-28
the two network adapters don't like each other... :-)

as soon as i disabled wlan0 - sudo ifconfig wlan0 down - i saw a new device named p9p1 in ifconfig

after ifconfig wlan0 up the new device p9p1 is gone again.

Because i don't really need wifi anyway i will remove the wlan card.
After configuring the device p9p1 in /etc/network/interfaces everything works fine.
I didnt try disconnecting the device in network manager as you suggested, i dont know that command (or is it a gui tool)? 
I have no gui installed (Ubuntu server installation), just a naked system as base for installing a slightly customized xbmc setup ([http://forum.xbmc.org/showthread.php?tid=165707](http://forum.xbmc.org/showthread.php?tid=165707))

Thank you very much for your help!

---

### Post by chili555 on 2014-02-28
Glad it's working by whatever means! Enjoy your NUC!

---

