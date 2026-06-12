---
title: "Monitor mode on Intel 7260  wireless card"
date: 2014-04-03
forum: Networking &amp; Wireless
---

### Post by jason72 on 2014-04-03
Hello, I’m trying to enable monitor mode on my device so I can monitor 802.11AC networks. I have an intel 7260 card. I was initially running saucy, but following output is from the trusty beta to make sure any kernel/driver updates were present.
I have installed airmon-ng, and start it up, but listening to the mon0 interface only yields broadcast packets and does not actually behave as expected for monitor mode. I am in a building with many wireless devices and know that there should be traffic on these channels.
This is the result of about 5 minutes of capture. For  a working card I typically receive several thousand packets bound to/from 30+ different mobile stations in this time-frame.


```
ubuntu-studio@ubuntu-studio:~$ sudo airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
2429    avahi-daemon
2431    avahi-daemon
3104    NetworkManager
3580    wpa_supplicant
3986    dhclient


Interface    Chipset        Driver

wlan0        Unknown     iwlwifi - [phy0]
                (monitor mode enabled on mon0)

ubuntu-studio@ubuntu-studio:~$ iwconfig
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.

mon0      IEEE 802.11abgn  Mode:Monitor  Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

eth1      no wireless extensions.

ubuntu-studio@ubuntu-studio:~$ sudo tshark -i mon0
tshark: Lua: Error during loading:
 [string "/usr/share/wireshark/init.lua"]:46: dofile has been disabled due to running Wireshark as superuser. See http://wiki.wireshark.org/CaptureSetup/CapturePrivileges for help in running Wireshark as an unprivileged user.
Running as user "root" and group "root". This could be dangerous.
Capturing on 'mon0'
  1   0.000000 Cisco-Li -> Broadcast    802.11 90 Beacon frame, SN=2405, FN=0, Flags=........, BI=100, SSID=linksys
1   2   0.007804 Cisco -> Broadcast    802.11 271 Beacon frame, SN=173, FN=0, Flags=........, BI=100, SSID=ssid1
  3   0.032392 Cisco -> Broadcast    802.11 265 Beacon frame, SN=174, FN=0, Flags=........, BI=100, SSID=ssid2
  4   0.224276 Cisco -> Broadcast    802.11 324 Beacon frame, SN=597, FN=0, Flags=........, BI=102, SSID=ssid3
4   5   0.756221 Cisco -> Broadcast    802.11 328 Beacon frame, SN=3951, FN=0, Flags=........, BI=102, SSID=ssid1
  6   0.780475 Cisco -> Broadcast    802.11 326 Beacon frame, SN=3952, FN=0, Flags=........, BI=102, SSID=ssid3
6   7   3.126922 Cisco -> Broadcast    802.11 271 Beacon frame, SN=3669, FN=0, Flags=........, BI=100, SSID=ssid3
7   8   3.151498 Cisco -> Broadcast    802.11 273 Beacon frame, SN=3670, FN=0, Flags=........, BI=100, SSID=ssid1
  9   3.176067 Cisco -> Broadcast    802.11 267 Beacon frame, SN=3671, FN=0, Flags=........, BI=100, SSID=ssid2
 10   3.229300 Cisco -> Broadcast    802.11 271 Beacon frame, SN=3672, FN=0, Flags=........, BI=100, SSID=ssid3
10  11  63.015129 Cisco -> Broadcast    802.11 269 Beacon frame, SN=653, FN=0, Flags=........, BI=100, SSID=ssid3
 12  63.205734 Cisco -> Broadcast    802.11 321 Beacon frame, SN=2421, FN=0, Flags=........, BI=102, SSID=ssid3
 13  63.224836 Cisco -> Broadcast    802.11 323 Beacon frame, SN=3259, FN=0, Flags=........, BI=102, SSID=ssid1
13  14  66.104436 Cisco -> Broadcast    802.11 271 Beacon frame, SN=1462, FN=0, Flags=........, BI=100, SSID=ssid3
 15  66.128992 Cisco -> Broadcast    802.11 273 Beacon frame, SN=1463, FN=0, Flags=........, BI=100, SSID=ssid1
 16  66.153578 Cisco -> Broadcast    802.11 267 Beacon frame, SN=1464, FN=0, Flags=........, BI=100, SSID=ssid2
16  17 126.017227 Cisco -> Broadcast    802.11 271 Beacon frame, SN=2842, FN=0, Flags=........, BI=100, SSID=ssid1
17  18 126.207284 Cisco -> Broadcast    802.11 323 Beacon frame, SN=1559, FN=0, Flags=........, BI=102, SSID=ssid1
 19 126.231862 Cisco -> Broadcast    802.11 321 Beacon frame, SN=1560, FN=0, Flags=........, BI=102, SSID=ssid3
19  20 129.106530 Cisco -> Broadcast    802.11 273 Beacon frame, SN=3342, FN=0, Flags=........, BI=100, SSID=ssid1
20  21 129.131091 Cisco -> Broadcast    802.11 267 Beacon frame, SN=3343, FN=0, Flags=........, BI=100, SSID=ssid2
 22 129.184352 Cisco -> Broadcast    802.11 271 Beacon frame, SN=3344, FN=0, Flags=........, BI=100, SSID=ssid3
22  23 189.226108 Cisco -> Broadcast    802.11 320 Beacon frame, SN=1952, FN=0, Flags=........, BI=102, SSID=ssid2
23  24 189.238872 Cisco -> Broadcast    802.11 318 Beacon frame, SN=3954, FN=0, Flags=........, BI=102, SSID=ssid4
24  25 192.108616 Cisco -> Broadcast    802.11 267 Beacon frame, SN=1103, FN=0, Flags=........, BI=100, SSID=ssid2
25  26 192.161846 Cisco -> Broadcast    802.11 271 Beacon frame, SN=1104, FN=0, Flags=........, BI=100, SSID=ssid3
 27 192.186442 Cisco -> Broadcast    802.11 273 Beacon frame, SN=1105, FN=0, Flags=........, BI=100, SSID=ssid1
27 ^C
ubuntu-studio@ubuntu-studio:~$ 
```



