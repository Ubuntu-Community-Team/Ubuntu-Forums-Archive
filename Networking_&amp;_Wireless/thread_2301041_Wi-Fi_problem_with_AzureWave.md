---
title: "Wi-Fi problem with AzureWave"
date: 2015-10-30
forum: Networking &amp; Wireless
---

### Post by andriy2 on 2015-10-30
AzureWave AW-GE703H RTL8187se. Give me a list of available wifi hotspots, but doesn't connect me to them  (It is trying to connect, but it always says that password is bad).  Ubuntu 15.10 live cd. Anybody help :roll: dmesg gives a following answer. 
```
[   43.373713] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   43.377652] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   43.380818] sky2 0000:04:00.0 enp4s0: enabling interface
[   43.381346] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   43.774930] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   45.212228] sky2 0000:04:00.0 enp4s0: Link is up at 100 Mbps, full duplex, flow control rx
[   45.212300] IPv6: ADDRCONF(NETDEV_CHANGE): enp4s0: link becomes ready
[   63.236562] Bluetooth: RFCOMM TTY layer initialized
[   63.236578] Bluetooth: RFCOMM socket layer initialized
[   63.236590] Bluetooth: RFCOMM ver 1.11
[  107.779898] wlp2s0: authenticate with 00:14:6c:92:7f:d6
[  107.891149] wlp2s0: send auth to 00:14:6c:92:7f:d6 (try 1/3)
[  107.892852] wlp2s0: authenticated
[  107.893155] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[  107.893165] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  107.893171] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[  107.895254] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 1/3)
[  108.099319] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 2/3)
[  108.303502] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 3/3)
[  108.507572] wlp2s0: association with 00:14:6c:92:7f:d6 timed out
[  110.033527] wlp2s0: authenticate with 00:14:6c:92:7f:d6
[  110.144678] wlp2s0: send auth to 00:14:6c:92:7f:d6 (try 1/3)
[  110.146353] wlp2s0: authenticated
[  110.146664] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[  110.146675] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  110.146683] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[  110.148566] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 1/3)
[  110.352777] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 2/3)
[  110.556888] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 3/3)
[  110.760949] wlp2s0: association with 00:14:6c:92:7f:d6 timed out
[  112.695033] wlp2s0: authenticate with 00:14:6c:92:7f:d6
[  112.810372] wlp2s0: send auth to 00:14:6c:92:7f:d6 (try 1/3)
[  112.812079] wlp2s0: authenticated
[  112.812322] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[  112.812329] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  112.812334] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[  112.814264] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 1/3)
[  113.018506] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 2/3)
[  113.222593] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 3/3)
[  113.426705] wlp2s0: association with 00:14:6c:92:7f:d6 timed out
[  115.869069] wlp2s0: authenticate with 00:14:6c:92:7f:d6
[  115.984316] wlp2s0: send auth to 00:14:6c:92:7f:d6 (try 1/3)
[  115.985872] wlp2s0: authenticated
[  115.986154] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[  115.986164] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  115.986171] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[  115.990020] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 1/3)
[  116.192502] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 2/3)
[  116.396543] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 3/3)
[  116.600733] wlp2s0: association with 00:14:6c:92:7f:d6 timed out
[  129.373573] wlp2s0: authenticate with 00:14:6c:92:7f:d6
[  129.488794] wlp2s0: send auth to 00:14:6c:92:7f:d6 (try 1/3)
[  129.490546] wlp2s0: authenticated
[  129.490798] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[  129.490805] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  129.490810] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[  129.492790] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 1/3)
[  129.696902] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 2/3)
[  129.901017] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 3/3)
[  130.105142] wlp2s0: association with 00:14:6c:92:7f:d6 timed out
[  241.310137] usbcore: registered new interface driver rtl8187
[  251.319394] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  253.739508] wlp2s0: authenticate with 00:14:6c:92:7f:d6
[  253.793440] wlp2s0: send auth to 00:14:6c:92:7f:d6 (try 1/3)
[  253.795053] wlp2s0: authenticated
[  253.795338] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[  253.795346] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  253.795351] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[  253.797338] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 1/3)
[  254.001538] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 2/3)
[  254.205619] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 3/3)
[  254.409774] wlp2s0: association with 00:14:6c:92:7f:d6 timed out
[  265.814293] wlp2s0: authenticate with 00:14:6c:92:7f:d6
[  265.929262] wlp2s0: send auth to 00:14:6c:92:7f:d6 (try 1/3)
[  265.931008] wlp2s0: authenticated
[  265.931327] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[  265.931336] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  265.931343] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[  265.932825] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 1/3)
[  266.137018] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 2/3)
[  266.341195] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 3/3)
[  266.545263] wlp2s0: association with 00:14:6c:92:7f:d6 timed out
[  399.408217] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  622.188124] wlp2s0: authenticate with 00:14:6c:92:7f:d6
[  622.243000] wlp2s0: send auth to 00:14:6c:92:7f:d6 (try 1/3)
[  622.244656] wlp2s0: authenticated
[  622.244992] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[  622.245001] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  622.245006] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[  622.246944] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 1/3)
[  622.451095] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 2/3)
[  622.655230] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 3/3)
[  622.859375] wlp2s0: association with 00:14:6c:92:7f:d6 timed out
[  634.231410] wlp2s0: authenticate with 00:14:6c:92:7f:d6
[  634.348617] wlp2s0: send auth to 00:14:6c:92:7f:d6 (try 1/3)
[  634.350223] wlp2s0: authenticated
[  634.350528] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[  634.350538] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  634.350545] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[  634.354165] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 1/3)
[  634.558426] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 2/3)
[  634.762474] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 3/3)
[  634.966500] wlp2s0: association with 00:14:6c:92:7f:d6 timed out
[  649.669355] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  761.732358] wlp2s0: authenticate with 00:14:6c:92:7f:d6
[  761.851767] wlp2s0: send auth to 00:14:6c:92:7f:d6 (try 1/3)
[  761.855910] wlp2s0: authenticated
[  761.856160] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  761.856167] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[  761.859419] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 1/3)
[  762.063658] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 2/3)
[  762.267901] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 3/3)
[  762.472003] wlp2s0: association with 00:14:6c:92:7f:d6 timed out
[  773.872016] wlp2s0: authenticate with 00:14:6c:92:7f:d6
[  773.987101] wlp2s0: send auth to 00:14:6c:92:7f:d6 (try 1/3)
[  773.988767] wlp2s0: authenticated
[  773.989071] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  773.989081] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[  773.990804] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 1/3)
[  774.195055] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 2/3)
[  774.399100] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 3/3)
[  774.603150] wlp2s0: association with 00:14:6c:92:7f:d6 timed out
[  787.442366] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  807.540430] wlp2s0: authenticate with 00:14:6c:92:7f:d6
[  807.657728] wlp2s0: send auth to 00:14:6c:92:7f:d6 (try 1/3)
[  807.659416] wlp2s0: authenticated
[  807.659745] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  807.659753] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[  807.663452] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 1/3)
[  807.867607] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 2/3)
[  808.071725] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 3/3)
[  808.275848] wlp2s0: association with 00:14:6c:92:7f:d6 timed out
[  819.667483] wlp2s0: authenticate with 00:14:6c:92:7f:d6
[  819.781268] wlp2s0: send auth to 00:14:6c:92:7f:d6 (try 1/3)
[  819.783089] wlp2s0: authenticated
[  819.783393] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  819.783402] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[  819.786833] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 1/3)
[  819.990913] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 2/3)
[  820.195024] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 3/3)
[  820.403195] wlp2s0: association with 00:14:6c:92:7f:d6 timed out
[  829.405547] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  834.579584] wlp2s0: authenticate with 00:14:6c:92:7f:d6
[  834.630802] wlp2s0: send auth to 00:14:6c:92:7f:d6 (try 1/3)
[  834.632394] wlp2s0: authenticated
[  834.632720] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  834.632730] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[  834.635832] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 1/3)
[  834.840131] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 2/3)
[  835.044064] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 3/3)
[  835.252305] wlp2s0: association with 00:14:6c:92:7f:d6 timed out
[  846.628894] wlp2s0: authenticate with 00:14:6c:92:7f:d6
[  846.743402] wlp2s0: send auth to 00:14:6c:92:7f:d6 (try 1/3)
[  846.745955] wlp2s0: authenticated
[  846.746226] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[  846.746234] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[  846.747253] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 1/3)
[  846.951399] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 2/3)
[  847.155576] wlp2s0: associate with 00:14:6c:92:7f:d6 (try 3/3)
[  847.359673] wlp2s0: association with 00:14:6c:92:7f:d6 timed out
[  863.641838] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready

```

