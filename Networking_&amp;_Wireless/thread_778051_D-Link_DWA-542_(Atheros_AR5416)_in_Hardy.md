---
title: "D-Link DWA-542 (Atheros AR5416) in Hardy"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by dylanv on 2008-05-01
Hello all,

First, I am sorry to bother you all with yet another "My Wi-Fi card isn't detected" scenario. However, I have done my research beforehand, but still haven't had any luck. I have not been able to get my card (a D-Link DWA-542 a/b/g/n adapter with an Atheros AR5416 chipset) to work in either Gutsy or Hardy.

First of all, the card definitely doesn't "just work" with the Madwifi in the linux-restricted-modules package that is installed by default. I am running a completely fresh install of Ubuntu 8.04 LTS, in a dual-boot with Windows XP (the card works fine in XP). The lspci command detects the card properly.

I downloaded ndiswrapper-common, ndiswrapper-utils, and ndisgtk on another computer and installed them on my Hardy machine. They installed fine, and accepted the Windows drivers. However, after clicking 'Install' and selecting the drivers in ndisgtk, the card does not appear in the list of hardware. I was successful by using the ndiswrapper terminal command to install the drivers.

When the card is available in Network Manager, it can see the various SSIDs of access points located in my neighborhood. However, any attempt at connection to a router (secure or not) fails with the following log output:

```

Apr 30 19:19:15 DellDimensionB110 NetworkManager: <info>  Device wlan0 activation scheduled... 
Apr 30 19:19:15 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) started... 
Apr 30 19:19:15 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 30 19:19:15 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr 30 19:19:15 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 30 19:19:15 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr 30 19:19:15 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr 30 19:19:15 DellDimensionB110 NetworkManager: <info>  Activation (wlan0/wireless): access point 'PTDE' is encrypted, but NO valid key exists.  New key needed. 
Apr 30 19:19:15 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'PTDE'. 
Apr 30 19:19:15 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 30 19:19:32 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'PTDE' received. 
Apr 30 19:19:32 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 30 19:19:32 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr 30 19:19:32 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 30 19:19:32 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr 30 19:19:32 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr 30 19:19:32 DellDimensionB110 NetworkManager: <info>  Activation (wlan0/wireless): access point 'PTDE' is encrypted, and a key exists.  No new key needed. 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  SUP: response was '0' 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 50544445' 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 19:19:33 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 30 19:20:33 DellDimensionB110 NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), failing activation. 
Apr 30 19:20:33 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Apr 30 19:20:33 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) failed for access point (PTDE) 
Apr 30 19:20:33 DellDimensionB110 NetworkManager: <info>  Activation (wlan0) failed. 
Apr 30 19:20:33 DellDimensionB110 NetworkManager: <info>  Deactivating device wlan0. 
Apr 30 19:20:35 DellDimensionB110 NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 

```

(The machine's hostname is DellDimensionB110 and the desired SSID is 'PTDE'. I am writing this post on the same computer, in WinXP).

Furthermore, ndiswrapper does not persist across reboots. I must run "sudo modprobe ndiswrapper" and hit Ctrl-Alt-Backspace to get it to work.

Any help would be immensely appreciated. Thank you all in advance.

- Dylan

---

### Post by Simonft on 2008-05-29
Bump.

---

### Post by prshah on 2008-05-30
> **dylanv said:**
> 
When the card is available in Network Manager, it can see the various SSIDs of access points located in my neighborhood. However, any attempt at connection to a router (secure or not) fails

Furthermore, ndiswrapper does not persist across reboots. I must run "sudo modprobe ndiswrapper" and hit Ctrl-Alt-Backspace to get it to work.


Working in reverse;

EITHER: add the word "ndiswrapper" to the end of your /etc/modules
OR: add the phrase "modprobe ndiswrapper" to the _LAST_BUT_ONE_LINE_ (second last) of /etc/rc.local.

Both are protected files, you'll need to use sudo to edit them.

DONT DO BOTH. First option is better.

1st problem:

Can you try connecting to the wireless network manually (ie, via terminal)? ```

sudo ifup wlan0
sudo iwconfig wlan0 essid whatever
sudo dhclient wlan0
ping www.google.com
```

Please post errors/outputs if it doesn't work.

As a matter of interest, what does ```
sudo ndiswrapper -l
``` show?

---

