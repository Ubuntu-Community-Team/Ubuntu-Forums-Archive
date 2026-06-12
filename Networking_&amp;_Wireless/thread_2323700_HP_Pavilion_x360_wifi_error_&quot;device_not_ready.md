---
title: "HP Pavilion x360 wifi error &quot;device not ready&quot;"
date: 2016-05-07
forum: Networking &amp; Wireless
---

### Post by scott131 on 2016-05-07
I have a new HP Pavilion x360 laptop running Ubuntu 16.04, updated with latest packages, including kernel "Linux x360-nix 4.4.0-22-generic #39-Ubuntu SMP Thu May 5 16:53:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux". 

Ethernet connection is working fine, but I can't get the wireless to work. As far as I can tell, the inbuilt wifi is being detected and drivers loaded, but is not in a state that is ready to be used. Network Manager applet has "device not ready" listed under Wi-Fi Networks.

Output from various commands below, please let me know if anything further is required. I'd certainly appreciate some assistance in getting this up and running.

```

$ sudo lshw -c network |grep DISABLED -A 20
  *-network DISABLED
       description: Wireless interface
       product: Wireless 3165
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 81
       serial: 08:d4:0c:99:dd:15
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-22-generic firmware=16.242414.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:317 memory:91200000-91201fff

```
```

$ dmesg |grep iwlwifi
[   16.192385] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2
[   16.193037] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2
[   16.193065] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-17.ucode failed with error -2
[   16.576685] iwlwifi 0000:03:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[   17.601398] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[   17.601514] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   17.601739] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   17.891836] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[   36.011574] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   36.011845] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   36.072393] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   36.072625] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  142.939854] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  142.940077] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  143.001462] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  143.001692] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  150.319588] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  150.320890] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  150.382150] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  150.382366] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  386.426614] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  386.426863] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  386.488035] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  386.488257] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  386.636991] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  386.637211] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  386.699429] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  386.699634] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  404.020539] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  404.020766] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  404.082631] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  404.082859] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled

```
```

$ lspci 
00:00.0 Host bridge: Intel Corporation Device 2280 (rev 21)
00:02.0 VGA compatible controller: Intel Corporation Device 22b1 (rev 21)
00:0b.0 Signal processing controller: Intel Corporation Device 22dc (rev 21)
00:13.0 SATA controller: Intel Corporation Device 22a3 (rev 21)
00:14.0 USB controller: Intel Corporation Device 22b5 (rev 21)
00:1a.0 Encryption controller: Intel Corporation Device 2298 (rev 21)
00:1b.0 Audio device: Intel Corporation Device 2284 (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 22c8 (rev 21)
00:1c.1 PCI bridge: Intel Corporation Device 22ca (rev 21)
00:1c.2 PCI bridge: Intel Corporation Device 22cc (rev 21)
00:1c.3 PCI bridge: Intel Corporation Device 22ce (rev 21)
00:1f.0 ISA bridge: Intel Corporation Device 229c (rev 21)
00:1f.3 SMBus: Intel Corporation Device 2292 (rev 21)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
03:00.0 Network controller: Intel Corporation Wireless 3165 (rev 81)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)

```
```

$ ifconfig
enp2s0    Link encap:Ethernet  HWaddr dc:4a:3e:aa:f8:e0  
          inet addr:172.24.0.16  Bcast:172.24.0.255  Mask:255.255.255.0
          inet6 addr: fe80::de4a:3eff:feaa:f8e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115221 errors:0 dropped:116 overruns:0 frame:0
          TX packets:68708 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:147403473 (147.4 MB)  TX bytes:5976657 (5.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4726 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4726 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:483997 (483.9 KB)  TX bytes:483997 (483.9 KB)

```
```

$ iwconfig
enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

---

### Post by jeremy31 on 2016-05-07
Welcome to the forum.  I think this may be one of the more common issues.  Check ```
lsmod | grep acer
```
If acer_wmi is in the output then ```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

If it doesn't work after the reboot see the wireless script link in my signature and post the results

---

### Post by scott131 on 2016-05-07
I was so close. I had previously blacklisted acer-wireless, without success. Blacklisting acer_wmi has fix the issue though - thank you very much!

---

