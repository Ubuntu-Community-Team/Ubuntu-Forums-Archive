---
title: "Ubuntu 16.04 WiFi Disconnects Randomly"
date: 2018-04-05
forum: Networking &amp; Wireless
---

### Post by alexkoganov on 2018-04-05
hi guys

from yesterday i have weird problem with my WiFi / Ethernet connections.
the wifi  Disconnects Randomly (but i can still ping to google ) and when i connecting the Ethernet cable after a couple of minutes
it disconnects and searching for WiFi networks :/  . 

from google searches it looks  lite a lot of people having the same problem but didn't found any reliable solution
(on windows i a lot easier to fix driver related problems but i am not turning back to my lovely Ubuntu :) ).

if it helps there is my lshw output:

 ```
 *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:02:00.1
       logical name: enp2s0f1
       version: 12
       serial: 10:c3:7b:ea:8d:f0
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:e000(size=256) memory:f7d14000-f7d14fff memory:f7d10000-f7d13fff
  *-network
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0f0
       version: 00
       serial: 54:35:30:cc:b5:73
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=4.13.0-38-generic firmware=0.37 ip=192.168.1.119 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:19 memory:f7c10000-f7c1ffff
```

thanks for your help

---

### Post by praseodym on 2018-04-05
Please show
```

iwconfig
iwlist chan
sudo iwlist scan
dmesg | grep rt2
```

---

### Post by alexkoganov on 2018-04-06
```
alex@alex-X550LA:~$ iwconfig 
enp0s20u1c4i2  no wireless extensions.


enp2s0f1  no wireless extensions.


lo        no wireless extensions.


vmnet1    no wireless extensions.


wlp3s0f0  IEEE 802.11  ESSID:"hotbiz"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 34:8A:AE:FF:2D:96   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:48  Invalid misc:339   Missed beacon:0

alex@alex-X550LA:~$ iwlist chan
enp0s20u1c4i2  no frequency information.


enp2s0f1  no frequency information.


lo        no frequency information.


vmnet1    no frequency information.


wlp3s0f0  14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)

alex@alex-X550LA:~$ sudo iwlist chan
enp0s20u1c4i2  no frequency information.


enp2s0f1  no frequency information.


lo        no frequency information.


vmnet1    no frequency information.


wlp3s0f0  14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)


alex@alex-X550LA:~$ dmesg | grep rt2
[    3.055703] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0013 detected
[    3.131983] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[    3.491752] rt2800pci 0000:03:00.0 wlp3s0f0: renamed from wlan0
[    4.305023] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[    4.306577] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[  136.278038] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1402.230238] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1403.158233] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1404.086260] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1405.078157] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1406.006143] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1406.934233] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1407.862142] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1408.790142] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1409.722209] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1410.654156] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1411.582186] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1412.518223] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1522.614039] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1523.542079] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1524.470012] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1525.398077] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1527.054075] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1642.613669] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1644.601664] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1882.216771] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1883.208690] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1884.200754] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1886.188749] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2002.944194] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2482.284011] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2483.212011] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2484.148001] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2485.075937] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2486.003964] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2486.935981] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2487.872048] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2488.800043] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2489.728040] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2490.655996] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2491.648004] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 2723.956736] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3082.284943] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3084.272901] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3085.268891] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3086.196899] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3531.884317] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3532.876326] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3772.563703] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 3773.491692] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4971.926500] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4972.854509] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4973.782522] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4974.710559] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4975.702516] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4976.630578] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4977.558529] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 4978.486521] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 5331.959870] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 9533.244762] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 9772.329529] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[11332.198584] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[12773.258748] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15891.350753] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15892.278732] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15893.210742] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15894.138776] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15895.070833] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15895.998782] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15896.926810] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15897.854799] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15898.782819] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15899.710850] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15960.283166] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15961.211108] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15962.871107] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15963.807145] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15964.739108] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15965.679123] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[15966.671131] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16003.291362] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16004.227327] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16005.163330] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16006.091408] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16007.019326] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16007.951330] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16008.879433] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16009.811485] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16010.739436] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16011.667392] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16012.595454] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16013.523419] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16014.451454] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16149.884110] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16150.812129] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16152.136118] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16373.345214] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16374.277222] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16375.269226] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16376.201216] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16492.677625] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16493.605652] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[16494.533651] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23692.376062] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23693.368121] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23694.296102] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23695.292099] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23696.220107] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23697.148116] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23698.080140] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23699.008102] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23699.936130] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23700.864090] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23754.979975] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23755.912024] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23756.843973] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23796.320228] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23797.252234] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23860.312495] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23861.240515] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23862.168504] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23863.096503] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23864.024546] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23864.952489] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23865.880574] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[23943.376969] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[24045.713486] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[24046.641461] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[24047.569500] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[24048.561508] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[24049.889511] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[24285.714616] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[24286.642692] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[24287.570634] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[24288.566673] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[24289.558638] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[24645.716401] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[24766.713009] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[24887.317601] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[25125.718820] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[25126.646859] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[25127.574832] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[25128.566867] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[25129.494877] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[25647.269102] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[25686.441752] Modules linked in: ipheth uas usb_storage bluetooth ecdh_generic vmnet(OE) vmw_vsock_vmci_transport vsock pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vmw_vmci vboxdrv(OE) vmmon(OE) ccm binfmt_misc nls_iso8859_1 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc uvcvideo arc4 videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core videodev media aesni_intel aes_x86_64 crypto_simd snd_soc_rt5640 rt2800pci glue_helper cryptd rt2800mmio snd_hda_codec_hdmi snd_soc_rl6231 rt2800lib snd_soc_core rt2x00pci snd_hda_codec_realtek intel_cstate snd_compress snd_hda_codec_generic ac97_bus snd_pcm_dmaengine intel_rapl_perf snd_seq_midi rt2x00mmio snd_hda_intel rt2x00lib snd_seq_midi_event joydev mac80211
[25767.370558] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[25887.371384] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26005.728440] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26007.728413] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26125.732565] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26126.664567] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26127.592555] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26128.520574] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26129.448588] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26130.376585] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26131.308567] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26132.236562] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26133.164591] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26134.092653] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26245.333124] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26247.333081] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26486.334734] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26487.262679] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26488.854717] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26605.730545] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26606.658546] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26607.586548] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26726.662308] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[26847.330373] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[27086.403032] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[27087.663045] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[27088.595079] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[27206.331635] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[27326.732227] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[27327.660199] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[27328.652231] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush


```
thanks

