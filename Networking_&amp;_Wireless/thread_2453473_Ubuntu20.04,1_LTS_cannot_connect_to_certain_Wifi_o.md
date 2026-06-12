---
title: "Ubuntu20.04,1 LTS cannot connect to certain Wifi on thinkpad T480s"
date: 2020-11-11
forum: Networking &amp; Wireless
---

### Post by matdk37 on 2020-11-11
Hello everyone,
just upgraded my thinkpad T480s (IntelWireless 8265/8275) from 18.04 to 20.04 week ago.

And I found that I cant connect to my company's wifi network. (It does not disconnect but keeps trying connecting)
and if i put a wrong password it will tell me to enter my password.
But still i can connect to a mobile hotspot successfully. 

I guess the problem could be : Our company wifi uses 2.4G and 5G under the same SSID and we are using a WPA2-Enterprise authentication

so I tried the following solution and enabled only 2.4G
[https://ubuntuforums.org/showthread.php?t=2442177](https://ubuntuforums.org/showthread.php?t=2442177) 
 and also:
```
[COLOR=#000000][FONT=&amp]sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]systemctl restart network-manager.service[/FONT][/COLOR]
```
but the problem still exists, I checked BIOS setup also and secure boot is off

-----------------------------------------------------------------------------------------------------------------------------------------
OK, i can connect now if i assign an IP manually, although its slow...
some more infos:
**$ uname -a**  ```
Linux i-yu-t480s 5.4.0-53-generic #59-Ubuntu SMP Wed Oct 21 09:38:44 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

[B]$ sudo dmesg | grep iwlwifi
[/B]```
[    4.090938] iwlwifi 0000:3d:00.0: Found debug destination: EXTERNAL_DRAM
[    4.090941] iwlwifi 0000:3d:00.0: Found debug configuration: 0
[    4.091869] iwlwifi 0000:3d:00.0: loaded firmware version 36.77d01142.0 op_mode iwlmvm
[    4.168409] iwlwifi 0000:3d:00.0: Detected Intel(R) Dual Band Wireless AC 8265, REV=0x230
[    4.176999] iwlwifi 0000:3d:00.0: Applying debug destination EXTERNAL_DRAM
[    4.177358] iwlwifi 0000:3d:00.0: Allocated 0x00400000 bytes for firmware monitor.
[    4.258075] iwlwifi 0000:3d:00.0: base HW address: a4:c3:f0:01:c9:03
[    4.805442] iwlwifi 0000:3d:00.0 wlp61s0: renamed from wlan0
[    8.500285] iwlwifi 0000:3d:00.0: Applying debug destination EXTERNAL_DRAM
[    8.632914] iwlwifi 0000:3d:00.0: Applying debug destination EXTERNAL_DRAM
[    8.700804] iwlwifi 0000:3d:00.0: FW already configured (0) - re-configuring

```
[B]sudo lshw -C Network

[/B]
 ```
 *-network                 
       description: Wireless interface
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:3d:00.0
       logical name: wlp61s0
       version: 78
       serial: a4:c3:f0:01:c9:03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-53-generic firmware=36.77d01142.0 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:159 memory:e9100000-e9101fff

```

---

