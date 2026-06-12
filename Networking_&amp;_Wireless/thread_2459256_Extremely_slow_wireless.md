---
title: "Extremely slow wireless"
date: 2021-03-14
forum: Networking &amp; Wireless
---

### Post by whytenoiz on 2021-03-14
ThinkPad X1 Carbon
Cannot achieve more than 20Mbit/s

Ubuntu 20.04
```
$ uname -r
5.8.0-44-generic
```

```
lshw -C Network
  *-network:0
       description: Wireless interface
       product: Wireless-AC 9462
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlp0s20f3
       version: 00
       serial: 00:42:38:c1:f7:05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.8.0-44-generic firmware=55.d9698065.0 QuZ-a0-hr-b0-55.u ip=192.168.0.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:ea238000-ea23bfff
```

```
~$ dmesg | grep iwl
[    3.185004] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[    3.200167] iwlwifi 0000:00:14.3: **Direct firmware load for iwlwifi-QuZ-a0-hr-b0-56.ucode failed with error -2**
[    3.201745] iwlwifi 0000:00:14.3: api flags index 2 larger than supported by driver
[    3.201755] iwlwifi 0000:00:14.3: TLV_FW_FSEQ_VERSION: FSEQ Version: 65.3.35.22
[    3.201758] iwlwifi 0000:00:14.3: Found debug destination: EXTERNAL_DRAM
[    3.201759] iwlwifi 0000:00:14.3: Found debug configuration: 0
[    3.202051] iwlwifi 0000:00:14.3: loaded firmware version 55.d9698065.0 QuZ-a0-hr-b0-55.ucode op_mode iwlmvm
[    3.205736] iwlwifi 0000:00:14.3: **Direct firmware load for iwl-debug-yoyo.bin failed with error -2**
[    3.275250] iwlwifi 0000:00:14.3: Detected Intel(R) Wi-Fi 6 AX201 160MHz, REV=0x354
[    3.455644] iwlwifi 0000:00:14.3: base HW address: 00:42:38:c1:f7:05
[    3.480680] iwlwifi 0000:00:14.3 wlp0s20f3: renamed from wlan0
```

~$ modinfo iwlwifi&#8203;
```
modinfo: ERROR: Module iwlwifi&#8203; not found.
```



What have I done :

Disable Power Mgmt
```
  iwconfig wlp0s20f3 power off
```

Disable IPv6
 ```
 sudo echo "#disable ipv6" >> /etc/sysctl.conf
  sudo echo "net.ipv6.conf.all.disable_ipv6 = 1" >> /etc/sysctl.conf
  sudo echo "net.ipv6.conf.default.disable_ipv6 = 1" >> /etc/sysctl.conf
  sudo echo "net.ipv6.conf.lo.disable_ipv6 = 1" >> /etc/sysctl.conf
```

Fix Nsswitch
```
  hosts:          files dns
```

Disable 802.11 in iwlwifi
```
  sudo echo "options iwlwifi 11n_disable=1" >> /etc/modprobe.d/iwlwifi.conf
```

Attempted to install Intel drivers :
```
$ sudo ls -lah /lib/firmware/iwlwifi-9000-pu-b0-jf-b0-34.ucode
-rw-r--r-- 1 root root 2.6M Mar 14 14:00 /lib/firmware/iwlwifi-9000-pu-b0-jf-b0-34.ucode
```

never once read / loaded on reboot.

I've even rolled back to previous kernels including one confirmed to have shipped with gen8 X1 Carbon w/ Ubuntu
No success. 

Any pointers would be greatly appreciated.

---

### Post by chili555 on 2021-03-14
```
Attempted to install Intel drivers :
Code:
$ sudo ls -lah /lib/firmware/iwlwifi-9000-pu-b0-jf-b0-34.ucode
-rw-r--r-- 1 root root 2.6M Mar 14 14:00 /lib/firmware/iwlwifi-9000-pu-b0-jf-b0[COLOR="#FF0000"]-34[/COLOR].ucode
```These are firmware files, not drivers. This step will be ineffective as the driver already found and loaded a much newer version:

> loaded firmware version 55.d9698065.0 QuZ-a0-hr-b0[COLOR="#FF0000"]-55[/COLOR].ucode op_mode iwlmvm


> Direct firmware load for iwl-debug-yoyo.bin failed with error -2Neither Google nor I are aware of either the existence of this file or any harm in its failure to load. My current speedtest is 260 Mbps and I have the same error. I suggest that you ignore it.

I strongly suspect that a possible issue is settings in the router. Please see posts #4 and #8 here: [https://ubuntuforums.org/showthread.php?t=2396035&highlight=firmware+iwlwifi](https://ubuntuforums.org/showthread.php?t=2396035&highlight=firmware+iwlwifi)

---

### Post by whytenoiz on 2021-03-15
Thank you for your reply.

**#4** My mistake, that should have been included in the original post as one of the steps I took. 
    REGDOMAIN=US

**#8** All APs are set to  VHT20 on 2.4Ghz and VHT20 on 5Ghz, Band Steering is disabled, Security proto is set to WPA-2. Static channels on 1, 6, 11, 40 and 100 (removed auto selection and ensured no duplication).  Reboot all APs and the USG3. 

Problem persists.

---

### Post by praseodym on 2021-03-15
Add the MAC address of the AP to connect to in the BSSID section of your profile. With equally named APs in 2,4 and 5 GHz region, "false" roaming could occur

---

### Post by whytenoiz on 2021-03-15
Assigning mac for 5Ghz AP resulted in 5.5Mbit/s
Assigning mac for 2.4Ghz AP resulted in 24.71 Mbit/s

---

### Post by chili555 on 2021-03-15
Are there any clues in the log?

```
sudo dmesg | grep -e iwl -e wlp
```

---

### Post by whytenoiz on 2021-03-16
After an incredible amount of frustration, you are exactly correct. My doubt placed in my expensive laptop running an excellent operating system was misplaced. The fault lay in the Ubiquiti network I have running here at home. Having shutdown as many APs as possible and stripping down to as simple a configuration as possible, I've come closer to resolving the issue. I suspect a hidden AI / automated config monitoring within the USG3. Still searching for that. 

My laptop is connected once again ( i did lose all connectivity yesterday afternoon ) and speeds are in excess of 160 Mbit/s while in close proximity to the UAP-AC-Pro [Ch. 6 VHT20 / Ch. 36 VHT40 No Band Steering, No Airtime Fairness, etc ]. 


Chili555, I appreciate your patience and all of your assistance.

Thank you all,

---

### Post by chili555 on 2021-03-16
Awesome! Glad to hear that it's working as expected. Please use Thread Tools at the top to mark Solved. The searchers will appreciate it.

---

