---
title: "Intel Centrino-N 2230 connection issues: internet is VERY slow and connection drops"
date: 2014-02-20
forum: Networking &amp; Wireless
---

### Post by charles18 on 2014-02-20
Hi guys

**History:** I am now at wit's end, I have enjoyed the struggled but am feeling like giving up, I come from Linux Mint 15 where I have had Wireless and Sound issues....
**Device:** I am using a Mecer W550EU, i5 8gb Ram and intel centrino-n 2230 wireless card 
**OS version:** Ubuntu 13.10
**Kernel:** 3.11.0-17-generic
**Device (lspci | grep Wireless):** 02:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
**internet speed:** +1 gb/s (university) - wireless

**Problem:**
[LIST]
[*]Firefox/Chrome are both VERY VERY slow, takes +/- 5min to load google.co.za alone! 
[*]at the same time, I do a playonlinux install with apt, I get 2mbps download speed, please note Firefox has ipv6 disabled, made a slight improvement! 
[*]after +/- 10 min after connecting, the pages load for infinity, when I ```
ping google.co.za
``` it says host is unreachable, at times the terminal is very slow also when ```
apt-get update
``` is run 
[/LIST]

The connection isnt a problem, I go on google and search something on both my android phone and tablet, it takes a little longer than normal but it loads quickly...

I am going to replace my existing iwlwifi-2030.ucode file with that from compat-wireless but I dont know if it will make a difference...

**terminal info**

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:f5:d9:7b:ee  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:936566 (936.5 KB)  TX bytes:936566 (936.5 KB)

wlan0     Link encap:Ethernet  HWaddr 84:a6:c8:6e:b5:b3  
          inet addr:10.102.29.83  Bcast:10.102.31.255  Mask:255.255.248.0
          inet6 addr: fe80::86a6:c8ff:fe6e:b5b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76004 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:110603138 (110.6 MB)  TX bytes:9481588 (9.4 MB)

```

```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.2 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 [8086:1e14] (rev c4)
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
00:1c.4 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 [8086:1e18] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM77 Express Chipset LPC Controller [8086:1e57] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5289] (rev 01)
03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)

```

**If anyone knowss about this issue or has fixed it, PLEASE help!!!**

---

### Post by chili555 on 2014-02-20
Please try a temporary driver parameter:```
sudo modprobe -r iwldvm
sudo modprobe iwlwifi 11n_disable=1
```If it helps, we can amend a file to make it permanent.

---

### Post by soum_axetuirk on 2014-02-20
Download and Install given driver from intel. [https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=17045](https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=17045)
Tested and working flowlessly on Dell Laptops.

---

### Post by chili555 on 2014-02-20
> **soum_axetuirk said:**
> Download and Install given driver from intel. [https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=17045](https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=17045)
Tested and working flowlessly on Dell Laptops.This simply offers the same firmware that's already installed by default in 13.10 for the 2230; or did you do something different? What??> iwlwifi-2030-ucode-18.168.6.1

---

### Post by phantom1bc on 2014-02-25
the intel 2230 is a proven dead dog and intel doesn't even care, sorry personal frustration on that wifi card, google wireless n 2230 connection problems and you'll see your answer is to get a new card

---

