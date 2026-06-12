---
title: "Lenovo L540 with RTL8192EE wireless chip - no driver (Ubuntu 14.04 LTS)"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by strsljen on 2014-04-19
Hi!

I can't get wireless apadter  on my new laptop running.
Laptop is Lenovo L540 and wireless adapter (according to lspci -v):

```
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter
    Subsystem: Realtek Semiconductor Co., Ltd. Device 001b
    Flags: bus master, fast devsel, latency 0, IRQ 10
    I/O ports at 5000 [size=256]
    Memory at f2400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 01-91-81-fe-ff-4c-e0-00
    Capabilities: [150] Latency Tolerance Reporting
    Capabilities: [158] L1 PM Substates

```

I found several pages reporting this as no-driver problem.

Is there a chance Ubuntu can support this adapter or I have to purchase additional USB wireless adapter with Intel chip?

Best regards,

--
Strs.

---

### Post by chili555 on 2014-04-19
Please see posts #11-17 here: [http://ubuntuforums.org/showthread.php?t=2190347&page=2](http://ubuntuforums.org/showthread.php?t=2190347&page=2)

---

### Post by strsljen on 2014-04-19
Hi!

Thank you for the link.
I compiled the module. Now I can see and connect to wifi network, but can't ping, resolve or surf to any location.

I got the IP address from wifi network, but that's about it.

I have old laptop with Ubuntu 12.04LTS on same wifi network working properly.

---

### Post by chili555 on 2014-04-19
Let's have a look at:```
nm-tool
```Please run and post it as the ethernet is detached and you're connected wirelessly and unable to surf.

---

### Post by strsljen on 2014-04-19
Hi!

Here is the output:


```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [WLAN] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ee
  State:             connected
  Default:           yes
  HW Address:        9C:D2:1E:18:91:89

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Gogo:            Infra, 00:21:04:80:EC:E0, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Debelimedo:      Infra, 00:1D:68:B6:DD:65, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WEP
    *WLAN:           Infra, C0:D0:44:64:94:78, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA2

  IPv4 Settings:
    Address:         192.168.1.190
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             8.8.8.8


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        54:EE:75:09:6D:42

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

---

