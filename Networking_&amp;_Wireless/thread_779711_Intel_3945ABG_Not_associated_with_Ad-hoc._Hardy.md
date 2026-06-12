---
title: "Intel 3945ABG Not associated with Ad-hoc. Hardy"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by DarkNekoRockman on 2008-05-02
Hello,

I'm beginner in Ubuntu, with the last distribution Ubuntu Gutsy Gibbon we have some troubles that can solve with Google, but when I make a clean install for Ubuntu Hardy Heron I get a trouble with my wireless card Intel 3945ABG. I try with the method of linux-backports-modules-hardy but dont work.
My card detect APs and detect my ad-hoc wlan, but not associated.
I see you a log of the wireless card.

My laptop name is "Gateway-Ubuntu", the ESSID is "Hardy", dont have encrypthion.


Thanks for your help and sorry for my bad english.

Regards,

```
Apr 26 17:19:13 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) started...
Apr 26 17:19:13 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 26 17:19:13 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 26 17:19:13 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 26 17:19:13 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 26 17:19:13 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 26 17:19:13 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'Hardy' is unencrypted, no key needed.
Apr 26 17:19:14 Gateway-Ubuntu NetworkManager: <info>  retry to connect to global supplicant socket (try=1)
Apr 26 17:19:14 Gateway-Ubuntu NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I'
Apr 26 17:19:14 Gateway-Ubuntu NetworkManager: <info>  SUP: response was 'OK'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: sending command 'AP_SCAN 2'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: response was 'OK'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: sending command 'ADD_NETWORK'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: response was '0'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4861726479'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: response was 'OK'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 mode 1'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: response was 'OK'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 frequency -1882967296'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: response was 'OK'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: response was 'OK'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: response was 'OK'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 26 17:19:21 Gateway-Ubuntu NetworkManager: <info>  Old device 'wlan0' activating, won't change.
Apr 26 17:19:51 Gateway-Ubuntu last message repeated 4 times
Apr 26 17:20:51 Gateway-Ubuntu last message repeated 7 times
Apr 26 17:21:11 Gateway-Ubuntu last message repeated 2 times
Apr 26 17:21:15 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>120s), failing activation.
Apr 26 17:21:15 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) failure scheduled...
Apr 26 17:21:15 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) failed for access point (Hardy)
Apr 26 17:21:15 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) failed.
Apr 26 17:21:15 Gateway-Ubuntu NetworkManager: <info>  Deactivating device wlan0.
Apr 26 17:21:15 Gateway-Ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'.
Apr 26 17:21:15 Gateway-Ubuntu NetworkManager: <info>  Will activate connection 'eth0'.  
```

```
  sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:c6:f2:65
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=10.10.11.2 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:0a:1b:85
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

```

---

### Post by Paris Heng on 2008-05-03
> **DarkNekoRockman said:**
> Hello,

I'm beginner in Ubuntu, with the last distribution Ubuntu Gutsy Gibbon we have some troubles that can solve with Google, but when I make a clean install for Ubuntu Hardy Heron I get a trouble with my wireless card Intel 3945ABG. I try with the method of linux-backports-modules-hardy but dont work.
My card detect APs and detect my ad-hoc wlan, but not associated.
I see you a log of the wireless card.

My laptop name is "Gateway-Ubuntu", the ESSID is "Hardy", dont have encrypthion.


Thanks for your help and sorry for my bad english.

Regards,

```
Apr 26 17:19:13 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) started...
Apr 26 17:19:13 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 26 17:19:13 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 26 17:19:13 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 26 17:19:13 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 26 17:19:13 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 26 17:19:13 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'Hardy' is unencrypted, no key needed.
Apr 26 17:19:14 Gateway-Ubuntu NetworkManager: <info>  retry to connect to global supplicant socket (try=1)
Apr 26 17:19:14 Gateway-Ubuntu NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I'
Apr 26 17:19:14 Gateway-Ubuntu NetworkManager: <info>  SUP: response was 'OK'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: sending command 'AP_SCAN 2'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: response was 'OK'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: sending command 'ADD_NETWORK'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: response was '0'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4861726479'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: response was 'OK'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 mode 1'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: response was 'OK'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 frequency -1882967296'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: response was 'OK'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: response was 'OK'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  SUP: response was 'OK'
Apr 26 17:19:15 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 26 17:19:21 Gateway-Ubuntu NetworkManager: <info>  Old device 'wlan0' activating, won't change.
Apr 26 17:19:51 Gateway-Ubuntu last message repeated 4 times
Apr 26 17:20:51 Gateway-Ubuntu last message repeated 7 times
Apr 26 17:21:11 Gateway-Ubuntu last message repeated 2 times
Apr 26 17:21:15 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>120s), failing activation.
Apr 26 17:21:15 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) failure scheduled...
Apr 26 17:21:15 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) failed for access point (Hardy)
Apr 26 17:21:15 Gateway-Ubuntu NetworkManager: <info>  Activation (wlan0) failed.
Apr 26 17:21:15 Gateway-Ubuntu NetworkManager: <info>  Deactivating device wlan0.
Apr 26 17:21:15 Gateway-Ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'.
Apr 26 17:21:15 Gateway-Ubuntu NetworkManager: <info>  Will activate connection 'eth0'.  
```

```
  sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:c6:f2:65
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=10.10.11.2 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:0a:1b:85
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

```

Are you trying to conenct to the Ad-hoc of other PC? If so, turns your wireless card into ad-hoc and set the same frequency and same ESSID to which the Ad-hoc PC that you wish to communicate.

---

### Post by jpcunha on 2008-05-03
I am having the same problem, maybe the new driver is still buggy... if anyone know a solution, let me know please..

---

### Post by carlkhabbaz on 2008-05-03
I have the same exact problem..

---

### Post by DarkNekoRockman on 2008-05-03
> **Paris Heng said:**
> Are you trying to conenct to the Ad-hoc of other PC? If so, turns your wireless card into ad-hoc and set the same frequency and same ESSID to which the Ad-hoc PC that you wish to communicate.

Yes, I try to connect to Ad-hoc of my wlan in my house, in Ubuntu 7.10 Gutsy Gibbon dont have any trouble to connected with the drivers ipw3945, but with the upgrade of iwl3945 I can not connect anymore to my ad-hoc lan.
I not try connect with another AP for now, but I afraid that can not too.:(

Regards,

---

### Post by eombah on 2008-05-03
I solved this by installing linux-backports-modules.

---

### Post by carlkhabbaz on 2008-05-03
solved by using ndiswrapper with the windows xp drivers provided by intel.com

---