---

### Post by jeremy31 on 2015-10-30
Looks like an encryption issue, change the wifi router encryption to WPA2 only as it appears that you are using WEP/TKIP

---

### Post by andriy2 on 2015-10-30
The encryption is set to WPA2-PSK [AES]
Also these are available
[TABLE="width: 100%"]
[TR]
[TD="colspan: 2"]None[/TD]
[TD][/TD]
[/TR]
[TR]
[TD="colspan: 2"]WEP[/TD]
[/TR]
[TR]
[TD="colspan: 2"]WPA-PSK [TKIP][/TD]
[/TR]
[TR]
[TD="colspan: 2"]WPA2-PSK [AES][/TD]
[/TR]
[TR]
[TD="colspan: 2"]WPA-PSK [TKIP] + WPA2-PSK [AES][/TD]
[/TR]
[/TABLE]

in my router setup page.Currently using netgear router[IMG]http://s8.postimg.org/a6gzok2pf/Screenshot_from_2015_10_30_10_36_42.png[/IMG]

---

### Post by jeremy31 on 2015-10-30
Please run ```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
And paste the contents of the wireless-info.**txt** file

---

### Post by andriy2 on 2015-10-30
```
########## wireless info START ##########

Report from: 30 Oct 2015 13:58 EET +0200

