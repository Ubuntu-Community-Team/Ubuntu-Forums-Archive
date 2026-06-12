---
title: "ndiswrapper Marvell 88w8335  intermittant problems"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by adityaj on 2008-02-22
Hi

I have a ndiswrapper enabled wireless connection on my ubuntu box. The network card seems to establish connection inconsistently. At times it establishes as soon as i boot up, or some time it requires two or three boots :(. I am not able to figure out why is it so erratic??

**lspci output**

```

01:03.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
```


**dmesg output**

```

[   35.651427] ndiswrapper version 1.45 loaded (smp=yes)
[   35.706461] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
[   35.706779] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 19 (level, low) -> IRQ 17
[   35.709372] ndiswrapper: using IRQ 17
[   35.974174] wlan0: ethernet device 00:1b:2f:2d:87:52 using NDIS driver: wg311v3, version: 0x3000036, NDIS version: 0x501, vendor: '', 11AB:1FAA.5.conf
[   35.974197] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   35.976633] usbcore: registered new interface driver ndiswrapper
```

**syslog output**

```
 NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
NetworkManager: <info>  Will activate connection 'wlan0/linksys'. 
NetworkManager: <info>  Device wlan0 activation scheduled... 
NetworkManager: <info>  Activation (wlan0) started... 
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
NetworkManager: <info>  Activation (wlan0/wireless): access point 'linksys' is unencrypted, no key needed. 
NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant2^I' 
NetworkManager: <info>  SUP: response was 'OK' 
NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
NetworkManager: <info>  SUP: response was 'OK' 
NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
NetworkManager: <info>  SUP: response was '0' 
NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6c696e6b737973' 
NetworkManager: <info>  SUP: response was 'OK' 
NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 scan_ssid 1' 
NetworkManager: <info>  SUP: response was 'OK' 
NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
NetworkManager: <info>  SUP: response was 'OK' 
NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
NetworkManager: <info>  SUP: response was 'OK' 
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), failing activation. 
NetworkManager: <info>  Activation (wlan0) failure scheduled... 
NetworkManager: <info>  Activation (wlan0) failed for access point (linksys) 
NetworkManager: <info>  Activation (wlan0) failed. 
NetworkManager: <info>  Deactivating device wlan0. 
NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
NetworkManager: <info>  SUP: response was 'TIMEOUT[CLI]' 
NetworkManager: <WARN>  nm_utils_supplicant_request_with_check(): supplicant_cleanup: supplicant error for 'DISABLE_NETWORK 0'.  Response: 'TIMEOUT[CLI]' 
NetworkManager: <WARN>  supplicant_cleanup(): supplicant_cleanup - couldn't disable network in supplicant_cleanup 
NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 

```

It seems to complete two stages then times out. What is the problem? I have no problem in windows. Also its not that the card has never worked. Its just inconsistent. Any suggestions?

Regards

Aditya

---

### Post by wieman01 on 2008-02-23
Just to say that I share the same frustration with a WUSB54G V4 on Kubuntu Feisty. It all started a few months ago and I have not found a solution yet. It seemed to work OK, but apparenly one of the updates has messed with 'ndiswrapper'.

---

### Post by adityaj on 2008-02-25
> **wieman01 said:**
> Just to say that I share the same frustration with a WUSB54G V4 on Kubuntu Feisty. It all started a few months ago and I have not found a solution yet. It seemed to work OK, but apparenly one of the updates has messed with 'ndiswrapper'.

Hi

Not sure if you have the same problem. I seemed to have fixed my issue. basically i 'debarred' NetworkManager from handling the wireless connection. Seems to work fine now.

Regards

Aditya

---

### Post by wieman01 on 2008-02-25
> **adityaj said:**
> Hi

Not sure if you have the same problem. I seemed to have fixed my issue. basically i 'debarred' NetworkManager from handling the wireless connection. Seems to work fine now.

Regards

Aditya
I have never used NM for the same reason. But thanks for your comment. :-)

---