### Post by chili555 on 2014-04-19
Looks fairly good, actually. Let's see some more diagnostics:```
dmesg | grep rtl
ping -c3 8.8.8.8
```It compiled with quite a few warnings but no errors on my 14.04 system. I wonder if all the faulty parts prevent the device from working correctly.> I have to purchase additional USB wireless adapter with **Intel** chip?Is there such a thing?

In case you are thinking of buying a different PCI card for your Lenovo, please read and consider this first: [http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card](http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card) And also: [http://forums.lenovo.com/t5/General-Discussion/WWAN-and-wireless-card-BIOS-whitelists-Lenovo-COME-ON/td-p/952681](http://forums.lenovo.com/t5/General-Discussion/WWAN-and-wireless-card-BIOS-whitelists-Lenovo-COME-ON/td-p/952681)

---

### Post by strsljen on 2014-04-19
Hi!

Here are the outputs;

dmesg:
```
[ 2751.809195] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 2751.809263] rtl8192ee: 
[ 2751.809266] In process "swapper/3" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2756.730569] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2756.730579] rtl8192ee: 
[ 2756.730583] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2756.815014] rtlwifi-0:rtl_lps_set_psmode():<600-1> FW LPS leave ps_mode:0
[ 2756.815080] rtl8192ee: 
[ 2756.815084] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2762.749178] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2762.749187] rtl8192ee: 
[ 2762.749191] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2774.087888] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 2774.087956] rtl8192ee: 
[ 2774.087959] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2776.792608] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2776.792618] rtl8192ee: 
[ 2776.792621] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2780.833098] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 2780.833165] rtl8192ee: 
[ 2780.833169] In process "swapper/1" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2790.835983] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2790.835993] rtl8192ee: 
[ 2790.835996] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2790.844421] rtlwifi-0:rtl_lps_set_psmode():<600-1> FW LPS leave ps_mode:0
[ 2790.844486] rtl8192ee: 
[ 2790.844490] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2794.848455] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2794.848465] rtl8192ee: 
[ 2794.848468] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2804.080650] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 2804.080712] rtl8192ee: 
[ 2804.080715] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2806.885687] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2806.885696] rtl8192ee: 
[ 2806.885700] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2816.872708] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 2816.872775] rtl8192ee: 
[ 2816.872779] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2820.929113] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2820.929123] rtl8192ee: 
[ 2820.929126] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2821.885010] rtlwifi-0:rtl_lps_set_psmode():<600-1> FW LPS leave ps_mode:0
[ 2821.885076] rtl8192ee: 
[ 2821.885079] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2830.960139] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2830.960149] rtl8192ee: 
[ 2830.960152] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2839.144012] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 2839.144077] rtl8192ee: 
[ 2839.144079] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2842.997368] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2842.997378] rtl8192ee: 
[ 2842.997382] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2854.914507] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 2854.914574] rtl8192ee: 
[ 2854.914578] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2859.047006] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2859.047016] rtl8192ee: 
[ 2859.047019] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2859.927931] rtlwifi-0:rtl_lps_set_psmode():<600-1> FW LPS leave ps_mode:0
[ 2859.927997] rtl8192ee: 
[ 2859.928001] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2869.078029] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2869.078039] rtl8192ee: 
[ 2869.078042] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2875.530238] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 2875.530307] rtl8192ee: 
[ 2875.530311] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2879.109051] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2879.109061] rtl8192ee: 
[ 2879.109065] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2894.974541] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 2894.974609] rtl8192ee: 
[ 2894.974612] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2899.171104] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2899.171113] rtl8192ee: 
[ 2899.171117] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2899.974617] rtlwifi-0:rtl_lps_set_psmode():<600-1> FW LPS leave ps_mode:0
[ 2899.974683] rtl8192ee: 
[ 2899.974686] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2909.202125] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2909.202135] rtl8192ee: 
[ 2909.202139] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2911.926601] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 2911.926668] rtl8192ee: 
[ 2911.926671] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2915.220734] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2915.220744] rtl8192ee: 
[ 2915.220747] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2937.004722] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 2937.004789] rtl8192ee: 
[ 2937.004793] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2941.301404] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2941.301414] rtl8192ee: 
[ 2941.301418] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2942.014499] rtlwifi-0:rtl_lps_set_psmode():<600-1> FW LPS leave ps_mode:0
[ 2942.014566] rtl8192ee: 
[ 2942.014569] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2951.332440] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2951.332450] rtl8192ee: 
[ 2951.332454] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2981.069145] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 2981.069213] rtl8192ee: 
[ 2981.069216] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2987.444110] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2987.444119] rtl8192ee: 
[ 2987.444123] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2991.080148] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 2991.080211] rtl8192ee: 
[ 2991.080214] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 2995.468923] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2995.468933] rtl8192ee: 
[ 2995.468936] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3014.360783] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3014.360851] rtl8192ee: 
[ 3014.360854] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3017.537162] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3017.537172] rtl8192ee: 
[ 3017.537176] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3027.103725] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3027.103791] rtl8192ee: 
[ 3027.103795] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3031.580604] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3031.580614] rtl8192ee: 
[ 3031.580617] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3032.110352] rtlwifi-0:rtl_lps_set_psmode():<600-1> FW LPS leave ps_mode:0
[ 3032.110419] rtl8192ee: 
[ 3032.110423] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3041.611627] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3041.611637] rtl8192ee: 
[ 3041.611641] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3049.386477] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3049.386546] rtl8192ee: 
[ 3049.386549] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3051.642595] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3051.642605] rtl8192ee: 
[ 3051.642608] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3075.172563] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3075.172630] rtl8192ee: 
[ 3075.172634] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3079.729518] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3079.729527] rtl8192ee: 
[ 3079.729531] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3080.180813] rtlwifi-0:rtl_lps_set_psmode():<600-1> FW LPS leave ps_mode:0
[ 3080.180878] rtl8192ee: 
[ 3080.180882] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3085.748141] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3085.748151] rtl8192ee: 
[ 3085.748155] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3085.860514] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3085.860582] rtl8192ee: 
[ 3085.860586] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3089.760545] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3089.760555] rtl8192ee: 
[ 3089.760558] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3122.156735] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3122.156803] rtl8192ee: 
[ 3122.156807] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3125.872226] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3125.872236] rtl8192ee: 
[ 3125.872239] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3130.241081] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3130.241149] rtl8192ee: 
[ 3130.241152] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3139.915655] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3139.915665] rtl8192ee: 
[ 3139.915669] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3152.520845] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3152.520912] rtl8192ee: 
[ 3152.520916] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3155.965298] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3155.965308] rtl8192ee: 
[ 3155.965311] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3177.284754] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3177.284822] rtl8192ee: 
[ 3177.284825] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3182.045956] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3182.045965] rtl8192ee: 
[ 3182.045969] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3182.297063] rtlwifi-0:rtl_lps_set_psmode():<600-1> FW LPS leave ps_mode:0
[ 3182.297130] rtl8192ee: 
[ 3182.297134] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3192.076969] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3192.076980] rtl8192ee: 
[ 3192.076984] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3222.105944] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3222.106014] rtl8192ee: 
[ 3222.106019] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3224.176256] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3224.176266] rtl8192ee: 
[ 3224.176270] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3231.344182] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3231.344250] rtl8192ee: 
[ 3231.344254] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3236.213447] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3236.213453] rtl8192ee: 
[ 3236.213455] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3236.358914] rtlwifi-0:rtl_lps_set_psmode():<600-1> FW LPS leave ps_mode:0
[ 3236.358977] rtl8192ee: 
[ 3236.358979] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3246.244465] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3246.244505] rtl8192ee: 
[ 3246.244508] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3253.621599] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3253.621667] rtl8192ee: 
[ 3253.621671] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3256.275534] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3256.275544] rtl8192ee: 
[ 3256.275548] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3287.421805] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3287.421868] rtl8192ee: 
[ 3287.421871] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3292.387217] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3292.387226] rtl8192ee: 
[ 3292.387230] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3297.432782] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3297.432850] rtl8192ee: 
[ 3297.432853] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3302.418240] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3302.418250] rtl8192ee: 
[ 3302.418253] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3318.707853] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3318.707920] rtl8192ee: 
[ 3318.707923] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3322.480213] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3322.480218] rtl8192ee: 
[ 3322.480220] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3345.485610] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3345.485677] rtl8192ee: 
[ 3345.485680] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3354.579519] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3354.579528] rtl8192ee: 
[ 3354.579532] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3355.185388] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3355.185455] rtl8192ee: 
[ 3355.185458] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3358.591977] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3358.591987] rtl8192ee: 
[ 3358.591991] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3391.580953] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3391.581020] rtl8192ee: 
[ 3391.581023] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3394.703660] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3394.703670] rtl8192ee: 
[ 3394.703674] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3405.535609] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3405.535676] rtl8192ee: 
[ 3405.535679] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3414.765705] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3414.765715] rtl8192ee: 
[ 3414.765718] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3415.557938] rtlwifi-0:rtl_lps_set_psmode():<600-1> FW LPS leave ps_mode:0
[ 3415.558005] rtl8192ee: 
[ 3415.558008] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3420.784281] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3420.784291] rtl8192ee: 
[ 3420.784294] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3428.008048] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3428.008110] rtl8192ee: 
[ 3428.008114] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3430.815348] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3430.815358] rtl8192ee: 
[ 3430.815361] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3464.476076] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3464.476144] rtl8192ee: 
[ 3464.476147] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3466.927024] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3466.927035] rtl8192ee: 
[ 3466.927038] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3472.633339] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3472.633405] rtl8192ee: 
[ 3472.633409] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3476.958056] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3476.958066] rtl8192ee: 
[ 3476.958069] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3477.636677] rtlwifi-0:rtl_lps_set_psmode():<600-1> FW LPS leave ps_mode:0
[ 3477.636743] rtl8192ee: 
[ 3477.636747] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3482.976673] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3482.976682] rtl8192ee: 
[ 3482.976686] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3531.593772] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3531.593840] rtl8192ee: 
[ 3531.593843] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3535.137976] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3535.137986] rtl8192ee: 
[ 3535.137989] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3541.669205] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3541.669273] rtl8192ee: 
[ 3541.669277] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3547.175204] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3547.175213] rtl8192ee: 
[ 3547.175217] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3562.939734] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3562.939801] rtl8192ee: 
[ 3562.939804] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3565.231045] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3565.231055] rtl8192ee: 
[ 3565.231059] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3597.730814] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3597.730881] rtl8192ee: 
[ 3597.730884] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3603.348963] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3603.348975] rtl8192ee: 
[ 3603.348978] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3607.741790] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3607.741859] rtl8192ee: 
[ 3607.741862] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3613.379957] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3613.379967] rtl8192ee: 
[ 3613.379970] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3630.029564] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3630.029630] rtl8192ee: 
[ 3630.029634] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3633.442011] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3633.442021] rtl8192ee: 
[ 3633.442024] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3666.425878] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3666.425945] rtl8192ee: 
[ 3666.425948] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3669.553697] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3669.553707] rtl8192ee: 
[ 3669.553711] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3675.832639] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3675.832706] rtl8192ee: 
[ 3675.832709] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3681.590921] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3681.590931] rtl8192ee: 
[ 3681.590935] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3698.112095] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3698.112162] rtl8192ee: 
[ 3698.112165] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3701.652971] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3701.652980] rtl8192ee: 
[ 3701.652984] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3734.568466] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3734.568533] rtl8192ee: 
[ 3734.568537] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3737.764648] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3737.764658] rtl8192ee: 
[ 3737.764662] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3740.928186] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3740.928254] rtl8192ee: 
[ 3740.928257] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3745.789476] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3745.789486] rtl8192ee: 
[ 3745.789489] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3745.939350] rtlwifi-0:rtl_lps_set_psmode():<600-1> FW LPS leave ps_mode:0
[ 3745.939416] rtl8192ee: 
[ 3745.939420] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3751.808082] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3751.808092] rtl8192ee: 
[ 3751.808095] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3764.213672] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3764.213688] rtl8192ee: 
[ 3764.213691] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3767.857725] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3767.857735] rtl8192ee: 
[ 3767.857739] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3800.696898] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3800.696966] rtl8192ee: 
[ 3800.696969] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3803.969409] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3803.969419] rtl8192ee: 
[ 3803.969422] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3807.961830] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3807.961897] rtl8192ee: 
[ 3807.961900] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3811.994222] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3811.994233] rtl8192ee: 
[ 3811.994236] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3812.968570] rtlwifi-0:rtl_lps_set_psmode():<600-1> FW LPS leave ps_mode:0
[ 3812.968637] rtl8192ee: 
[ 3812.968640] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3822.025235] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3822.025246] rtl8192ee: 
[ 3822.025249] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3830.336937] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3830.337004] rtl8192ee: 
[ 3830.337007] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3834.062476] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3834.062486] rtl8192ee: 
[ 3834.062490] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3866.534754] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3866.534818] rtl8192ee: 
[ 3866.534820] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3870.174165] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3870.174175] rtl8192ee: 
[ 3870.174179] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3882.091295] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3882.091361] rtl8192ee: 
[ 3882.091365] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3886.223801] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3886.223811] rtl8192ee: 
[ 3886.223814] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3887.093608] rtlwifi-0:rtl_lps_set_psmode():<600-1> FW LPS leave ps_mode:0
[ 3887.093675] rtl8192ee: 
[ 3887.093678] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3896.254821] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3896.254831] rtl8192ee: 
[ 3896.254834] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3902.930848] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3902.930916] rtl8192ee: 
[ 3902.930920] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3906.285851] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3906.285861] rtl8192ee: 
[ 3906.285864] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3939.316959] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3939.317027] rtl8192ee: 
[ 3939.317030] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3942.397528] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3942.397538] rtl8192ee: 
[ 3942.397541] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3958.126851] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 3958.126917] rtl8192ee: 
[ 3958.126920] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3962.459493] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3962.459500] rtl8192ee: 
[ 3962.459502] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3963.133486] rtlwifi-0:rtl_lps_set_psmode():<600-1> FW LPS leave ps_mode:0
[ 3963.133553] rtl8192ee: 
[ 3963.133556] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3972.490599] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3972.490608] rtl8192ee: 
[ 3972.490612] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3975.804281] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 3975.804348] rtl8192ee: 
[ 3975.804351] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 3978.509214] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 3978.509224] rtl8192ee: 
[ 3978.509228] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4012.292479] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4012.292546] rtl8192ee: 
[ 4012.292550] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4014.620904] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4014.620913] rtl8192ee: 
[ 4014.620917] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4036.260716] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 4036.260782] rtl8192ee: 
[ 4036.260786] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4043.688952] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: c0:d0:44:64:94:78
[ 4043.688973] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 4043.688984] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 4043.688991] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 4043.689061] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc 
[ 4043.689079] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 4043.689085] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[ 4043.689148] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 4043.689154] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[ 4043.689232] rtlwifi-0:rtl_op_sta_remove():<0-0> Remove sta addr is c0:d0:44:64:94:78
[ 4043.689328] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[ 4043.689390] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1c
[ 4043.689455] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1b
[ 4043.689520] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: 00:00:00:00:00:00
[ 4043.704959] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 2, mac: ff:ff:ff:ff:ff:ff
[ 4043.704975] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 4043.704981] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 4043.704985] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:2
[ 4043.705047] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 4043.705051] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010010 
[ 4044.743091] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: c0:d0:44:64:94:78
[ 4044.743223] rtlwifi-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 4044.748551] rtlwifi-0:rtl_op_sta_add():<0-0> Add sta addr is c0:d0:44:64:94:78
[ 4044.748558] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ff5
[ 4044.748563] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:6, ratr_val:ff5, 0:6:0:f5:f:0:0
[ 4044.748659] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ff5
[ 4044.748663] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:6, ratr_val:ff5, 0:6:0:f5:f:0:0
[ 4044.748747] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[ 4044.748816] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 5b
[ 4044.748892] rtl8192ee: 
[ 4044.748895] In process "kworker/u16:0" (pid 7204):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[ 4044.748912] rtl8192ee: 
[ 4044.750729] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 4044.751233] rtl8192ee: 
[ 4044.751237] In process "kworker/u16:0" (pid 7204):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[ 4044.751249] rtl8192ee: 
[ 4044.753393] rtl8192ee: 
[ 4044.753395] In process "kworker/u16:0" (pid 7204):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[ 4044.753407] rtl8192ee: 
[ 4044.755563] rtl8192ee: 
[ 4044.755566] In process "kworker/u16:0" (pid 7204):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[ 4044.755578] rtl8192ee: 
[ 4044.757721] rtl8192ee: 
[ 4044.757723] In process "kworker/u16:0" (pid 7204):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[ 4044.757735] rtl8192ee: 
[ 4044.760656] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 4044.760749] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[ 4044.762836] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 4044.763052] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 4044.763144] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[ 4044.763218] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: c0:d0:44:64:94:78
[ 4044.763221] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 4044.763222] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 4044.763224] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[ 4044.763282] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc 
[ 4044.763287] rtlwifi-0:rtl_op_set_key():<0-0> set pairwise key
[ 4044.763288] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 4044.763290] rtl8192ee-0:rtl92ee_set_key():<0-0> set Pairwiase key
[ 4044.763291] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr c0:d0:44:64:94:78
[ 4044.763293] rtlwifi: 
[ 4044.764245] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end 
[ 4044.764338] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: ff:ff:ff:ff:ff:ff
[ 4044.764340] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 4044.764341] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[ 4044.764343] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 4044.764344] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[ 4044.764345] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr ff:ff:ff:ff:ff:ff
[ 4044.764347] rtlwifi: 
[ 4044.765299] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end 
[ 4054.744989] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4054.744999] rtl8192ee: 
[ 4054.745002] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4085.202207] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4085.202274] rtl8192ee: 
[ 4085.202277] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4088.850479] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4088.850489] rtl8192ee: 
[ 4088.850493] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4116.332724] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 4116.332792] rtl8192ee: 
[ 4116.332795] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4118.943539] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4118.943549] rtl8192ee: 
[ 4118.943553] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4121.703486] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4121.703553] rtl8192ee: 
[ 4121.703557] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4124.962152] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4124.962162] rtl8192ee: 
[ 4124.962165] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4158.084808] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4158.084875] rtl8192ee: 
[ 4158.084878] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4161.073838] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4161.073848] rtl8192ee: 
[ 4161.073851] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4194.481615] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4194.481683] rtl8192ee: 
[ 4194.481686] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4197.185523] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4197.185533] rtl8192ee: 
[ 4197.185537] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4203.452466] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 4203.452536] rtl8192ee: 
[ 4203.452539] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4207.216548] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4207.216558] rtl8192ee: 
[ 4207.216561] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4230.877420] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4230.877487] rtl8192ee: 
[ 4230.877490] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4233.297212] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4233.297222] rtl8192ee: 
[ 4233.297225] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4267.263457] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4267.263524] rtl8192ee: 
[ 4267.263528] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4269.408890] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4269.408900] rtl8192ee: 
[ 4269.408903] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4282.531361] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 4282.531430] rtl8192ee: 
[ 4282.531433] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4285.458532] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4285.458542] rtl8192ee: 
[ 4285.458545] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4303.742667] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4303.742735] rtl8192ee: 
[ 4303.742739] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4307.526786] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4307.526796] rtl8192ee: 
[ 4307.526800] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4340.215972] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4340.216039] rtl8192ee: 
[ 4340.216042] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4343.638470] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4343.638480] rtl8192ee: 
[ 4343.638484] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4368.625964] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 4368.625979] rtl8192ee: 
[ 4368.625983] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4371.725336] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4371.725345] rtl8192ee: 
[ 4371.725349] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4376.612500] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4376.612567] rtl8192ee: 
[ 4376.612570] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4379.750158] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4379.750168] rtl8192ee: 
[ 4379.750172] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4412.898073] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4412.898140] rtl8192ee: 
[ 4412.898144] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4415.861838] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4415.861848] rtl8192ee: 
[ 4415.861852] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4449.374532] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4449.374600] rtl8192ee: 
[ 4449.374604] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4451.973519] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4451.973529] rtl8192ee: 
[ 4451.973532] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4456.738798] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 4456.738866] rtl8192ee: 
[ 4456.738869] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4459.998345] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4459.998355] rtl8192ee: 
[ 4459.998359] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4485.781406] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4485.781475] rtl8192ee: 
[ 4485.781478] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4488.085212] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4488.085222] rtl8192ee: 
[ 4488.085226] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4519.734811] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4519.734879] rtl8192ee: 
[ 4519.734882] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4522.190687] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4522.190696] rtl8192ee: 
[ 4522.190700] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4546.789763] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 4546.789831] rtl8192ee: 
[ 4546.789835] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4550.277545] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4550.277555] rtl8192ee: 
[ 4550.277558] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4556.278494] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4556.278561] rtl8192ee: 
[ 4556.278565] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4558.302365] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4558.302375] rtl8192ee: 
[ 4558.302379] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4592.574398] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4592.574465] rtl8192ee: 
[ 4592.574468] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4596.420251] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4596.420261] rtl8192ee: 
[ 4596.420265] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4622.847396] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4622.847463] rtl8192ee: 
[ 4622.847467] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4626.513325] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4626.513335] rtl8192ee: 
[ 4626.513338] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4638.874958] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 4638.875024] rtl8192ee: 
[ 4638.875028] In process "swapper/3" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4642.562960] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4642.562970] rtl8192ee: 
[ 4642.562973] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4659.244081] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4659.244148] rtl8192ee: 
[ 4659.244152] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4662.625013] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4662.625023] rtl8192ee: 
[ 4662.625026] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4695.630073] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4695.630136] rtl8192ee: 
[ 4695.630139] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4698.736693] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4698.736702] rtl8192ee: 
[ 4698.736706] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4732.048397] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4732.048464] rtl8192ee: 
[ 4732.048467] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4734.848378] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4734.848388] rtl8192ee: 
[ 4734.848391] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4738.039907] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 4738.039977] rtl8192ee: 
[ 4738.039981] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4740.866991] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4740.867001] rtl8192ee: 
[ 4740.867004] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4768.492339] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4768.492406] rtl8192ee: 
[ 4768.492410] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4770.960072] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4770.960082] rtl8192ee: 
[ 4770.960085] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4804.969092] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4804.969159] rtl8192ee: 
[ 4804.969162] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4807.071747] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4807.071757] rtl8192ee: 
[ 4807.071761] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4829.083974] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 4829.084040] rtl8192ee: 
[ 4829.084043] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4831.146200] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4831.146211] rtl8192ee: 
[ 4831.146214] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4841.366327] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4841.366394] rtl8192ee: 
[ 4841.366397] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4845.189635] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4845.189645] rtl8192ee: 
[ 4845.189648] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4877.770933] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4877.771002] rtl8192ee: 
[ 4877.771005] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4881.301311] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4881.301321] rtl8192ee: 
[ 4881.301325] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4914.267401] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4914.267464] rtl8192ee: 
[ 4914.267466] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4917.413004] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4917.413014] rtl8192ee: 
[ 4917.413017] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4927.255808] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 4927.255874] rtl8192ee: 
[ 4927.255877] In process "dnsmasq" (pid 2338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4929.450222] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4929.450232] rtl8192ee: 
[ 4929.450235] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4950.673642] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4950.673710] rtl8192ee: 
[ 4950.673713] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4953.524694] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4953.524704] rtl8192ee: 
[ 4953.524707] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4987.059883] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 4987.059950] rtl8192ee: 
[ 4987.059954] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 4989.636376] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 4989.636386] rtl8192ee: 
[ 4989.636390] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5023.456088] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 5023.456156] rtl8192ee: 
[ 5023.456160] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5025.748041] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 5025.748051] rtl8192ee: 
[ 5025.748055] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5032.331328] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 5032.331393] rtl8192ee: 
[ 5032.331396] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5035.779087] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 5035.779097] rtl8192ee: 
[ 5035.779100] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5056.465092] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 5056.465159] rtl8192ee: 
[ 5056.465163] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5059.853535] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 5059.853545] rtl8192ee: 
[ 5059.853548] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5092.931529] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 5092.931596] rtl8192ee: 
[ 5092.931599] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5095.965212] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 5095.965222] rtl8192ee: 
[ 5095.965225] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5129.478096] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 5129.478163] rtl8192ee: 
[ 5129.478167] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5132.076902] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 5132.076912] rtl8192ee: 
[ 5132.076916] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5233.576481] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 5233.576547] rtl8192ee: 
[ 5233.576551] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5236.399552] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 5236.399562] rtl8192ee: 
[ 5236.399565] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5339.725141] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 5339.725209] rtl8192ee: 
[ 5339.725213] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5342.728400] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 5342.728410] rtl8192ee: 
[ 5342.728414] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5447.843952] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 5447.843968] rtl8192ee: 
[ 5447.843971] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5451.063451] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 5451.063460] rtl8192ee: 
[ 5451.063464] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5557.964901] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 5557.964969] rtl8192ee: 
[ 5557.964972] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5561.404702] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 5561.404712] rtl8192ee: 
[ 5561.404716] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5670.088183] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 5670.088250] rtl8192ee: 
[ 5670.088253] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5673.752163] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 5673.752173] rtl8192ee: 
[ 5673.752176] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5784.133512] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 5784.133579] rtl8192ee: 
[ 5784.133583] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5788.105840] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 5788.105849] rtl8192ee: 
[ 5788.105853] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5837.351403] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 2, mac: ff:ff:ff:ff:ff:ff
[ 5837.351419] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 5837.351426] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[ 5837.351433] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 5837.351439] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[ 5837.351446] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:2, ulKeyId=2, ulEncAlg=4, ulUseDK=0 MacAddr ff:ff:ff:ff:ff:ff
[ 5837.351453] rtlwifi: 
[ 5837.352536] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end 
[ 5837.352601] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 5837.352662] rtlwifi-0:rtl_lps_set_psmode():<200-1> FW LPS leave ps_mode:0
[ 5837.352722] rtl8192ee: 
[ 5837.352725] In process "wpa_supplicant" (pid 888):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5840.267154] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 5840.267164] rtl8192ee: 
[ 5840.267167] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5877.846165] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 5877.846233] rtl8192ee: 
[ 5877.846237] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5880.391253] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 5880.391263] rtl8192ee: 
[ 5880.391267] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5900.293169] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 5900.293237] rtl8192ee: 
[ 5900.293241] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5902.459500] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 5902.459509] rtl8192ee: 
[ 5902.459513] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5914.146710] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 5914.146778] rtl8192ee: 
[ 5914.146782] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5916.502930] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 5916.502940] rtl8192ee: 
[ 5916.502944] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5986.817443] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 5986.817510] rtl8192ee: 
[ 5986.817514] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 5990.732503] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 5990.732513] rtl8192ee: 
[ 5990.732517] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6023.404439] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 6023.404505] rtl8192ee: 
[ 6023.404508] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6026.844191] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 6026.844201] rtl8192ee: 
[ 6026.844205] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6053.964160] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 6053.964228] rtl8192ee: 
[ 6053.964231] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6056.937258] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 6056.937268] rtl8192ee: 
[ 6056.937272] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6089.957831] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 6089.957898] rtl8192ee: 
[ 6089.957902] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6093.048943] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 6093.048953] rtl8192ee: 
[ 6093.048957] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6126.133761] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 6126.133829] rtl8192ee: 
[ 6126.133832] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6129.160631] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 6129.160641] rtl8192ee: 
[ 6129.160644] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6138.554999] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 6138.555066] rtl8192ee: 
[ 6138.555070] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6141.197854] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 6141.197864] rtl8192ee: 
[ 6141.197867] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6160.885511] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 6160.885522] rtl8192ee: 
[ 6160.885523] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6163.266106] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 6163.266115] rtl8192ee: 
[ 6163.266119] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6193.075121] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 6193.075187] rtl8192ee: 
[ 6193.075191] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6195.365383] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 6195.365393] rtl8192ee: 
[ 6195.365396] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6229.057794] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 6229.057862] rtl8192ee: 
[ 6229.057866] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6231.477073] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 6231.477082] rtl8192ee: 
[ 6231.477086] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6259.822610] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 6259.822678] rtl8192ee: 
[ 6259.822681] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6263.576347] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 6263.576357] rtl8192ee: 
[ 6263.576361] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6275.697710] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 6275.697778] rtl8192ee: 
[ 6275.697781] In process "swapper/1" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6279.625980] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 6279.625990] rtl8192ee: 
[ 6279.625994] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6384.793604] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 6384.793666] rtl8192ee: 
[ 6384.793670] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6387.961037] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 6387.961047] rtl8192ee: 
[ 6387.961050] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6511.028326] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 6511.028395] rtl8192ee: 
[ 6511.028398] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6514.351934] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 6514.351943] rtl8192ee: 
[ 6514.351947] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6639.169145] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 6639.169213] rtl8192ee: 
[ 6639.169216] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6642.749026] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 6642.749036] rtl8192ee: 
[ 6642.749039] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6769.264105] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 6769.264173] rtl8192ee: 
[ 6769.264176] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6773.152293] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 6773.152303] rtl8192ee: 
[ 6773.152306] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6901.441282] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 6901.441349] rtl8192ee: 
[ 6901.441352] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 6903.555637] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 6903.555646] rtl8192ee: 
[ 6903.555650] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7035.556744] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 7035.556812] rtl8192ee: 
[ 7035.556815] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7037.971352] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7037.971362] rtl8192ee: 
[ 7037.971366] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7171.658310] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 7171.658378] rtl8192ee: 
[ 7171.658382] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7174.393267] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7174.393277] rtl8192ee: 
[ 7174.393281] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7309.906235] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 7309.906303] rtl8192ee: 
[ 7309.906307] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7312.821395] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7312.821405] rtl8192ee: 
[ 7312.821408] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7450.060255] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 7450.060323] rtl8192ee: 
[ 7450.060326] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7453.255718] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7453.255728] rtl8192ee: 
[ 7453.255731] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7592.120367] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 7592.120435] rtl8192ee: 
[ 7592.120439] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7595.696249] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7595.696258] rtl8192ee: 
[ 7595.696262] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7637.559764] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: ff:ff:ff:ff:ff:ff
[ 7637.559775] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 7637.559780] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 7637.559785] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[ 7637.559846] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 7637.559850] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[ 7637.559935] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: ff:ff:ff:ff:ff:ff
[ 7637.559941] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 7637.559944] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[ 7637.559949] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 7637.559953] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[ 7637.559957] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr ff:ff:ff:ff:ff:ff
[ 7637.559962] rtlwifi: 
[ 7637.560938] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end 
[ 7637.561000] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 7637.561061] rtlwifi-0:rtl_lps_set_psmode():<200-1> FW LPS leave ps_mode:0
[ 7637.561122] rtl8192ee: 
[ 7637.561125] In process "wpa_supplicant" (pid 888):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7639.832753] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7639.832763] rtl8192ee: 
[ 7639.832766] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7651.242397] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 7651.242464] rtl8192ee: 
[ 7651.242467] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7653.876187] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7653.876197] rtl8192ee: 
[ 7653.876200] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7687.418957] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 7687.419026] rtl8192ee: 
[ 7687.419029] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7689.987868] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7689.987878] rtl8192ee: 
[ 7689.987881] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7721.863562] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 7721.863629] rtl8192ee: 
[ 7721.863632] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7724.093353] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7724.093363] rtl8192ee: 
[ 7724.093367] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7736.262770] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 7736.262838] rtl8192ee: 
[ 7736.262842] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7740.142983] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7740.142993] rtl8192ee: 
[ 7740.142997] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7758.051044] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 7758.051113] rtl8192ee: 
[ 7758.051116] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7760.205030] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7760.205040] rtl8192ee: 
[ 7760.205043] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7794.255735] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 7794.255802] rtl8192ee: 
[ 7794.255806] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7796.316718] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7796.316727] rtl8192ee: 
[ 7796.316731] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7830.436577] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 7830.436644] rtl8192ee: 
[ 7830.436648] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7834.434591] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7834.434601] rtl8192ee: 
[ 7834.434604] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7866.726522] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 7866.726591] rtl8192ee: 
[ 7866.726594] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7870.546235] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7870.546246] rtl8192ee: 
[ 7870.546250] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7882.519498] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 7882.519566] rtl8192ee: 
[ 7882.519570] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7884.589686] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7884.589696] rtl8192ee: 
[ 7884.589699] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7902.903192] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 7902.903259] rtl8192ee: 
[ 7902.903263] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7906.657964] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7906.657974] rtl8192ee: 
[ 7906.657978] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7939.090352] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 7939.090419] rtl8192ee: 
[ 7939.090423] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7942.769655] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7942.769665] rtl8192ee: 
[ 7942.769668] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7975.380146] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 7975.380214] rtl8192ee: 
[ 7975.380217] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 7978.881310] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 7978.881320] rtl8192ee: 
[ 7978.881324] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8011.772550] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8011.772618] rtl8192ee: 
[ 8011.772622] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8014.993025] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8014.993034] rtl8192ee: 
[ 8014.993038] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8030.618266] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 8030.618339] rtl8192ee: 
[ 8030.618347] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8033.048867] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8033.048877] rtl8192ee: 
[ 8033.048881] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8047.868656] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8047.868724] rtl8192ee: 
[ 8047.868727] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8051.104693] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8051.104703] rtl8192ee: 
[ 8051.104707] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8084.055672] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8084.055740] rtl8192ee: 
[ 8084.055743] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8087.216394] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8087.216404] rtl8192ee: 
[ 8087.216407] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8120.345692] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8120.345759] rtl8192ee: 
[ 8120.345762] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8123.328077] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8123.328087] rtl8192ee: 
[ 8123.328091] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8156.521906] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8156.521974] rtl8192ee: 
[ 8156.521977] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8159.439761] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8159.439771] rtl8192ee: 
[ 8159.439774] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8180.751235] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 8180.751302] rtl8192ee: 
[ 8180.751306] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8183.514219] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8183.514229] rtl8192ee: 
[ 8183.514233] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8192.709570] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8192.709637] rtl8192ee: 
[ 8192.709640] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8195.551450] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8195.551460] rtl8192ee: 
[ 8195.551463] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8228.805252] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8228.805320] rtl8192ee: 
[ 8228.805323] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8231.663128] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8231.663138] rtl8192ee: 
[ 8231.663141] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8264.992472] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8264.992539] rtl8192ee: 
[ 8264.992543] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8267.774816] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8267.774826] rtl8192ee: 
[ 8267.774829] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8301.168940] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8301.169007] rtl8192ee: 
[ 8301.169011] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8303.886503] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8303.886512] rtl8192ee: 
[ 8303.886516] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8333.014506] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 8333.014573] rtl8192ee: 
[ 8333.014576] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8335.985787] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8335.985796] rtl8192ee: 
[ 8335.985800] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8336.649380] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8336.649447] rtl8192ee: 
[ 8336.649451] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8339.998191] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8339.998201] rtl8192ee: 
[ 8339.998205] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8372.826321] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8372.826389] rtl8192ee: 
[ 8372.826392] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8376.109872] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8376.109883] rtl8192ee: 
[ 8376.109886] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8409.116426] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8409.116494] rtl8192ee: 
[ 8409.116497] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8412.221562] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8412.221572] rtl8192ee: 
[ 8412.221575] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8445.406060] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8445.406128] rtl8192ee: 
[ 8445.406132] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8448.333247] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8448.333257] rtl8192ee: 
[ 8448.333261] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8481.696077] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8481.696144] rtl8192ee: 
[ 8481.696147] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8484.444925] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8484.444935] rtl8192ee: 
[ 8484.444939] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8487.119933] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 8487.120011] rtl8192ee: 
[ 8487.120016] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8490.463550] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8490.463560] rtl8192ee: 
[ 8490.463564] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8517.791395] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8517.791462] rtl8192ee: 
[ 8517.791466] In process "gdbus" (pid 1684):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8520.556614] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8520.556623] rtl8192ee: 
[ 8520.556627] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8553.967974] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8553.968042] rtl8192ee: 
[ 8553.968046] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8556.668278] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8556.668288] rtl8192ee: 
[ 8556.668292] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8590.155621] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8590.155688] rtl8192ee: 
[ 8590.155692] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8592.779973] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8592.779984] rtl8192ee: 
[ 8592.779987] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8626.445323] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8626.445390] rtl8192ee: 
[ 8626.445393] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8628.891655] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8628.891665] rtl8192ee: 
[ 8628.891669] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8643.275515] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 8643.275582] rtl8192ee: 
[ 8643.275586] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8646.947496] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8646.947506] rtl8192ee: 
[ 8646.947509] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8662.643651] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8662.643718] rtl8192ee: 
[ 8662.643721] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8665.003340] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8665.003350] rtl8192ee: 
[ 8665.003353] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8698.933581] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8698.933648] rtl8192ee: 
[ 8698.933652] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8701.115029] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8701.115039] rtl8192ee: 
[ 8701.115042] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8735.223470] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8735.223537] rtl8192ee: 
[ 8735.223540] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8737.226714] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8737.226724] rtl8192ee: 
[ 8737.226728] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8771.399770] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8771.399839] rtl8192ee: 
[ 8771.399842] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8775.344601] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8775.344611] rtl8192ee: 
[ 8775.344615] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8801.465352] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 8801.465419] rtl8192ee: 
[ 8801.465422] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8805.437668] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8805.437678] rtl8192ee: 
[ 8805.437681] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8807.689847] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8807.689915] rtl8192ee: 
[ 8807.689919] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8811.456284] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8811.456294] rtl8192ee: 
[ 8811.456297] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8843.877204] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8843.877271] rtl8192ee: 
[ 8843.877274] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8847.567967] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8847.567977] rtl8192ee: 
[ 8847.567981] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8880.167218] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8880.167285] rtl8192ee: 
[ 8880.167289] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8883.679655] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8883.679664] rtl8192ee: 
[ 8883.679668] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8916.262540] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8916.262555] rtl8192ee: 
[ 8916.262559] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8919.791341] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8919.791351] rtl8192ee: 
[ 8919.791355] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8952.552626] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8952.552693] rtl8192ee: 
[ 8952.552697] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8955.903022] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8955.903032] rtl8192ee: 
[ 8955.903036] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8961.641385] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 8961.641453] rtl8192ee: 
[ 8961.641457] In process "swapper/1" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8963.927834] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8963.927844] rtl8192ee: 
[ 8963.927848] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8987.704164] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 8987.704231] rtl8192ee: 
[ 8987.704235] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 8990.008499] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 8990.008509] rtl8192ee: 
[ 8990.008513] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9023.993820] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9023.993889] rtl8192ee: 
[ 9023.993892] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9026.120188] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9026.120198] rtl8192ee: 
[ 9026.120202] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9057.526520] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9057.526588] rtl8192ee: 
[ 9057.526591] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9060.225661] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9060.225671] rtl8192ee: 
[ 9060.225674] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9093.817166] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9093.817233] rtl8192ee: 
[ 9093.817237] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9096.337350] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9096.337360] rtl8192ee: 
[ 9096.337363] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9123.851621] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 9123.851687] rtl8192ee: 
[ 9123.851691] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9126.430418] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9126.430428] rtl8192ee: 
[ 9126.430432] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9130.106852] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9130.106921] rtl8192ee: 
[ 9130.106924] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9132.449030] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9132.449040] rtl8192ee: 
[ 9132.449044] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9166.488100] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9166.488169] rtl8192ee: 
[ 9166.488172] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9168.560715] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9168.560725] rtl8192ee: 
[ 9168.560728] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9202.778031] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9202.778099] rtl8192ee: 
[ 9202.778103] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9206.678606] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9206.678616] rtl8192ee: 
[ 9206.678620] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9238.773067] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9238.773131] rtl8192ee: 
[ 9238.773133] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9240.784090] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9240.784100] rtl8192ee: 
[ 9240.784103] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9274.947752] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9274.947819] rtl8192ee: 
[ 9274.947822] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9278.901976] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9278.901986] rtl8192ee: 
[ 9278.901990] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9287.984000] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 9287.984066] rtl8192ee: 
[ 9287.984070] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9290.939204] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9290.939214] rtl8192ee: 
[ 9290.939217] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9311.147326] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9311.147394] rtl8192ee: 
[ 9311.147397] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9315.013662] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9315.013672] rtl8192ee: 
[ 9315.013675] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9347.333485] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9347.333553] rtl8192ee: 
[ 9347.333557] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9351.125347] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9351.125357] rtl8192ee: 
[ 9351.125361] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9383.612598] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9383.612665] rtl8192ee: 
[ 9383.612668] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9387.237031] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9387.237042] rtl8192ee: 
[ 9387.237046] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9419.902060] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9419.902127] rtl8192ee: 
[ 9419.902130] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9423.348723] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9423.348733] rtl8192ee: 
[ 9423.348736] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9441.343640] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 2, mac: ff:ff:ff:ff:ff:ff
[ 9441.343651] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 9441.343656] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 9441.343661] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:2
[ 9441.343722] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 9441.343726] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010010 
[ 9441.343817] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 2, mac: ff:ff:ff:ff:ff:ff
[ 9441.343822] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 9441.343826] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[ 9441.343831] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 9441.343835] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[ 9441.343839] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:2, ulKeyId=2, ulEncAlg=4, ulUseDK=0 MacAddr ff:ff:ff:ff:ff:ff
[ 9441.343844] rtlwifi: 
[ 9441.344912] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end 
[ 9441.344977] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 9441.345040] rtlwifi-0:rtl_lps_set_psmode():<200-1> FW LPS leave ps_mode:0
[ 9441.345101] rtl8192ee: 
[ 9441.345103] In process "wpa_supplicant" (pid 888):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9443.410764] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9443.410774] rtl8192ee: 
[ 9443.410777] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9454.230695] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 9454.230763] rtl8192ee: 
[ 9454.230767] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9459.460399] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9459.460408] rtl8192ee: 
[ 9459.460412] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9492.380034] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9492.380102] rtl8192ee: 
[ 9492.380105] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9495.572085] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9495.572095] rtl8192ee: 
[ 9495.572098] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9528.566813] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9528.566880] rtl8192ee: 
[ 9528.566883] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9531.683767] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9531.683777] rtl8192ee: 
[ 9531.683780] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9564.764731] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9564.764799] rtl8192ee: 
[ 9564.764802] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9567.795445] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9567.795455] rtl8192ee: 
[ 9567.795458] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9600.952656] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9600.952723] rtl8192ee: 
[ 9600.952727] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9603.907127] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9603.907137] rtl8192ee: 
[ 9603.907140] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9622.399464] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 9622.399524] rtl8192ee: 
[ 9622.399525] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9625.975380] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9625.975389] rtl8192ee: 
[ 9625.975393] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9637.242241] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9637.242310] rtl8192ee: 
[ 9637.242313] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9640.018815] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9640.018825] rtl8192ee: 
[ 9640.018829] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9673.477416] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9673.477485] rtl8192ee: 
[ 9673.477488] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9676.130501] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9676.130511] rtl8192ee: 
[ 9676.130514] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9709.924615] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9709.924676] rtl8192ee: 
[ 9709.924680] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9712.242187] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9712.242197] rtl8192ee: 
[ 9712.242201] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9746.111770] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9746.111839] rtl8192ee: 
[ 9746.111842] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9748.353864] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9748.353874] rtl8192ee: 
[ 9748.353878] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9778.711323] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9778.711391] rtl8192ee: 
[ 9778.711394] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9782.459348] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9782.459358] rtl8192ee: 
[ 9782.459361] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9792.602545] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 9792.602613] rtl8192ee: 
[ 9792.602617] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9796.502783] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9796.502793] rtl8192ee: 
[ 9796.502796] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9813.965454] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9813.965521] rtl8192ee: 
[ 9813.965525] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9816.564827] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9816.564837] rtl8192ee: 
[ 9816.564841] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9850.255315] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9850.255383] rtl8192ee: 
[ 9850.255387] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9852.676511] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9852.676521] rtl8192ee: 
[ 9852.676524] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9886.350703] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9886.350769] rtl8192ee: 
[ 9886.350773] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9888.788202] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9888.788212] rtl8192ee: 
[ 9888.788216] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9922.640973] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9922.641040] rtl8192ee: 
[ 9922.641043] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9924.899879] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9924.899889] rtl8192ee: 
[ 9924.899892] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9958.930396] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9958.930464] rtl8192ee: 
[ 9958.930468] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9961.011567] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9961.011577] rtl8192ee: 
[ 9961.011581] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9964.759733] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 9964.759801] rtl8192ee: 
[ 9964.759804] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9967.030180] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9967.030190] rtl8192ee: 
[ 9967.030194] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9991.930000] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 9991.930068] rtl8192ee: 
[ 9991.930071] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[ 9995.117045] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 9995.117055] rtl8192ee: 
[ 9995.117059] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10028.219303] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10028.219370] rtl8192ee: 
[10028.219374] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10031.228732] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10031.228742] rtl8192ee: 
[10031.228745] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10064.508989] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10064.509056] rtl8192ee: 
[10064.509060] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10067.340409] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10067.340419] rtl8192ee: 
[10067.340422] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10096.493040] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10096.493108] rtl8192ee: 
[10096.493111] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10099.439691] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10099.439701] rtl8192ee: 
[10099.439705] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10132.589004] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10132.589071] rtl8192ee: 
[10132.589074] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10135.551370] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10135.551379] rtl8192ee: 
[10135.551383] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10138.903106] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[10138.903173] rtl8192ee: 
[10138.903177] In process "swapper/1" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10141.569992] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10141.570002] rtl8192ee: 
[10141.570005] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10168.765624] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10168.765692] rtl8192ee: 
[10168.765695] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10171.663056] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10171.663066] rtl8192ee: 
[10171.663069] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10204.953429] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10204.953496] rtl8192ee: 
[10204.953499] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10207.774744] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10207.774754] rtl8192ee: 
[10207.774758] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10241.243080] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10241.243147] rtl8192ee: 
[10241.243151] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10243.886426] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10243.886437] rtl8192ee: 
[10243.886441] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10277.532744] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10277.532811] rtl8192ee: 
[10277.532814] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10279.998097] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10279.998107] rtl8192ee: 
[10279.998110] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10313.515111] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10313.515178] rtl8192ee: 
[10313.515182] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10316.109797] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10316.109807] rtl8192ee: 
[10316.109811] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10320.110233] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[10320.110300] rtl8192ee: 
[10320.110304] In process "swapper/1" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10322.128404] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10322.128414] rtl8192ee: 
[10322.128418] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10345.305064] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10345.305131] rtl8192ee: 
[10345.305134] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10348.209071] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10348.209081] rtl8192ee: 
[10348.209086] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10381.586223] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10381.586290] rtl8192ee: 
[10381.586293] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10384.320755] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10384.320765] rtl8192ee: 
[10384.320768] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10454.174683] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10454.174745] rtl8192ee: 
[10454.174748] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10456.544121] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10456.544130] rtl8192ee: 
[10456.544134] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10490.464698] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10490.464765] rtl8192ee: 
[10490.464768] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10492.655811] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10492.655821] rtl8192ee: 
[10492.655825] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10498.338093] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[10498.338160] rtl8192ee: 
[10498.338163] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10500.680631] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10500.680640] rtl8192ee: 
[10500.680644] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10521.412949] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10521.413016] rtl8192ee: 
[10521.413019] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10524.755082] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10524.755092] rtl8192ee: 
[10524.755096] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10557.702842] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10557.702912] rtl8192ee: 
[10557.702917] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10560.866753] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10560.866762] rtl8192ee: 
[10560.866766] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10587.443607] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10587.443674] rtl8192ee: 
[10587.443677] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10590.959828] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10590.959838] rtl8192ee: 
[10590.959842] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10623.646513] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10623.646581] rtl8192ee: 
[10623.646584] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10627.071506] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10627.071517] rtl8192ee: 
[10627.071520] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10660.136151] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10660.136220] rtl8192ee: 
[10660.136224] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10663.183199] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10663.183209] rtl8192ee: 
[10663.183213] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10673.554648] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[10673.554716] rtl8192ee: 
[10673.554719] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10677.226627] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10677.226637] rtl8192ee: 
[10677.226640] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10694.877172] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10694.877240] rtl8192ee: 
[10694.877243] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10697.288679] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10697.288689] rtl8192ee: 
[10697.288692] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10731.167332] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10731.167399] rtl8192ee: 
[10731.167403] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10733.400367] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10733.400377] rtl8192ee: 
[10733.400381] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10767.446227] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10767.446293] rtl8192ee: 
[10767.446297] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10769.512048] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10769.512058] rtl8192ee: 
[10769.512061] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10803.633580] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10803.633647] rtl8192ee: 
[10803.633650] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10807.629938] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10807.629947] rtl8192ee: 
[10807.629951] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10836.745430] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10836.745498] rtl8192ee: 
[10836.745502] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10839.729218] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10839.729228] rtl8192ee: 
[10839.729231] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10855.786904] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[10855.786972] rtl8192ee: 
[10855.786975] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10859.791259] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10859.791269] rtl8192ee: 
[10859.791272] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10873.035438] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10873.035505] rtl8192ee: 
[10873.035508] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10875.841022] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10875.841036] rtl8192ee: 
[10875.841042] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10909.134700] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10909.134766] rtl8192ee: 
[10909.134770] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10911.952582] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10911.952591] rtl8192ee: 
[10911.952595] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10945.000107] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10945.000174] rtl8192ee: 
[10945.000177] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10948.064274] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10948.064284] rtl8192ee: 
[10948.064287] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10981.184260] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[10981.184327] rtl8192ee: 
[10981.184330] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[10984.175949] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[10984.175958] rtl8192ee: 
[10984.175962] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11017.477080] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11017.477147] rtl8192ee: 
[11017.477151] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11020.287636] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11020.287646] rtl8192ee: 
[11020.287649] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11039.909246] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[11039.909312] rtl8192ee: 
[11039.909316] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11042.355888] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11042.355897] rtl8192ee: 
[11042.355900] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11053.573058] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11053.573125] rtl8192ee: 
[11053.573128] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11056.399323] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11056.399332] rtl8192ee: 
[11056.399336] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11089.863218] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11089.863285] rtl8192ee: 
[11089.863289] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11092.511001] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11092.511011] rtl8192ee: 
[11092.511015] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11126.142157] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11126.142224] rtl8192ee: 
[11126.142227] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11128.622685] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11128.622695] rtl8192ee: 
[11128.622699] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11162.534598] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11162.534667] rtl8192ee: 
[11162.534671] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11164.734374] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11164.734383] rtl8192ee: 
[11164.734387] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11196.263326] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11196.263393] rtl8192ee: 
[11196.263397] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11198.839852] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11198.839862] rtl8192ee: 
[11198.839865] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11226.113867] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[11226.113933] rtl8192ee: 
[11226.113937] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11228.932925] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11228.932935] rtl8192ee: 
[11228.932938] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11229.487330] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11229.487397] rtl8192ee: 
[11229.487400] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11232.945337] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11232.945347] rtl8192ee: 
[11232.945350] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11241.549756] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: ff:ff:ff:ff:ff:ff
[11241.549767] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[11241.549772] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[11241.549777] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[11241.549837] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[11241.549841] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[11241.549928] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: ff:ff:ff:ff:ff:ff
[11241.549933] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[11241.549937] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[11241.549942] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[11241.549946] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[11241.549950] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr ff:ff:ff:ff:ff:ff
[11241.549955] rtlwifi: 
[11241.551022] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end 
[11241.551088] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[11241.551148] rtlwifi-0:rtl_lps_set_psmode():<200-1> FW LPS leave ps_mode:0
[11241.551205] rtl8192ee: 
[11241.551208] In process "wpa_supplicant" (pid 888):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11244.982562] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11244.982571] rtl8192ee: 
[11244.982575] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11265.776498] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11265.776566] rtl8192ee: 
[11265.776569] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11269.057011] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11269.057021] rtl8192ee: 
[11269.057024] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11301.874532] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11301.874598] rtl8192ee: 
[11301.874602] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11305.168701] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11305.168711] rtl8192ee: 
[11305.168715] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11338.345418] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11338.345480] rtl8192ee: 
[11338.345483] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11341.280395] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11341.280405] rtl8192ee: 
[11341.280409] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11374.635467] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11374.635534] rtl8192ee: 
[11374.635538] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11377.392072] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11377.392082] rtl8192ee: 
[11377.392086] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11410.823277] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11410.823344] rtl8192ee: 
[11410.823347] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11413.503748] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11413.503758] rtl8192ee: 
[11413.503762] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11419.366240] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[11419.366307] rtl8192ee: 
[11419.366311] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11421.528578] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11421.528588] rtl8192ee: 
[11421.528592] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11446.509400] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11446.509467] rtl8192ee: 
[11446.509471] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11449.615428] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11449.615438] rtl8192ee: 
[11449.615441] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11482.798714] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11482.798782] rtl8192ee: 
[11482.798785] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11485.727131] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11485.727140] rtl8192ee: 
[11485.727144] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11519.089191] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11519.089258] rtl8192ee: 
[11519.089262] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11521.838807] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11521.838816] rtl8192ee: 
[11521.838820] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11555.264899] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11555.264966] rtl8192ee: 
[11555.264970] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11557.950496] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11557.950506] rtl8192ee: 
[11557.950509] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11591.566264] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11591.566332] rtl8192ee: 
[11591.566335] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11594.062171] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11594.062181] rtl8192ee: 
[11594.062184] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11604.625832] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[11604.625900] rtl8192ee: 
[11604.625903] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11608.105606] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11608.105617] rtl8192ee: 
[11608.105621] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11627.743110] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11627.743177] rtl8192ee: 
[11627.743181] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11630.173842] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11630.173853] rtl8192ee: 
[11630.173856] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11664.033471] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11664.033538] rtl8192ee: 
[11664.033542] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11666.285539] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11666.285549] rtl8192ee: 
[11666.285552] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11700.219333] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11700.219400] rtl8192ee: 
[11700.219403] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11702.397225] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11702.397235] rtl8192ee: 
[11702.397238] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11736.509474] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11736.509542] rtl8192ee: 
[11736.509545] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11738.508911] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11738.508921] rtl8192ee: 
[11738.508925] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11772.492872] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11772.492940] rtl8192ee: 
[11772.492943] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11774.620598] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11774.620608] rtl8192ee: 
[11774.620612] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11796.740951] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[11796.741017] rtl8192ee: 
[11796.741020] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11800.701255] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11800.701265] rtl8192ee: 
[11800.701269] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11808.677673] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11808.677740] rtl8192ee: 
[11808.677744] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11810.732277] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11810.732287] rtl8192ee: 
[11810.732290] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11881.258791] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11881.258858] rtl8192ee: 
[11881.258862] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11884.961850] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11884.961860] rtl8192ee: 
[11884.961863] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11917.548466] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11917.548533] rtl8192ee: 
[11917.548537] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11921.073536] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11921.073546] rtl8192ee: 
[11921.073550] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11948.108231] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11948.108298] rtl8192ee: 
[11948.108301] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11951.166595] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11951.166602] rtl8192ee: 
[11951.166605] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11984.285991] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[11984.286059] rtl8192ee: 
[11984.286062] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11987.278293] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11987.278303] rtl8192ee: 
[11987.278306] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11991.050483] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[11991.050546] rtl8192ee: 
[11991.050549] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[11993.296895] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[11993.296905] rtl8192ee: 
[11993.296908] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12020.472291] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12020.472358] rtl8192ee: 
[12020.472361] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12023.389978] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12023.389988] rtl8192ee: 
[12023.389992] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12056.567952] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12056.568021] rtl8192ee: 
[12056.568024] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12059.501655] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12059.501665] rtl8192ee: 
[12059.501669] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12092.755341] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12092.755408] rtl8192ee: 
[12092.755412] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12095.613339] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12095.613349] rtl8192ee: 
[12095.613353] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12129.046496] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12129.046564] rtl8192ee: 
[12129.046567] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12131.725024] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12131.725034] rtl8192ee: 
[12131.725038] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12165.326150] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12165.326217] rtl8192ee: 
[12165.326220] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12167.836715] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12167.836725] rtl8192ee: 
[12167.836729] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12187.250093] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[12187.250160] rtl8192ee: 
[12187.250164] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12189.904967] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12189.904977] rtl8192ee: 
[12189.904981] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12201.511957] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12201.512024] rtl8192ee: 
[12201.512027] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12203.948401] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12203.948411] rtl8192ee: 
[12203.948415] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12237.905570] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12237.905639] rtl8192ee: 
[12237.905642] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12240.060079] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12240.060088] rtl8192ee: 
[12240.060092] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12274.001553] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12274.001622] rtl8192ee: 
[12274.001625] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12276.171762] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12276.171772] rtl8192ee: 
[12276.171775] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12310.187769] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12310.187836] rtl8192ee: 
[12310.187840] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12312.283449] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12312.283458] rtl8192ee: 
[12312.283462] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12346.467493] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12346.467561] rtl8192ee: 
[12346.467564] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12350.401343] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12350.401353] rtl8192ee: 
[12350.401356] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12382.756238] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12382.756306] rtl8192ee: 
[12382.756309] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12386.513026] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12386.513035] rtl8192ee: 
[12386.513039] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12390.385290] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[12390.385358] rtl8192ee: 
[12390.385361] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12392.531639] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12392.531649] rtl8192ee: 
[12392.531653] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12418.943457] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12418.943524] rtl8192ee: 
[12418.943528] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12422.624659] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12422.624668] rtl8192ee: 
[12422.624672] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12450.517839] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12450.517901] rtl8192ee: 
[12450.517905] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12452.717787] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12452.717796] rtl8192ee: 
[12452.717800] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12486.705339] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12486.705406] rtl8192ee: 
[12486.705409] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12488.829470] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12488.829480] rtl8192ee: 
[12488.829484] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12522.749631] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12522.749697] rtl8192ee: 
[12522.749701] In process "syndaemon" (pid 1781):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12524.941148] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12524.941157] rtl8192ee: 
[12524.941161] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12559.091472] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12559.091539] rtl8192ee: 
[12559.091542] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12563.059046] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12563.059056] rtl8192ee: 
[12563.059060] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12585.703968] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[12585.704031] rtl8192ee: 
[12585.704034] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12589.139690] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12589.139700] rtl8192ee: 
[12589.139704] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12595.381830] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12595.381897] rtl8192ee: 
[12595.381901] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12599.170714] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12599.170724] rtl8192ee: 
[12599.170727] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12631.557346] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12631.557414] rtl8192ee: 
[12631.557418] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12635.282392] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12635.282402] rtl8192ee: 
[12635.282405] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12663.041033] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12663.041100] rtl8192ee: 
[12663.041103] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12665.375472] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12665.375482] rtl8192ee: 
[12665.375486] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12699.330728] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12699.330795] rtl8192ee: 
[12699.330799] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12701.487152] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12701.487162] rtl8192ee: 
[12701.487165] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12735.619861] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12735.619929] rtl8192ee: 
[12735.619933] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12739.605040] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12739.605051] rtl8192ee: 
[12739.605054] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12771.898717] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12771.898784] rtl8192ee: 
[12771.898787] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12775.716728] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12775.716737] rtl8192ee: 
[12775.716741] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12787.830093] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[12787.830161] rtl8192ee: 
[12787.830164] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12791.766364] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12791.766374] rtl8192ee: 
[12791.766377] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12808.200357] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12808.200424] rtl8192ee: 
[12808.200427] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12811.828412] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12811.828421] rtl8192ee: 
[12811.828425] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12844.489390] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12844.489458] rtl8192ee: 
[12844.489461] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12847.940102] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12847.940111] rtl8192ee: 
[12847.940115] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12880.780420] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12880.780488] rtl8192ee: 
[12880.780492] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12884.051779] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12884.051788] rtl8192ee: 
[12884.051792] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12916.956997] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12916.957065] rtl8192ee: 
[12916.957068] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12920.163466] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12920.163475] rtl8192ee: 
[12920.163479] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12950.183740] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12950.183807] rtl8192ee: 
[12950.183810] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12952.262738] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12952.262748] rtl8192ee: 
[12952.262752] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12980.422880] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[12980.422948] rtl8192ee: 
[12980.422952] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12984.362019] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12984.362029] rtl8192ee: 
[12984.362033] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12992.054520] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[12992.054587] rtl8192ee: 
[12992.054591] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[12994.393035] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[12994.393045] rtl8192ee: 
[12994.393048] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13016.599050] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13016.599117] rtl8192ee: 
[13016.599121] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13020.473696] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13020.473705] rtl8192ee: 
[13020.473708] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13045.334773] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 2, mac: ff:ff:ff:ff:ff:ff
[13045.334785] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[13045.334790] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[13045.334795] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:2
[13045.334855] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[13045.334859] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010010 
[13045.334944] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 2, mac: ff:ff:ff:ff:ff:ff
[13045.334949] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[13045.334953] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[13045.334958] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[13045.334962] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[13045.334966] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:2, ulKeyId=2, ulEncAlg=4, ulUseDK=0 MacAddr ff:ff:ff:ff:ff:ff
[13045.334970] rtlwifi: 
[13045.335946] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end 
[13045.336007] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[13045.336069] rtlwifi-0:rtl_lps_set_psmode():<200-1> FW LPS leave ps_mode:0
[13045.336130] rtl8192ee: 
[13045.336133] In process "wpa_supplicant" (pid 888):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13048.560569] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13048.560579] rtl8192ee: 
[13048.560583] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13052.889303] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13052.889370] rtl8192ee: 
[13052.889373] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13056.585383] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13056.585393] rtl8192ee: 
[13056.585397] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13089.076491] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13089.076559] rtl8192ee: 
[13089.076562] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13092.697067] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13092.697077] rtl8192ee: 
[13092.697080] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13125.468796] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13125.468864] rtl8192ee: 
[13125.468867] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13128.808755] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13128.808765] rtl8192ee: 
[13128.808768] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13161.670025] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13161.670092] rtl8192ee: 
[13161.670096] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13164.920441] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13164.920450] rtl8192ee: 
[13164.920454] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13197.967545] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13197.967612] rtl8192ee: 
[13197.967615] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13201.032119] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13201.032128] rtl8192ee: 
[13201.032132] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13208.356216] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[13208.356283] rtl8192ee: 
[13208.356287] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13211.063140] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13211.063150] rtl8192ee: 
[13211.063154] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13234.145065] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13234.145132] rtl8192ee: 
[13234.145136] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13237.143805] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13237.143815] rtl8192ee: 
[13237.143818] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13270.320856] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13270.320918] rtl8192ee: 
[13270.320922] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13273.255490] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13273.255500] rtl8192ee: 
[13273.255503] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13306.508135] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13306.508202] rtl8192ee: 
[13306.508205] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13309.367176] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13309.367185] rtl8192ee: 
[13309.367189] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13342.798204] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13342.798271] rtl8192ee: 
[13342.798274] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13345.478856] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13345.478866] rtl8192ee: 
[13345.478870] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13379.087828] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13379.087895] rtl8192ee: 
[13379.087899] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13381.590548] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13381.590558] rtl8192ee: 
[13381.590562] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13406.558030] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[13406.558098] rtl8192ee: 
[13406.558101] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13409.677414] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13409.677424] rtl8192ee: 
[13409.677427] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13415.378164] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13415.378231] rtl8192ee: 
[13415.378234] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13417.702234] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13417.702244] rtl8192ee: 
[13417.702247] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13451.667812] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13451.667879] rtl8192ee: 
[13451.667883] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13453.813885] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13453.813895] rtl8192ee: 
[13453.813899] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13484.996687] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13484.996756] rtl8192ee: 
[13484.996759] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13487.919399] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13487.919409] rtl8192ee: 
[13487.919413] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13521.274733] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13521.274800] rtl8192ee: 
[13521.274804] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13524.031076] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13524.031086] rtl8192ee: 
[13524.031090] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13557.576631] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13557.576698] rtl8192ee: 
[13557.576701] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13560.142756] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13560.142766] rtl8192ee: 
[13560.142769] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13593.751993] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13593.752060] rtl8192ee: 
[13593.752064] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13596.254441] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13596.254451] rtl8192ee: 
[13596.254454] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13616.757028] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[13616.757101] rtl8192ee: 
[13616.757107] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13620.328897] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13620.328907] rtl8192ee: 
[13620.328910] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13630.041618] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13630.041685] rtl8192ee: 
[13630.041688] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13632.366127] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13632.366137] rtl8192ee: 
[13632.366140] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13666.331685] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13666.331752] rtl8192ee: 
[13666.331755] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13668.477804] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13668.477814] rtl8192ee: 
[13668.477817] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13702.621456] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13702.621523] rtl8192ee: 
[13702.621527] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13706.595701] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13706.595710] rtl8192ee: 
[13706.595714] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13738.823670] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13738.823738] rtl8192ee: 
[13738.823741] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13742.707380] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13742.707390] rtl8192ee: 
[13742.707394] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13775.212422] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13775.212489] rtl8192ee: 
[13775.212493] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13778.819067] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13778.819076] rtl8192ee: 
[13778.819080] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13807.708994] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13807.709062] rtl8192ee: 
[13807.709066] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13810.918342] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13810.918352] rtl8192ee: 
[13810.918356] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13844.101668] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13844.101736] rtl8192ee: 
[13844.101739] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13847.030030] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13847.030039] rtl8192ee: 
[13847.030043] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13880.483596] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13880.483663] rtl8192ee: 
[13880.483666] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13883.141704] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13883.141714] rtl8192ee: 
[13883.141718] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13916.773062] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13916.773125] rtl8192ee: 
[13916.773128] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13919.253394] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13919.253404] rtl8192ee: 
[13919.253408] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13953.165657] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13953.165724] rtl8192ee: 
[13953.165727] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13955.365082] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13955.365092] rtl8192ee: 
[13955.365095] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13989.557703] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[13989.557771] rtl8192ee: 
[13989.557774] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[13993.482972] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[13993.482982] rtl8192ee: 
[13993.482986] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14025.847461] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14025.847528] rtl8192ee: 
[14025.847531] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14029.594658] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14029.594667] rtl8192ee: 
[14029.594671] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14043.209661] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[14043.209729] rtl8192ee: 
[14043.209732] In process "swapper/1" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14045.644289] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14045.644299] rtl8192ee: 
[14045.644302] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14062.137524] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14062.137592] rtl8192ee: 
[14062.137595] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14065.706340] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14065.706350] rtl8192ee: 
[14065.706353] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14098.529934] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14098.530001] rtl8192ee: 
[14098.530004] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14101.818017] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14101.818027] rtl8192ee: 
[14101.818031] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14133.088031] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14133.088098] rtl8192ee: 
[14133.088101] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14135.923501] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14135.923512] rtl8192ee: 
[14135.923516] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14169.378009] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14169.378076] rtl8192ee: 
[14169.378079] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14172.035180] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14172.035190] rtl8192ee: 
[14172.035193] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14196.236325] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14196.236394] rtl8192ee: 
[14196.236397] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14200.122049] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14200.122058] rtl8192ee: 
[14200.122062] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14232.628723] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14232.628791] rtl8192ee: 
[14232.628794] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14236.233732] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14236.233742] rtl8192ee: 
[14236.233746] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14259.479327] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[14259.479395] rtl8192ee: 
[14259.479399] In process "swapper/1" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14262.314397] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14262.314407] rtl8192ee: 
[14262.314410] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14268.918873] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14268.918942] rtl8192ee: 
[14268.918945] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14272.345422] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14272.345432] rtl8192ee: 
[14272.345436] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14305.208748] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14305.208815] rtl8192ee: 
[14305.208819] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14308.457107] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14308.457116] rtl8192ee: 
[14308.457120] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14341.601006] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14341.601074] rtl8192ee: 
[14341.601077] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14344.568785] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14344.568793] rtl8192ee: 
[14344.568796] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14377.880000] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14377.880068] rtl8192ee: 
[14377.880072] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14380.680477] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14380.680487] rtl8192ee: 
[14380.680491] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14414.169870] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14414.169938] rtl8192ee: 
[14414.169942] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14416.792153] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14416.792163] rtl8192ee: 
[14416.792167] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14450.562219] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14450.562286] rtl8192ee: 
[14450.562290] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14452.903846] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14452.903856] rtl8192ee: 
[14452.903860] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14477.735181] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[14477.735249] rtl8192ee: 
[14477.735252] In process "swapper/1" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14480.990708] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14480.990718] rtl8192ee: 
[14480.990722] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14486.967859] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14486.967928] rtl8192ee: 
[14486.967931] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14489.015513] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14489.015523] rtl8192ee: 
[14489.015526] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14523.460354] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14523.460369] rtl8192ee: 
[14523.460373] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14527.133407] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14527.133417] rtl8192ee: 
[14527.133420] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14559.750413] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14559.750475] rtl8192ee: 
[14559.750478] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14563.245094] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14563.245104] rtl8192ee: 
[14563.245108] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14596.142886] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14596.142953] rtl8192ee: 
[14596.142956] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14599.356781] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14599.356791] rtl8192ee: 
[14599.356795] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14632.535045] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14632.535112] rtl8192ee: 
[14632.535115] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14635.468469] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14635.468479] rtl8192ee: 
[14635.468482] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14668.927425] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14668.927487] rtl8192ee: 
[14668.927491] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14671.580143] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14671.580153] rtl8192ee: 
[14671.580156] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14697.977209] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[14697.977271] rtl8192ee: 
[14697.977275] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14701.673218] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14701.673228] rtl8192ee: 
[14701.673231] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14705.217698] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14705.217765] rtl8192ee: 
[14705.217769] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14707.691830] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14707.691840] rtl8192ee: 
[14707.691844] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14741.599194] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14741.599262] rtl8192ee: 
[14741.599266] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14743.803517] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14743.803526] rtl8192ee: 
[14743.803530] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14777.991409] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14777.991477] rtl8192ee: 
[14777.991481] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14781.921403] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14781.921413] rtl8192ee: 
[14781.921417] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14814.384015] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14814.384083] rtl8192ee: 
[14814.384086] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14818.037097] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14818.037107] rtl8192ee: 
[14818.037110] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14845.541488] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: ff:ff:ff:ff:ff:ff
[14845.541499] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[14845.541504] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[14845.541508] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[14845.541569] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[14845.541573] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[14845.541661] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: ff:ff:ff:ff:ff:ff
[14845.541667] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[14845.541671] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[14845.541676] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[14845.541680] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[14845.541684] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr ff:ff:ff:ff:ff:ff
[14845.541689] rtlwifi: 
[14845.542667] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end 
[14845.542729] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[14845.542790] rtlwifi-0:rtl_lps_set_psmode():<200-1> FW LPS leave ps_mode:0
[14845.542851] rtl8192ee: 
[14845.542854] In process "wpa_supplicant" (pid 888):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14848.130229] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14848.130240] rtl8192ee: 
[14848.130244] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14850.776249] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14850.776316] rtl8192ee: 
[14850.776320] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14854.148709] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14854.148718] rtl8192ee: 
[14854.148722] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14887.271127] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14887.271195] rtl8192ee: 
[14887.271198] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14890.260460] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14890.260470] rtl8192ee: 
[14890.260474] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14917.318362] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14917.318428] rtl8192ee: 
[14917.318432] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14920.353532] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14920.353542] rtl8192ee: 
[14920.353546] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14925.186889] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[14925.186957] rtl8192ee: 
[14925.186960] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14928.378350] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14928.378360] rtl8192ee: 
[14928.378364] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14953.608575] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14953.608642] rtl8192ee: 
[14953.608645] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14956.465216] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14956.465226] rtl8192ee: 
[14956.465230] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14989.898376] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[14989.898444] rtl8192ee: 
[14989.898447] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[14992.576903] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[14992.576912] rtl8192ee: 
[14992.576916] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15026.280034] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15026.280101] rtl8192ee: 
[15026.280104] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15028.688546] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15028.688550] rtl8192ee: 
[15028.688551] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15061.954925] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15061.954992] rtl8192ee: 
[15061.954995] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15064.800273] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15064.800283] rtl8192ee: 
[15064.800287] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15098.249333] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15098.249400] rtl8192ee: 
[15098.249403] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15100.911948] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15100.911958] rtl8192ee: 
[15100.911962] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15134.739511] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15134.739579] rtl8192ee: 
[15134.739582] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15137.023643] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15137.023654] rtl8192ee: 
[15137.023658] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15144.483890] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[15144.483957] rtl8192ee: 
[15144.483961] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15147.054660] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15147.054670] rtl8192ee: 
[15147.054673] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15171.029572] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15171.029641] rtl8192ee: 
[15171.029644] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15173.135323] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15173.135333] rtl8192ee: 
[15173.135337] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15207.330122] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15207.330189] rtl8192ee: 
[15207.330193] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15211.253215] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15211.253225] rtl8192ee: 
[15211.253229] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15243.619922] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15243.619989] rtl8192ee: 
[15243.619992] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15247.364898] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15247.364908] rtl8192ee: 
[15247.364911] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15280.115139] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15280.115206] rtl8192ee: 
[15280.115210] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15283.476494] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15283.476503] rtl8192ee: 
[15283.476506] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15316.508271] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15316.508338] rtl8192ee: 
[15316.508341] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15319.588253] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15319.588263] rtl8192ee: 
[15319.588266] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15352.899481] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15352.899549] rtl8192ee: 
[15352.899552] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15355.699957] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15355.699967] rtl8192ee: 
[15355.699970] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15370.700478] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[15370.700546] rtl8192ee: 
[15370.700549] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15373.755799] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15373.755809] rtl8192ee: 
[15373.755813] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15389.292379] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15389.292447] rtl8192ee: 
[15389.292450] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15391.811638] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15391.811648] rtl8192ee: 
[15391.811652] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15425.673766] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15425.673830] rtl8192ee: 
[15425.673832] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15427.923324] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15427.923334] rtl8192ee: 
[15427.923337] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15462.066409] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15462.066476] rtl8192ee: 
[15462.066480] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15466.041196] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15466.041206] rtl8192ee: 
[15466.041209] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15498.356125] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15498.356192] rtl8192ee: 
[15498.356195] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15502.152895] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15502.152905] rtl8192ee: 
[15502.152909] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15534.645972] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15534.646040] rtl8192ee: 
[15534.646043] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15538.264585] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15538.264595] rtl8192ee: 
[15538.264598] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15571.038218] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15571.038286] rtl8192ee: 
[15571.038289] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15574.376263] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15574.376272] rtl8192ee: 
[15574.376276] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15598.951315] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[15598.951384] rtl8192ee: 
[15598.951387] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15602.463122] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15602.463131] rtl8192ee: 
[15602.463135] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15604.161032] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15604.161099] rtl8192ee: 
[15604.161103] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15606.475500] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15606.475505] rtl8192ee: 
[15606.475506] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15638.196168] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15638.196235] rtl8192ee: 
[15638.196238] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15640.580996] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15640.581006] rtl8192ee: 
[15640.581010] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15674.485515] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15674.485583] rtl8192ee: 
[15674.485586] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15676.692699] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15676.692708] rtl8192ee: 
[15676.692712] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15706.778253] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15706.778316] rtl8192ee: 
[15706.778319] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15708.791976] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15708.791986] rtl8192ee: 
[15708.791990] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15743.169973] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15743.170041] rtl8192ee: 
[15743.170044] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15746.909862] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15746.909872] rtl8192ee: 
[15746.909876] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15779.563315] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15779.563382] rtl8192ee: 
[15779.563385] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15783.021548] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15783.021558] rtl8192ee: 
[15783.021562] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15816.056867] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15816.056934] rtl8192ee: 
[15816.056938] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15819.133226] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15819.133235] rtl8192ee: 
[15819.133239] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15829.268417] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[15829.268484] rtl8192ee: 
[15829.268487] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15833.176662] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15833.176671] rtl8192ee: 
[15833.176675] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15852.347131] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15852.347198] rtl8192ee: 
[15852.347201] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15855.244920] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15855.244930] rtl8192ee: 
[15855.244933] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15888.740737] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15888.740805] rtl8192ee: 
[15888.740808] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15891.356600] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15891.356609] rtl8192ee: 
[15891.356613] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15925.131542] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15925.131609] rtl8192ee: 
[15925.131613] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15927.468251] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15927.468260] rtl8192ee: 
[15927.468263] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15954.758546] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15954.758613] rtl8192ee: 
[15954.758616] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15957.561332] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15957.561343] rtl8192ee: 
[15957.561346] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15991.151186] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[15991.151254] rtl8192ee: 
[15991.151257] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[15993.673034] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[15993.673044] rtl8192ee: 
[15993.673047] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16027.543955] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16027.544023] rtl8192ee: 
[16027.544027] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16029.784721] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16029.784731] rtl8192ee: 
[16029.784735] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16058.502458] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16058.502525] rtl8192ee: 
[16058.502528] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16061.883994] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16061.884004] rtl8192ee: 
[16061.884007] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16066.505119] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[16066.505187] rtl8192ee: 
[16066.505190] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16069.908815] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16069.908825] rtl8192ee: 
[16069.908829] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16090.589209] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16090.589276] rtl8192ee: 
[16090.589280] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16093.983266] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16093.983276] rtl8192ee: 
[16093.983280] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16126.981682] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16126.981749] rtl8192ee: 
[16126.981753] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16130.094956] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16130.094966] rtl8192ee: 
[16130.094969] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16163.363296] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16163.363363] rtl8192ee: 
[16163.363367] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16166.206639] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16166.206649] rtl8192ee: 
[16166.206652] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16199.755816] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16199.755883] rtl8192ee: 
[16199.755886] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16202.318322] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16202.318331] rtl8192ee: 
[16202.318335] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16236.148126] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16236.148193] rtl8192ee: 
[16236.148196] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16238.430006] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16238.430016] rtl8192ee: 
[16238.430019] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16268.451587] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16268.451655] rtl8192ee: 
[16268.451659] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16270.529285] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16270.529295] rtl8192ee: 
[16270.529298] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16295.668951] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[16295.669017] rtl8192ee: 
[16295.669020] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16298.616149] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16298.616159] rtl8192ee: 
[16298.616162] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16304.843306] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16304.843374] rtl8192ee: 
[16304.843377] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16308.647171] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16308.647181] rtl8192ee: 
[16308.647184] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16341.236481] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16341.236549] rtl8192ee: 
[16341.236553] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16344.758858] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16344.758867] rtl8192ee: 
[16344.758871] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16377.628003] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16377.628070] rtl8192ee: 
[16377.628073] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16380.870552] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16380.870562] rtl8192ee: 
[16380.870565] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16413.952783] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16413.952849] rtl8192ee: 
[16413.952853] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16416.982227] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16416.982237] rtl8192ee: 
[16416.982241] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16450.358941] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16450.359008] rtl8192ee: 
[16450.359011] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16453.093915] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16453.093924] rtl8192ee: 
[16453.093928] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16486.775173] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16486.775240] rtl8192ee: 
[16486.775244] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16489.205603] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16489.205612] rtl8192ee: 
[16489.205616] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16523.094861] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16523.094928] rtl8192ee: 
[16523.094932] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16525.317288] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16525.317298] rtl8192ee: 
[16525.317301] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16531.992665] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[16531.992732] rtl8192ee: 
[16531.992736] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16535.348312] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16535.348322] rtl8192ee: 
[16535.348325] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16554.687185] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16554.687253] rtl8192ee: 
[16554.687256] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16557.416544] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16557.416553] rtl8192ee: 
[16557.416557] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16627.399622] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16627.399691] rtl8192ee: 
[16627.399694] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16629.639926] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16629.639936] rtl8192ee: 
[16629.639940] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16649.326675] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 2, mac: ff:ff:ff:ff:ff:ff
[16649.326687] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[16649.326692] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[16649.326697] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:2
[16649.326756] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[16649.326760] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010010 
[16649.326848] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 2, mac: ff:ff:ff:ff:ff:ff
[16649.326853] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[16649.326857] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[16649.326862] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[16649.326866] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[16649.326870] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:2, ulKeyId=2, ulEncAlg=4, ulUseDK=0 MacAddr ff:ff:ff:ff:ff:ff
[16649.326875] rtlwifi: 
[16649.327850] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end 
[16649.327910] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[16649.327972] rtlwifi-0:rtl_lps_set_psmode():<200-1> FW LPS leave ps_mode:0
[16649.328033] rtl8192ee: 
[16649.328035] In process "wpa_supplicant" (pid 888):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16651.708168] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16651.708178] rtl8192ee: 
[16651.708182] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16663.795775] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16663.795842] rtl8192ee: 
[16663.795846] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16667.757777] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16667.757783] rtl8192ee: 
[16667.757785] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16696.413350] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[16696.413418] rtl8192ee: 
[16696.413421] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16699.857083] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16699.857092] rtl8192ee: 
[16699.857096] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16700.189856] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16700.189924] rtl8192ee: 
[16700.189927] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16703.869493] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16703.869501] rtl8192ee: 
[16703.869504] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16736.574367] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16736.574435] rtl8192ee: 
[16736.574439] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16739.981182] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16739.981192] rtl8192ee: 
[16739.981196] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16770.302550] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[16770.302618] rtl8192ee: 
[16770.302621] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16776.092861] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16776.092871] rtl8192ee: 
[16776.092875] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16809.405391] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16809.405458] rtl8192ee: 
[16809.405461] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16812.204549] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16812.204559] rtl8192ee: 
[16812.204563] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16845.496027] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16845.496094] rtl8192ee: 
[16845.496098] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16848.316237] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16848.316247] rtl8192ee: 
[16848.316250] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16881.902167] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16881.902236] rtl8192ee: 
[16881.902240] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16884.427915] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16884.427925] rtl8192ee: 
[16884.427929] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16918.278305] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16918.278372] rtl8192ee: 
[16918.278375] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16920.539599] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16920.539609] rtl8192ee: 
[16920.539612] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16954.684436] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16954.684505] rtl8192ee: 
[16954.684508] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16958.657482] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16958.657492] rtl8192ee: 
[16958.657495] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16989.317312] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[16989.317379] rtl8192ee: 
[16989.317382] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[16992.762919] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[16992.762928] rtl8192ee: 
[16992.762932] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[17010.486491] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[17010.486559] rtl8192ee: 
[17010.486563] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[17012.825012] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[17012.825022] rtl8192ee: 
[17012.825025] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[17025.713019] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[17025.713086] rtl8192ee: 
[17025.713090] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[17028.874657] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[17028.874666] rtl8192ee: 
[17028.874670] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[17061.176858] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[17061.176925] rtl8192ee: 
[17061.176928] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 
[17064.986335] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[17064.986345] rtl8192ee: 
[17064.986348] In process "kworker/0:2" (pid 6224):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode 