Booted last: 30 Oct 2015 00:00 EET +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199]
    Kernel driver in use: rtl818x_pci

04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller [11ab:4380] (rev 10)
    Subsystem: Sony Corporation Device [104d:9067]
    Kernel driver in use: sky2

##### lsusb #############################

Bus 002 Device 003: ID 09da:c10a A4Tech Co., Ltd. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai Foxconn T77H114 BCM2070 [Single-Chip Bluetooth 2.1 + EDR Adapter]
Bus 001 Device 003: ID 064e:2100 Suyin Corp. Sony Visual Communication Camera
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ndiswrapper           286720  0
rtl818x_pci            53248  0
mac80211              733184  1 rtl818x_pci
cfg80211              548864  2 mac80211,rtl818x_pci
eeprom_93cx6           16384  1 rtl818x_pci
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp4s0    Link encap:Ethernet  HWaddr <MAC 'enp4s0' [IF]>  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp4s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50811 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39014 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56082565 (56.0 MB)  TX bytes:4111044 (4.1 MB)
          Interrupt:18 

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp4s0    no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp4s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp4s0

##### resolv.conf #######################

nameserver 127.0.1.1
search andrjuha01

##### network managers ##################

Installed:

    NetworkManager

Running:

root       683     1  0 13:32 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        88E8057 PCI-E Gigabit Ethernet Controller
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp4s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/enp4s0
GENERAL.IP-IFACE:                       enp4s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     &#1044;&#1088;&#1086;&#1090;&#1086;&#1074;&#1077; &#1079;’&#1108;&#1076;&#1085;&#1072;&#1085;&#1085;&#1103; 1
GENERAL.CON-UUID:                       6f628a14-1f6c-45bd-986f-2fec1d3d0026
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6f628a14-1f6c-45bd-986f-2fec1d3d0026 | &#1044;&#1088;&#1086;&#1090;&#1086;&#1074;&#1077; &#1079;’&#1108;&#1076;&#1085;&#1072;&#1085;&#1085;&#1103; 1
IP4.ADDRESS[1]:                         192.168.1.7/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          andrjuha01
DHCP4.OPTION[1]:                        network_number = 192.168.1.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        requested_domain_name = 1
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        expiry = 1446291184
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       domain_name = andrjuha01
DHCP4.OPTION[12]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       ip_address = 192.168.1.7
DHCP4.OPTION[17]:                       dhcp_lease_time = 86400
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[22]:                       dhcp_rebinding_time = 73440
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       requested_netbios_scope = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp4s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8187SE Wireless LAN Controller
GENERAL.DRIVER:                         rtl818x_pci
GENERAL.DRIVER-VERSION:                 4.2.0-16-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   781e1f73-8f74-40dd-8ba0-525313076a7d | andrjuha01

SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Sweet_Home     <MAC 'Sweet_Home' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Svitlana_Kama  <MAC 'Svitlana_Kama' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
andrjuha01     <MAC 'andrjuha01' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  95      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
pasichna       <MAC 'pasichna' [AC4]>  Infra  13    2472 MHz  54 Mbit/s  19      &#9602;___  --         no        
CH_HOME        <MAC 'CH_HOME' [AC5]>  Infra  10    2457 MHz  54 Mbit/s  19      &#9602;___  WPA1       no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/andrjuha01]] (600 root)
[connection] id=andrjuha01 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=andrjuha01
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Kiev (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp4s0    no frequency information.

lo        no frequency information.

wlp2s0    14 channels in total; available frequencies :
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

##### iwlist scan #######################

enp4s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.472 GHz (Channel 13)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'Sweet_Home' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Sweet_Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000013f2e3be8bd
                    Extra: Last beacon: 664ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Svitlana_Kama' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Svitlana_Kama"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000052fdb03f997
                    Extra: Last beacon: 1192ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'andrjuha01' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"andrjuha01"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000da7b3a59
                    Extra: Last beacon: 760ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'pasichna' [AC4]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"pasichna"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000daaa2180
                    Extra: Last beacon: 19616ms ago
          Cell 05 - Address: <MAC 'CH_HOME' [AC5]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"CH_HOME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000035e9e352
                    Extra: Last beacon: 19400ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Vasyl' [AC6]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"Vasyl"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000454842531de
                    Extra: Last beacon: 828ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ndiswrapper]
filename:       /lib/modules/4.2.0-16-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     F409BC57C0CA7C84BD3C333
depends:        
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

