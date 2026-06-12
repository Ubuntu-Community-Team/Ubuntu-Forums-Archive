---
title: "Can't connect to wifi"
date: 2016-11-26
forum: Networking &amp; Wireless
---

### Post by thomas-sablik on 2016-11-26
Hi,

I can't connect to my wifi with Xubuntu 16.04. I use an Acer Aspire E5-573-54HH with Qualcomm Atheros QCA9377 Wireless Network Adapter. I tried to connect with Network Manager and it's asking repeatedly for the password. So I tried Wicd. When I try to connect I get the error message that the password is wrong. Until yesterday I had Windows 10 on this laptop and it worked perfectly. How can I get more information and solve this problem?

Until Ubuntu 15.10 there were problems with the wifi adapter and the firmware. The user had to install it manually. With Ubuntu 16.04 it should be installed directly so that I can find my network with properties like channel and security settings but I can't connect. Even if I set the securtiy to none and try to connect I can see in Wicd that there is an unsecured network and password is wrong. Strange.

Finally I tried an Edimax Wifi USB Stick and it works. But I prefer to use my intern wifi card.

```
$ iwconfig
 wlp3s0    IEEE 802.11abgn  ESSID:off/any  
           Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
           Retry short limit:7   RTS thr:off   Fragment thr:off
           Power Management:on

 enp2s0    no wireless extensions.

 lo        no wireless extensions.

 wlx801f02e4a8fd  IEEE 802.11bgn  ESSID:"Gljja"  
           Mode:Managed  Frequency:2.432 GHz  Access Point: 00:17:9A:6F:FC:FB   
           Bit Rate=54 Mb/s   Tx-Power=20 dBm   
           Retry short limit:7   RTS thr=2347 B   Fragment thr:off
           Power Management:off
           Link Quality=42/70  Signal level=-68 dBm  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:3714   Missed beacon:0

 $ dmesg | grep wlp3s0
 [   16.973819] ath10k_pci 0000:03:00.0 wlp3s0: renamed from wlan0
 [   23.974863] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
 [   25.886916] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
 [   29.998944] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
 [   62.996019] wlp3s0: authenticate with 00:17:9a:6f:fc:fb
 [   63.039736] wlp3s0: send auth to 00:17:9a:6f:fc:fb (try 1/3)
 [   63.041261] wlp3s0: authenticated
 [   63.041408] ath10k_pci 0000:03:00.0 wlp3s0: disabling HT as WMM/QoS is not supported by the AP
 [   63.041412] ath10k_pci 0000:03:00.0 wlp3s0: disabling VHT as WMM/QoS is not supported by the AP
 [   63.042042] wlp3s0: associate with 00:17:9a:6f:fc:fb (try 1/3)
 [   63.044123] wlp3s0: RX AssocResp from 00:17:9a:6f:fc:fb (capab=0x431 status=0 aid=5)
 [   63.045580] wlp3s0: associated
 [   63.045612] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
 [   66.731076] wlp3s0: disassociated from 00:17:9a:6f:fc:fb (Reason: 3)
 [   74.658881] wlp3s0: authenticate with 00:17:9a:6f:fc:fb
 [   74.701802] wlp3s0: send auth to 00:17:9a:6f:fc:fb (try 1/3)
 [   74.703335] wlp3s0: authenticated
 [   74.703501] ath10k_pci 0000:03:00.0 wlp3s0: disabling HT as WMM/QoS is not supported by the AP
 [   74.703504] ath10k_pci 0000:03:00.0 wlp3s0: disabling VHT as WMM/QoS is not supported by the AP
 [   74.705913] wlp3s0: associate with 00:17:9a:6f:fc:fb (try 1/3)
 [   74.707983] wlp3s0: RX AssocResp from 00:17:9a:6f:fc:fb (capab=0x431 status=0 aid=5)
 [   74.709876] wlp3s0: associated
 [   77.884261] wlp3s0: disassociated from 00:17:9a:6f:fc:fb (Reason: 3)
 [   80.430329] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready

 $ dmesg | grep wlx801f02e4a8fd
 [   99.498664] rtl8192cu 2-2:1.0 wlx801f02e4a8fd: renamed from wlan0
 [   99.529120] IPv6: ADDRCONF(NETDEV_UP): wlx801f02e4a8fd: link is not ready
 [   99.924207] IPv6: ADDRCONF(NETDEV_UP): wlx801f02e4a8fd: link is not ready
 [   99.961862] IPv6: ADDRCONF(NETDEV_UP): wlx801f02e4a8fd: link is not ready
 [  118.058355] wlx801f02e4a8fd: authenticate with 00:17:9a:6f:fc:fb
 [  118.080625] wlx801f02e4a8fd: send auth to 00:17:9a:6f:fc:fb (try 1/3)
 [  118.099749] wlx801f02e4a8fd: authenticated
 [  118.099934] rtl8192cu 2-2:1.0 wlx801f02e4a8fd: disabling HT as WMM/QoS is not supported by the AP
 [  118.099939] rtl8192cu 2-2:1.0 wlx801f02e4a8fd: disabling VHT as WMM/QoS is not supported by the AP
 [  118.101826] wlx801f02e4a8fd: associate with 00:17:9a:6f:fc:fb (try 1/3)
 [  118.205854] wlx801f02e4a8fd: associate with 00:17:9a:6f:fc:fb (try 2/3)
 [  118.247341] wlx801f02e4a8fd: RX AssocResp from 00:17:9a:6f:fc:fb (capab=0x431 status=0 aid=5)
 [  118.347487] wlx801f02e4a8fd: associated
 [  118.347496] IPv6: ADDRCONF(NETDEV_CHANGE): wlx801f02e4a8fd: link becomes ready

 $ dmesg | grep ath10k[   13.823372] ath10k_pci 0000:03:00.0: pci irq msi interrupts 1 irq_mode 0 reset_mode 0
 [   14.546304] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
 [   16.653947] ath10k_pci 0000:03:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 11ad:0806) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
 [   16.653955] ath10k_pci 0000:03:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
 [   16.973819] ath10k_pci 0000:03:00.0 wlp3s0: renamed from wlan0
 [   63.041408] ath10k_pci 0000:03:00.0 wlp3s0: disabling HT as WMM/QoS is not supported by the AP
 [   63.041412] ath10k_pci 0000:03:00.0 wlp3s0: disabling VHT as WMM/QoS is not supported by the AP
 [   66.846535] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [   66.846829] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [   67.051342] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [   67.153714] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [   67.256116] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [   67.358519] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [   68.236463] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [   68.382577] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [   68.484971] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [   68.587389] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [   74.703501] ath10k_pci 0000:03:00.0 wlp3s0: disabling HT as WMM/QoS is not supported by the AP
 [   74.703504] ath10k_pci 0000:03:00.0 wlp3s0: disabling VHT as WMM/QoS is not supported by the AP
 [   78.007234] ath10k_warn: 12 callbacks suppressed
 [   78.007248] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [   79.544039] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [   79.646432] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [   79.748817] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [   79.851341] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [   79.851477] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [   80.058047] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [  108.727056] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [  363.692698] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [ 3072.853880] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [ 3261.599501] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [ 4080.691326] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [ 4521.829086] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
 [ 4836.667286] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
```

---

