---
title: "Atheros QCA9377 n/w properly on Lenovo ideapad"
date: 2017-01-04
forum: Networking &amp; Wireless
---

### Post by crew-j on 2017-01-04
Running Ubuntu 16.04.1 on new Lenovo 510S notebook. 

Internal wifi works fine on Windows. However, under Ubuntu was slow and losing connection, so forced to use external wifi adaptor (RALINK/Edimax) which works fine. 

In virgin state, system showed both Wifi adaptors as expected under wireless, but after attempted remedial action now have Ralink running but pretending to be direct ethernet connection (up down arrow as if tethered). Appear to have clobbered wifi configuration. 

Previously followed various threads this forum and elsewhere seemingly similar to mine. Result in first case was to disable all wifi, and requiring restore of entire system to resolve. I don't have sufficient knowledge of how the elements of the networking software link together to repair what I had done. 

Now (after updating lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin) Atheros is non operational and is greyed out in wifi options. Update was from github not from linux.org.

wireless-info script does not show anything to the relatively uninitiated, and too big to attach, but could possibly ftp if required. 

This is the second machine bought recently with wifi nightmares due to lack of hardware support in Linux.

---

### Post by crew-j on 2017-01-04
Not sure how or why, but it has now started working normally? Will it last?

---

### Post by slickymaster on 2017-01-04
> **crew-j said:**
> <---snip--->
wireless-info script does not show anything to the relatively uninitiated, and too big to attach, but could possibly ftp if required.
<---snip--->