[rtl818x_pci]
filename:       /lib/modules/4.2.0-16-generic/kernel/drivers/net/wireless/rtl818x/rtl8180/rtl818x_pci.ko
license:        GPL
description:    RTL8180 / RTL8185 / RTL8187SE PCI wireless driver
author:         Andrea Merello <andrea.merello@gmail.com>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     718CDE48D1F626F7851C577
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6A:1C:9C:21:F0:4A:B8:6F:D1:D7:CE:D6:CA:11:35:40:FC:8E:35:B6
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-16-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C9DB66EC5B332CC610F266D
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6A:1C:9C:21:F0:4A:B8:6F:D1:D7:CE:D6:CA:11:35:40:FC:8E:35:B6
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-16-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6A:1C:9C:21:F0:4A:B8:6F:D1:D7:CE:D6:CA:11:35:40:FC:8E:35:B6
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v000010ECd00008185sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv00000035sd00001B0Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv00000066sd00001B0Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv00000CD6sd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv00006894sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv0000831Fsd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv00008341sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008199sv*sd*bc*sc*i* ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    4.579201] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[    4.582914] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[    6.483805] sky2 0000:04:00.0 enp4s0: Link is up at 100 Mbps, full duplex, flow control rx
[    6.483834] IPv6: ADDRCONF(NETDEV_CHANGE): enp4s0: link becomes ready
[ 1237.169589] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[ 1237.171692] ndiswrapper version 1.59 loaded (smp=yes, preempt=no) (repeated 2 times)
[ 1350.775087] wlp2s0: authenticate with <MAC 'andrjuha01' [AC3]>
[ 1350.891583] wlp2s0: send auth to <MAC 'andrjuha01' [AC3]> (try 1/3)
[ 1350.893309] wlp2s0: authenticated
[ 1350.893558] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[ 1350.893564] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[ 1350.894560] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 1/3)
[ 1351.098802] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 2/3)
[ 1351.302949] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 3/3)
[ 1351.507076] wlp2s0: association with <MAC 'andrjuha01' [AC3]> timed out
[ 1352.900571] wlp2s0: authenticate with <MAC 'andrjuha01' [AC3]>
[ 1353.005250] wlp2s0: send auth to <MAC 'andrjuha01' [AC3]> (try 1/3)
[ 1353.007053] wlp2s0: authenticated
[ 1353.007298] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[ 1353.007305] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[ 1353.007879] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 1/3)
[ 1353.212097] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 2/3)
[ 1353.416177] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 3/3)
[ 1353.620312] wlp2s0: association with <MAC 'andrjuha01' [AC3]> timed out
[ 1355.438265] wlp2s0: authenticate with <MAC 'andrjuha01' [AC3]>
[ 1355.549948] wlp2s0: send auth to <MAC 'andrjuha01' [AC3]> (try 1/3)
[ 1355.551515] wlp2s0: authenticated
[ 1355.551718] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[ 1355.551725] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[ 1355.553455] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 1/3)
[ 1355.757630] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 2/3)
[ 1355.961751] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 3/3)
[ 1356.165788] wlp2s0: association with <MAC 'andrjuha01' [AC3]> timed out
[ 1358.496227] wlp2s0: authenticate with <MAC 'andrjuha01' [AC3]>
[ 1358.607457] wlp2s0: send auth to <MAC 'andrjuha01' [AC3]> (try 1/3)
[ 1358.609239] wlp2s0: authenticated
[ 1358.609502] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[ 1358.609509] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[ 1358.611288] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 1/3)
[ 1358.815678] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 2/3)
[ 1359.019693] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 3/3)
[ 1359.223664] wlp2s0: association with <MAC 'andrjuha01' [AC3]> timed out
[ 1370.315686] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 1371.556213] wlp2s0: authenticate with <MAC 'andrjuha01' [AC3]>
[ 1371.674517] wlp2s0: send auth to <MAC 'andrjuha01' [AC3]> (try 1/3)
[ 1371.676018] wlp2s0: authenticated
[ 1371.676221] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[ 1371.676228] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[ 1371.679175] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 1/3)
[ 1371.883278] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 2/3)
[ 1372.087641] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 3/3)
[ 1372.291755] wlp2s0: association with <MAC 'andrjuha01' [AC3]> timed out
[ 1383.627203] wlp2s0: authenticate with <MAC 'andrjuha01' [AC3]>
[ 1383.742515] wlp2s0: send auth to <MAC 'andrjuha01' [AC3]> (try 1/3)
[ 1383.744890] wlp2s0: authenticated
[ 1383.745193] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[ 1383.745203] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[ 1383.746730] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 1/3)
[ 1383.950668] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 2/3)
[ 1384.154948] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 3/3)
[ 1384.358856] wlp2s0: association with <MAC 'andrjuha01' [AC3]> timed out
[ 1392.081427] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 1424.328033] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 1430.931857] wlp2s0: authenticate with <MAC 'andrjuha01' [AC3]>
[ 1431.051713] wlp2s0: send auth to <MAC 'andrjuha01' [AC3]> (try 1/3)
[ 1431.053340] wlp2s0: authenticated
[ 1431.053654] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[ 1431.053662] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[ 1431.055358] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 1/3)
[ 1431.259553] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 2/3)
[ 1431.463675] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 3/3)
[ 1431.667756] wlp2s0: association with <MAC 'andrjuha01' [AC3]> timed out
[ 1442.975203] wlp2s0: authenticate with <MAC 'andrjuha01' [AC3]>
[ 1443.090593] wlp2s0: send auth to <MAC 'andrjuha01' [AC3]> (try 1/3)
[ 1443.092086] wlp2s0: authenticated
[ 1443.092315] rtl818x_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[ 1443.092322] rtl818x_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[ 1443.094646] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 1/3)
[ 1443.298879] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 2/3)
[ 1443.502820] wlp2s0: associate with <MAC 'andrjuha01' [AC3]> (try 3/3)
[ 1443.706991] wlp2s0: association with <MAC 'andrjuha01' [AC3]> timed out
[ 1456.306944] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready

########## wireless info END ############
```

---

### Post by andriy2 on 2015-10-30
Do you have any ideas what it could be?

---

### Post by jeremy31 on 2015-10-30
Something going on yet with encryption as the script report shows
```

ell 03 - Address: <MAC 'andrjuha01' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"andrjuha01"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000da7b3a59
                    Extra: Last beacon: 760ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
```
I wouldn't bother with ndiswrapper as it is a poor solution

---

### Post by andriy2 on 2015-10-30
Okay, I'll delete it

---

### Post by andriy2 on 2015-10-30
To admit, in Windows works great, but problems on linux

---

### Post by praseodym on 2015-10-30
Why is ndiswrapper installed?!
```

sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndiswrapper* ndisgtk
```
Reboot.

---