```

ping:
```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms


```

All the time I have valid IP address, proper netmask and gateway.

---

### Post by chili555 on 2014-04-20
One maybe last thing to try:```
sudo modprobe -r rtl8192ee
sudo modprobe rtl8192ee swenc=1
```Better? Worse? Same??

We are rapidly running low on options, I'm afraid.

---

### Post by strsljen on 2014-04-20
Hi!

No change, unfortunately.

I will try at work on Tuesday.Maybe few heads can think of something. Or not. :)

Thank you very much for your help. I will keep you posted after we play with it on Tuesday.

I'm not sure qhat is the problem. SO far I can only conclude that driver is not working, although is present.

---

### Post by strsljen on 2014-04-21
Hi!

Looks like I have even bigger problems with Lenovo L540: whitelisted BIOS regarding WLAN adapters.
I put D-Link WLAN USB adapter from my PC and Ubuntu won't use it at all. 

```
[   48.675902] usb 3-2: new high-speed USB device number 4 using xhci_hcd
[   48.693918] usb 3-2: New USB device found, idVendor=2001, idProduct=330d
[   48.693922] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   48.693924] usb 3-2: Product: 802.11n WLAN Adapter
[   48.693925] usb 3-2: Manufacturer: Realtek
[   48.693926] usb 3-2: SerialNumber: 00e04c000001
```


I disabled onboard WLAN in BIOS and when I insert D-link USB WLAN adapter, nm-tool shows nothing:

```

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        54:EE:75:09:6D:42

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```


So, either I make this onboard WLAN adapter to work, or get BIOS image without these limitations, or I can't use Ubuntu on it (which would be shame)

Best regards,

--
Strs

---

### Post by strsljen on 2014-04-21
And another update: if windows 7 is installed on that laptop, there are drivers to be downloaded from Lenovo website which actually work properly.

Also, Huawei mobile broadband USB adapter works correctly (with manufacturer's driver) on windows 7. This solves the mistery of possible whitelist problem (there is none).

It doesn't change the fact that with Ubuntu 14.04 I can't get mobile or wireless network operating. :(

---

### Post by chili555 on 2014-04-21
> So, either I make this onboard WLAN adapter to work, or get BIOS image without these limitations, It ain't done until Chili says it's done. Just because you inserted the USB and you didn't instantly connect doesn't mean we're done.

Please insert the USB and run:```
sudo -i
modprobe rtl8192cu
echo "2001 330D" > /sys/bus/usb/drivers/rtl8192cu/new_id
exit
```Was a wireless interface created, possibly wlan1?```
iwconfig
```Does it scan?```
sudo iwlist wlan1 scan
```Of course, substitute the interface you found, if not wlan1.

If it scans, it probably connects.

---

### Post by strsljen on 2014-04-24
Hi!

I found another usb wireless adapter that works. I have a workaround for now.

Btw, Im tracking this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1239578](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1239578)

Hopefully, Ubuntu will have driver for this chip in next kernel update.

---

