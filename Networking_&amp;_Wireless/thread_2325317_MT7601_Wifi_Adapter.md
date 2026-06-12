---
title: "MT7601 Wifi Adapter"
date: 2016-05-21
forum: Networking &amp; Wireless
---

### Post by jmumby on 2016-05-21
Hi,

I am trying to get this dongle to work. My Ubuntu version is 16.04 and the Kernel should support the adapter out of the box. 

```
lsusb
Bus 001 Device 043: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter
```

```
iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
```

```
modinfo mt7601u
filename:       /lib/modules/4.4.6-ti-r15/kernel/drivers/net/wireless/mediatek/mt7601u/mt7601u.ko
license:        GPL
firmware:       mt7601u.bin
alias:          usb:v7392p7710d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2A5Fp1000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2955p1001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2955p0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2717p4106d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3D04d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp760Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp760Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp760Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp760Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp7601d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3434d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3431d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E8Dp760Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E8Dp760Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17D3d*dc*dsc*dp*ic*isc*ip*in*
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.6-ti-r15 SMP mod_unload modversions ARMv7 thumb2 p2v8 
```

```
dmesg(sample)
[ 2638.359013] mt7601u 1-1:1.0: Warning: unsupported EEPROM version 0d
[ 2638.359066] mt7601u 1-1:1.0: EEPROM ver:0d fae:00
[ 2638.524157] mt7601u 1-1:1.0: Error: RX urb failed:-71
[ 2638.529526] mt7601u 1-1:1.0: Error: submit URB dir:128 ep:1 failed:-19
[ 2638.553896] usb 1-1: USB disconnect, device number 102
[ 2638.900862] usb 1-1: new high-speed USB device number 103 using musb-hdrc
[ 2639.040340] usb 1-1: New USB device found, idVendor=148f, idProduct=7601
[ 2639.040396] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2639.040427] usb 1-1: Product: 802.11 n WLAN
[ 2639.040457] usb 1-1: Manufacturer: MediaTek
[ 2639.040484] usb 1-1: SerialNumber: 1.0
[ 2639.164996] usb 1-1: reset high-speed USB device number 103 using musb-hdrc
[ 2639.296008] mt7601u 1-1:1.0: ASIC revision: 76010001 MAC revision: 76010500
[ 2639.301701] mt7601u 1-1:1.0: Firmware Version: 0.1.00 Build: 7640 Build time: 201302052146____
[ 2639.667397] mt7601u 1-1:1.0: Warning: unsupported EEPROM version 0d
[ 2639.667452] mt7601u 1-1:1.0: EEPROM ver:0d fae:00
[ 2639.826527] mt7601u 1-1:1.0: Error: RX urb failed:-71
[ 2639.831797] mt7601u 1-1:1.0: Error: RX urb failed:-71
[ 2639.836956] mt7601u 1-1:1.0: Error: RX urb failed:-71
[ 2639.842109] mt7601u 1-1:1.0: Error: RX urb failed:-71
[ 2639.847261] mt7601u 1-1:1.0: Error: RX urb failed:-71
[ 2639.852525] mt7601u 1-1:1.0: Error: RX urb failed:-71
[ 2639.857684] mt7601u 1-1:1.0: Error: RX urb failed:-71
[ 2639.862837] mt7601u 1-1:1.0: Error: RX urb failed:-71
[ 2639.868047] mt7601u 1-1:1.0: Error: RX urb failed:-71
[ 2639.873203] mt7601u 1-1:1.0: Error: RX urb failed:-71
[ 2639.878354] mt7601u 1-1:1.0: Error: RX urb failed:-71
[ 2639.883508] mt7601u 1-1:1.0: Error: RX urb failed:-71
[ 2639.888659] mt7601u 1-1:1.0: Error: RX urb failed:-71
[ 2639.893809] mt7601u 1-1:1.0: Error: RX urb failed:-71
[ 2639.907434] mt7601u 1-1:1.0: Error: submit URB dir:128 ep:1 failed:-19
[ 2639.933578] usb 1-1: USB disconnect, device number 103
[ 2640.212944] usb 1-1: new high-speed USB device number 104 using musb-hdrc
[ 2640.352044] usb 1-1: New USB device found, idVendor=148f, idProduct=7601
[ 2640.352077] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2640.352093] usb 1-1: Product: 802.11 n WLAN
[ 2640.352107] usb 1-1: Manufacturer: MediaTek
[ 2640.352122] usb 1-1: SerialNumber: 1.0
[ 2640.472999] usb 1-1: reset high-speed USB device number 104 using musb-hdrc
[ 2640.603417] mt7601u 1-1:1.0: ASIC revision: 76010001 MAC revision: 76010500
[ 2640.604572] mt7601u 1-1:1.0: Firmware Version: 0.1.00 Build: 7640 Build time
```

```
lsmod
Module                  Size  Used by
mt7601u                75508  0
mac80211              484852  1 mt7601u
cfg80211              417677  2 mac80211,mt7601u
rfkill                 18226  2 cfg80211
snd_soc_simple_card     8385  0
omap_aes               13081  0
omap_sham              21371  0
omap_rng                4423  0
rng_core                7471  1 omap_rng
usb_f_ecm               9400  1
g_ether                 4976  0
spi_omap2_mcspi        10764  0
usb_f_rndis            22191  2 g_ether
u_ether                11917  3 usb_f_ecm,usb_f_rndis,g_ether
libcomposite           43461  3 usb_f_ecm,usb_f_rndis,g_ether
snd_soc_davinci_mcasp    16318  2
snd_soc_edma            1290  1 snd_soc_davinci_mcasp
snd_soc_omap            3058  1 snd_soc_davinci_mcasp
snd_soc_hdmi_codec      5842  1
snd_soc_core          155592  5 snd_soc_hdmi_codec,snd_soc_davinci_mcasp,snd_soc_edma,snd_soc_omap,snd_soc_simple_card
snd_pcm_dmaengine       5209  2 snd_soc_core,snd_soc_omap
snd_pcm                82689  5 snd_soc_hdmi_codec,snd_soc_davinci_mcasp,snd_soc_core,snd_soc_omap,snd_pcm_dmaengine
snd_timer              19720  1 snd_pcm
snd                    59559  3 snd_soc_core,snd_timer,snd_pcm
soundcore               7601  1 snd
evdev                  10695  2
uio_pdrv_genirq         3539  0
uio                     8822  1 uio_pdrv_genirq
tilcdc                 26364  0
tda998x                12754  0
```

The driver just doesn't seem to bind to the hardware.

Any suggestions to further troubleshoot?

Thanks

---

### Post by howefield on 2016-05-21
Thread moved to the "*Networking & Wireless*" for a better fit and code tags added.

---