I have tested this with other wireless cards (the intel 6250) also using the iwlwifi driver and have successfully enabled monitor mode, so I suspect that the issue lies either with this card or with the firmware for it. Since there are two firmware versions for the 7260 (iwlwifi-7260-ucode-22.1.7.0.tgz and iwlwifi-7260-ucode-22.24.8.0.tgz), I attempted to use the most recent one that comes with trusty. These appear in the /lib/firmware as iwlwifi-7260-7.ucode and iwlwifi-7260-8.ucode. I moved the iwlwifi-7260-7.ucode file out of /lib/firmware and unloaded and reloaded iwlwifi and rebooted, but this does not appear to have pulled in the iwlwifi-7260-8.ucode file according to modinfo, but it does according to lshw, which is odd.
 
 Does anybody know how to resolve this? Has anybody else had issues with monitor mode on this card? Thank you very much for your time!




from trusty:
kernel / driver stuff:
```

ubuntu-studio@ubuntu-studio:~$ ls /lib/firmware/
3.13.0-12-lowlatency      dsp56k                       iwlwifi-3945-2.ucode           myri10ge_rss_eth_z8e.dat  tehuti
3com                      dvb-fe-xc5000-1.6.114.fw     iwlwifi-4965-2.ucode           NPE-B                     ti_3410.fw
acenic                    dvb-usb-dib0700-1.20.fw      iwlwifi-5000-5.ucode           NPE-C                     ti_5052.fw
adaptec                   dvb-usb-terratec-h5-drxk.fw  iwlwifi-5150-2.ucode           ositech                   ti-connectivity
advansys                  ea                           iwlwifi-6000-4.ucode           phanfw.bin                tigon
agere_ap_fw.bin           edgeport                     iwlwifi-6000g2a-5.ucode        ql2100_fw.bin             tlg2300_firmware.bin
agere_sta_fw.bin          emi26                        iwlwifi-6000g2a-6.ucode        ql2200_fw.bin             ttusb-budget
amd-ucode                 emi62                        iwlwifi-6000g2b-6.ucode        ql2300_fw.bin             ueagle-atm
ar3k                      ene-ub6250                   iwlwifi-6050-5.ucode           ql2322_fw.bin             usbdux
ar5523.bin                ess                          iwlwifi-7260-8.ucode           ql2400_fw.bin             usbduxfast_firmware.bin
asihpi                    f2255usb.bin                 kaweth                         ql2500_fw.bin             usbdux_firmware.bin
ath10k                    go7007                       keyspan                        r128                      usbduxsigma_firmware.bin
ath3k-1.fw                GPL-3                        keyspan_pda                    radeon                    v4l-cx231xx-avcore-01.fw
ath6k                     hp                           korg                           README                    v4l-cx23418-apu.fw
atmel_at76c504_2958.bin   htc_7010.fw                  lbtf_usb.bin                   rp2.fw                    v4l-cx23418-cpu.fw
atmel_at76c504a_2958.bin  htc_9271.fw                  lgs8g75.fw                     rt2561.bin                v4l-cx23418-dig.fw
atmsar11.fw               i2400m-fw-usb-1.4.sbcf       libertas                       rt2561s.bin               v4l-cx2341x-dec.fw
av7110                    i2400m-fw-usb-1.5.sbcf       Makefile                       rt2661.bin                v4l-cx2341x-enc.fw
bnx2x                     i6050-fw-usb-1.5.sbcf        matrox                         rt2860.bin                v4l-cx2341x-init.mpg
brcm                      intel                        moxa                           rt2870.bin                v4l-cx23885-avcore-01.fw
carl9170-1.fw             ipw2100-1.3.fw               mrvl                           rt3070.bin                v4l-cx25840.fw
carl9170fw                ipw2100-1.3-i.fw             mt7650.bin                     rt3090.bin                v4l-pvrusb2-24xxx-01.fw
cbfw-3.2.1.1.bin          ipw2100-1.3-p.fw             mts_cdma.fw                    rt3290.bin                v4l-pvrusb2-29xxx-01.fw
cbfw-3.2.3.0.bin          ipw2200-bss.fw               mts_edge.fw                    rt73.bin                  vicam
cis                       ipw2200-ibss.fw              mts_gsm.fw                     RTL8192E                  vntwusb.fw
configure                 ipw2200-sniffer.fw           mts_mt9234mu.fw                rtl_nic                   vxge
cpia2                     isci                         mts_mt9234zba.fw               rtlwifi                   WHENCE.ubuntu
ct2fw-3.2.1.1.bin         iwlwifi-1000-5.ucode         mwl8k                          s2250.fw                  whiteheat.fw
ct2fw-3.2.3.0.bin         iwlwifi-100-5.ucode          myri10ge_eth_big_z8e.dat       s2250_loader.fw           whiteheat_loader.fw
ctefx.bin                 iwlwifi-105-6.ucode          myri10ge_ethp_big_z8e.dat      s5p-mfc                   wsm_22.bin
ctfw-3.2.1.1.bin          iwlwifi-135-6.ucode          myri10ge_ethp_z8e.dat          sb16                      yam
ctfw-3.2.3.0.bin          iwlwifi-2000-6.ucode         myri10ge_eth_z8e.dat           scripts                   yamaha
ctspeq.bin                iwlwifi-2030-6.ucode         myri10ge_rss_eth_big_z8e.dat   sdd_sagrad_1091_1098.bin  zd1201-ap.fw
cxgb3                     iwlwifi-3160-7.ucode         myri10ge_rss_ethp_big_z8e.dat  slicoss                   zd1201.fw
cxgb4                     iwlwifi-3160-8.ucode         myri10ge_rss_ethp_z8e.dat      sun                       zd1211

ubuntu-studio@ubuntu-studio:~$ lsmod
Module                  Size  Used by
iwlmvm                172662  0 
snd_hda_codec_realtek    50963  1 
snd_hda_codec_hdmi     45303  1 
snd_hda_intel          42689  5 
mac80211              558429  1 iwlmvm
iwlwifi               152049  1 iwlmvm
cfg80211              423695  3 iwlwifi,mac80211,iwlmvm


ubuntu-studio@ubuntu-studio:~$ modinfo iwlwifi 
filename:       /lib/modules/3.13.0-12-lowlatency/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     9512E1F8D11CCA18336043F
alias:          pci:v00008086d0000095Asv*sd00005490bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005290bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005590bc*sc*i*
    .
    .
    .
    <I removed a page of aliases for brevity>
    .
    .
    .
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-12-lowlatency SMP preempt mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        CB:08:57:CE:87:B3:DD:9D:90:8E:E6:5A:DD:03:A2:55:A2:8A:72:64
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

ubuntu-studio@ubuntu-studio:~$ uname -a
Linux ubuntu-studio 3.13.0-12-lowlatency #32-Ubuntu SMP PREEMPT Fri Feb 21 18:12:35 UTC 2014 i686 i686 i686 GNU/Linux

ubuntu-studio@ubuntu-studio:~$ sudo lshw | grep wireless
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless logical
                configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-12-lowlatency firmware=22.24.8.0 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn


ubuntu-studio@ubuntu-studio:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty
```

---

### Post by excetara2 on 2014-09-28
Did you ever figure anything out? I am struggling to get monitor mode working on my Asus ux301 which also uses the same intel wireless card.

Thanks,

---

### Post by wildmanne39 on 2014-09-28
> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed. You can probably get help on the kali forum or aircrack forum.

Thread closed!

---

