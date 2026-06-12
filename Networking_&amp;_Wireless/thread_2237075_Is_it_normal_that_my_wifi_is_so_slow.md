---
title: "Is it normal that my wifi is so slow ?"
date: 2014-07-30
forum: Networking &amp; Wireless
---

### Post by dargaud2 on 2014-07-30
Hello all,
the wifi between my laptop and the wifi router runs at only 300~600Kb/s, so it takes exactly one hour to transfer ONE Gb. An NFS server has a 1Gbps ethernet cable connection to the wifi router. The configuration of the router is a pain in the ass (it's a DLink DAP-1360 which can only be configured by setting a fixed address via ethernet) but I've set it to ONLY do 802.11n, no security. Shouldn't it operate at something like half of the promised 300Mbps, 500 times faster than what I get ?!? What is the problem ?
```
$ iwconfig
wlan0     IEEE 802.11abgn  ESSID:"LameAssWifi" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: 5C:D9:98:5F:A7:68  
          Bit Rate=72.2 Mb/s   Tx-Power=15 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:894   Missed beacon:0

```
```
$ lspci | grep Network  
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)

```
```
$ dmesg | grep -i "wlan\|wifi"
[    7.627343] Intel(R) Wireless WiFi driver for Linux, in-tree:
[    7.627619] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    7.627801] iwlwifi 0000:03:00.0: irq 47 for MSI/MSI-X
[    7.734774] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    7.796581] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    7.796583] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    7.796584] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    7.796585] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[    7.796682] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    8.724816] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    8.732013] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    8.998443] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    9.005197] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    9.094355] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.094927] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.279961] wlan0: authenticate with 5c:d9:98:5f:a7:68
[   12.284392] wlan0: send auth to 5c:d9:98:5f:a7:68 (try 1/3)
[   12.286761] wlan0: authenticated
[   12.286948] wlan0: waiting for beacon from 5c:d9:98:5f:a7:68
[   12.357648] wlan0: associate with 5c:d9:98:5f:a7:68 (try 1/3)
[   12.361805] wlan0: RX AssocResp from 5c:d9:98:5f:a7:68 (capab=0x401 status=0 aid=13)
[   12.382387] wlan0: associated
[   12.382442] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```
```
$ lsmod | grep wifi
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm

```
```
$ sudo lshw -C Network
...
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205 [Taylor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: a4:4e:31:1e:66:d8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-32-generic firmware=18.168.6.1 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f7d00000-f7d01fff

```
...thanks

---

### Post by praseodym on 2014-07-30
Change the router mode to a/b/g and deactivate the N-mode of the driver:
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by dargaud2 on 2014-07-31
Well, apparently it's not an option on this model, it has N, N/G or N/G/B options only. I set it on N/G...
I did what you suggested for the iwlwifi file and now:
> 
$ iwconfig
wlan0     IEEE 802.11abg  ESSID:"DargaudWifiN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 5C:D9:98:5F:A7:68   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:286   Missed beacon:0

But I just tested it on a large file and the effective transfer speed is 52kB/s...

---

### Post by praseodym on 2014-08-01
Change the nameservers:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by dargaud2 on 2014-08-03
I already use those nameservers, and anyway the speed problem happens also when doing local copies between machines, like in my example.

---

### Post by praseodym on 2014-08-03
Add the mtu value of your ISP instead of "Automatic" in  your NM profile. Normally its 1500

---

### Post by dargaud2 on 2014-08-03
The MTU given by ifconfig is 1500. I've forced mode N on the router, forced WPA2 only and now I can get 5MB/s (bytes), I also disabled the bluetooth in the BIOS ([interferences?]("http://ubuntuforums.org/showthread.php?t=2236744&p=13086831#post13086831")), so that's an improvement (a one Gb file now copies in 8 minutes instead of one hour). But still, the cheap HP sitting right next to it copies the same file in one minute. With the same i[fw]config. I also tried a simultaneous copy from both computers. The HP took 2 minutes (makes sense), the Dell 10 minutes....

---

### Post by praseodym on 2014-08-03
Try to deactivate the queue of the network in the driver, too:

```
echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
```
Reboot.

---