---

### Post by praseodym on 2018-04-06
Try this
```

echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf
```
Reboot and run
```

sudo modprobe -v rt2800pci
```

---

### Post by alexkoganov on 2018-04-07
Hi

After thise steps it killed my wifi completely (cant find any network)
So at the mean time i reversed it.

Any other idea?

Thanks

---

### Post by praseodym on 2018-04-07
```
sudo modprobe -v rt2800pci
```

did not reactivate it?!

---

### Post by kc1di on 2018-04-07
try this go to your favorite text editor (gedit) and open it as root.  Then navigate to this file. /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
in that file fine this line:```
wifi.powersave = 3
``` change the =3 to =2 and  save the file and reboot.  
See if that solves the disconnect problem.

---

### Post by wildmanne39 on 2018-04-07
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by alexkoganov on 2018-05-02
so i got fresh install of Ubuntu 18 and now its happening again ( none of the solutions above on 16.04).
why suddenly the driver is corrupted (or maybe its the hardware ? ) .
the most strange thing is that i still have ping to 8.8.8.8 but no access to any website :/ 

appreciate  your help guys.

---

### Post by alexkoganov on 2018-05-02
so i got fresh install of Ubuntu 18 and now its happening again ( none of the solutions above on 16.04).
why suddenly the driver is corrupted (or maybe its the hardware ? ) .
the most strange thing is that i still have ping to 8.8.8.8 but no access to any website :/ 

appreciate  your help guys.

---

### Post by alexkoganov on 2018-05-02
sorry for the double post.

take a look at my pic that i uploaded.

as you can see i still have layer 1-3 connection but layer 4-7 is dead :/.

what the hell is going on?

thanks

---

### Post by alexkoganov on 2018-05-03
Anyone?

---