Use [http://pastebin.com/](http://pastebin.com/) to past the content of the wireless-info script.

---

### Post by trundlenut on 2017-01-04
I have the same wireless card in my ideapad 310 and I also have problems with disconnections and slow speeds.  Currently I only get 6mb/s when my other laptop is showing 200+mb/s on the same network.

dmesg shows some apparent issues:

```
[    9.506875] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    9.992206] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   11.968756] ath10k_pci 0000:02:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 17aa:4035) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[   11.968760] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   12.009277] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[ 1459.886263] ath10k_pci 0000:02:00.0: failed to receive scan abortion completion: timed out
[ 1459.886289] ath10k_pci 0000:02:00.0: failed to abort scan: -110
[ 1559.028322] ath10k_pci 0000:02:00.0: failed to stop wmi scan: -11
[ 1559.028337] ath10k_pci 0000:02:00.0: failed to stop scan: -11
[ 1559.028344] ath10k_pci 0000:02:00.0: failed to start hw scan: -110
[ 1563.028384] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1567.028428] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1571.028557] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1575.028616] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1579.028680] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1583.028800] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1587.029274] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1591.028958] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1595.028514] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1599.028674] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1603.028928] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1607.029288] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1611.029372] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1615.029452] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1619.029255] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1623.029199] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1627.029700] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1631.029381] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1635.029869] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1639.029954] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1643.029578] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1647.030122] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1651.029798] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1655.029878] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1659.030370] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1663.030446] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1667.030521] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1671.030604] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1675.030695] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1678.030768] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1681.030818] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1685.030901] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1689.030792] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1693.030640] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1697.030656] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1701.030905] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1705.031067] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1709.031198] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1713.030934] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1717.031537] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1721.031642] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1725.031228] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1729.031352] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1733.031360] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1737.031441] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1741.035577] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1745.035652] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1749.035815] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1753.035897] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1757.035980] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1761.035976] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1765.036086] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1769.036230] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[ 1772.112701] ath10k_pci 0000:02:00.0: failed to delete WMI vdev 1: -11
[ 1775.112755] ath10k_pci 0000:02:00.0: failed to set inactivity time for vdev 0: -11
[ 1775.112768] ath10k_pci 0000:02:00.0: failed to setup powersave: -11
[ 1778.112819] ath10k_pci 0000:02:00.0: failed to set inactivity time for vdev 0: -11
[ 1778.112832] ath10k_pci 0000:02:00.0: failed to setup powersave: -11
[ 1781.112887] ath10k_pci 0000:02:00.0: failed to set PS Mode 0 for vdev 0: -11
[ 1781.112900] ath10k_pci 0000:02:00.0: failed to setup powersave: -11
[ 1781.112908] ath10k_pci 0000:02:00.0: failed to setup ps on vdev 0: -11
[ 1786.112980] ath10k_pci 0000:02:00.0: failed to flush transmit queue (skip 0 ar-state 1): 0
[ 1789.113053] ath10k_pci 0000:02:00.0: failed to install key for vdev 0 peer 20:a6:80:b0:a8:60: -11
[ 1792.113107] ath10k_pci 0000:02:00.0: failed to delete peer 20:a6:80:b0:a8:60 for vdev 0: -11
[ 1792.113188] Modules linked in: drbg ansi_cprng ctr ccm rfcomm msr bnep binfmt_misc nls_iso8859_1 arc4 rtsx_usb_ms memstick uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common videodev media btusb btrtl snd_soc_skl snd_soc_skl_ipc snd_hda_ext_core snd_soc_sst_ipc snd_soc_sst_dsp snd_soc_core snd_compress ac97_bus snd_pcm_dmaengine dw_dmac_core snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic intel_rapl x86_pkg_temp_thermal snd_hda_intel intel_powerclamp snd_hda_codec snd_hda_core coretemp snd_hwdep kvm_intel snd_pcm kvm ath10k_pci snd_seq_midi ath10k_core snd_seq_midi_event ath snd_rawmidi irqbypass snd_seq mac80211 snd_seq_device crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_timer aesni_intel cfg80211 hci_uart snd aes_x86_64 lrw soundcore btbcm
[ 1792.114064]  [<ffffffffc05653c2>] ? ath10k_config+0x42/0x90 [ath10k_core]
[ 1795.113190] ath10k_pci 0000:02:00.0: failed to recalculate rts/cts prot for vdev 0: -11
[ 1798.113238] ath10k_pci 0000:02:00.0: failed to set protection mode 0 on vdev 0: -11
[ 1801.113299] ath10k_pci 0000:02:00.0: failed to set erp slot for vdev 0: -11
[ 1804.113378] ath10k_pci 0000:02:00.0: failed to set preamble for vdev 0: -11
[ 1807.113419] ath10k_pci 0000:02:00.0: faield to down vdev 0: -11
[ 1810.113504] ath10k_pci 0000:02:00.0: failed to submit vdev param txbf 0x0: -11
[ 1810.113518] ath10k_pci 0000:02:00.0: failed to recalc txbf for vdev 0: -11
[ 1813.113567] ath10k_pci 0000:02:00.0: failed to set vdev wmm params on vdev 0: -11
[ 1816.113081] ath10k_pci 0000:02:00.0: failed to set vdev wmm params on vdev 0: -11
[ 1819.113670] ath10k_pci 0000:02:00.0: failed to set vdev wmm params on vdev 0: -11
[ 1822.113291] ath10k_pci 0000:02:00.0: failed to set vdev wmm params on vdev 0: -11
[ 1825.113798] ath10k_pci 0000:02:00.0: failed to stop WMI vdev 0: -11
[ 1825.113812] ath10k_pci 0000:02:00.0: failed to stop vdev 0: -11
[ 1830.113894] ath10k_pci 0000:02:00.0: failed to flush transmit queue (skip 0 ar-state 1): 0
[ 1833.113564] ath10k_pci 0000:02:00.0: failed to delete WMI vdev 0: -11
[ 1833.113578] ath10k_pci 0000:02:00.0: removing stale peer 20:a6:80:b0:a8:60 from vdev_id 0
[ 1839.113960] ath10k_pci 0000:02:00.0: could not suspend target (-11)
```

The firmware seems to be the latest version.

Below is the pastebin link for the output from the wireless-info script (I have sanitised the SSIDs)

[http://pastebin.com/s6v0GfeP](http://pastebin.com/s6v0GfeP)

---

### Post by jeremy31 on 2017-01-04
I would try ```
sudo apt-get install --reinstall linux-firmware
```
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Shutdown and do a cold boot

---

### Post by trundlenut on 2017-01-04
> **jeremy31 said:**
> I would try ```
sudo apt-get install --reinstall linux-firmware
```
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Shutdown and do a cold boot

Does the second command turn off power saving for the wifi card?  I'm not great with sed, so does it just substitute 2 for 3 in effect?

---

### Post by jeremy31 on 2017-01-05
Yes it does turn powersave off by changing 3 to 2

---

### Post by trundlenut on 2017-01-05
> **jeremy31 said:**
> I would try ```
sudo apt-get install --reinstall linux-firmware
```
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Shutdown and do a cold boot

unfortunately that didn't make any difference to the speed, still stuck at 6mb/s.  But i seem to have less gumpf in dmesg:

```
[   10.753470] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   11.136559] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   13.221695] ath10k_pci 0000:02:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 17aa:4035) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[   13.221697] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   13.267089] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0

```

---

### Post by jeremy31 on 2017-01-05
Can you change the encryption for the wifi router to WPA2 only with no TKIP

---

### Post by trundlenut on 2017-01-05
> **jeremy31 said:**
> Can you change the encryption for the wifi router to WPA2 only with no TKIP


I will give it a go tomorrow.  I will also try connecting to the wireless at work and see if it is any different.

---

### Post by trundlenut on 2017-01-08
I've tried changing to WPA2 and AES and it has made no difference, still stuck at 6mb/s.

Also tried the wireless at work, standing next to the AP I got a thundering 1mb/s...

---

### Post by jeremy31 on 2017-01-08
I wonder if the bit rate can be changed
```
sudo iwconfig wlp2s0 rate auto
```

It may help to go into Network Manager settings for the wireless connection and set IPv6 to off or ignore

---

### Post by trundlenut on 2017-01-08
> **jeremy31 said:**
> I wonder if the bit rate can be changed
```
sudo iwconfig wlp2s0 rate auto
```

It may help to go into Network Manager settings for the wireless connection and set IPv6 to off or ignore

Unfortunately no difference.

---

### Post by jeremy31 on 2017-01-09
Are you doing any speedtests online or just going by what iwconfig shows?

---

### Post by trundlenut on 2017-01-09
> **jeremy31 said:**
> Are you doing any speedtests online or just going by what iwconfig shows?

I've tried using speedtest.net, which gave me a speed of 5.98mb/s, so I'm believing iwconfig.

Running it on my phone gives ~20mb/s.

---

### Post by trundlenut on 2017-01-09
OK, now weirdness ensues.  Just tried speedtest.net again and I'm getting 20mb/s!

So is what iwconfig reports wrong?

---

