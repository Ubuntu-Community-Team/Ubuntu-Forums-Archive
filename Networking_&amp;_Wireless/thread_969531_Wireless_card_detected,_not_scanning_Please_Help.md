---
title: "Wireless card detected, not scanning? Please Help"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by HawkST on 2008-11-03
I have an Atheros card, and having downloaded the linux-backports-generic-intrepid thing, my wireless card is no recognized, and I have the option to 'Enable Wireless'.

However nothing shows up under the wireless network part when I left click the network icon - whereas in Hardy there would be 7 or 8 at a time.

I tried to connect to my network by creating a new network, but the bottom green light came on, nothing happen for ages then it asked for my password again (which had been correctly input the first time round).

iwconfig gives this

```
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Please help!

Also, what do the two green lights stand for when you connect to a network?

Edit to say I have a wireless button, but it doesnt appear to be working in Intrepid - is there anyway I can try turning it on via the terminal - it is meant to be enabled by default though

syslog gives this

```
Nov  3 19:05:18 sysadmin NetworkManager: <info>  Config: added 'ssid' value '******' 
Nov  3 19:05:18 sysadmin NetworkManager: <info>  Config: added 'mode' value '1' 
Nov  3 19:05:18 sysadmin NetworkManager: <info>  Config: added 'frequency' value '2412' 
Nov  3 19:05:18 sysadmin NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-NONE' 
Nov  3 19:05:18 sysadmin NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Nov  3 19:05:18 sysadmin NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Nov  3 19:05:18 sysadmin NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Nov  3 19:05:18 sysadmin NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Nov  3 19:05:18 sysadmin NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov  3 19:05:18 sysadmin NetworkManager: <info>  Config: set interface ap_scan to 2 
Nov  3 19:05:18 sysadmin NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Nov  3 19:05:43 sysadmin NetworkManager: <info>  Activation (wlan0/wireless): association took too long. 
Nov  3 19:05:43 sysadmin NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Nov  3 19:05:43 sysadmin NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets 
Nov  3 19:05:43 sysadmin NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 0 
Nov  3 19:05:47 sysadmin NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1512 (get_secrets_dialog_response_cb): canceled. 
Nov  3 19:05:47 sysadmin NetworkManager: <info>  (wlan0): device state change: 6 -> 9 
Nov  3 19:05:47 sysadmin NetworkManager: <info>  Activation (wlan0) failed for access point (******) 
Nov  3 19:05:47 sysadmin NetworkManager: <info>  Marking connection '******' invalid. 
Nov  3 19:05:47 sysadmin NetworkManager: <info>  Activation (wlan0) failed. 
Nov  3 19:05:47 sysadmin NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Nov  3 19:05:47 sysadmin NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
```

lshw -C network

```
 *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:c0:a8:f5:45:80
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

```

iwlist scan

```
wlan0     No scan results

```

---

### Post by HawkST on 2008-11-04
Desperation bump

---

### Post by superprash2003 on 2008-11-04
[http://ubuntuforums.org/showthread.php?t=766169&page=2](http://ubuntuforums.org/showthread.php?t=766169&page=2)

---

### Post by HawkST on 2008-11-04
> **superprash2003 said:**
> [http://ubuntuforums.org/showthread.php?t=766169&page=2](http://ubuntuforums.org/showthread.php?t=766169&page=2)

Hey man, thanks for trying to help, but the problem is not so much with the detection of the wireless card (I've followed 3 seperate tutorials which have got the system to recognize the card, yours was the third, even though its written for Hardy and I'm running Ibex), but what happens once the card is detected - it doesnt seem to be scanning at all.

iwlist scan returns 'No scan results', and nothing comes up when I left click the network manager icon.

I'm not sure what is going on, and really need some advice.

---

### Post by SickBoy on 2008-11-17
Same problem here. It's impossible to scan and to connect to a wifi although the wireless card seems to be correctly detected.

---

### Post by Serpentus on 2008-11-19
I have the same problem...no problem on 8.04, but after installing 8.10 I had wifi with no problem...But after an update to the network manager... I had no more Wifi support (It is recognized, but doesn't scan)....I uninstalled it and re installed the old one (knetwork), no luck.... So what can I do???? I'm stuck using Vista just because of this!!!! Maybe if someone can tell us how to completly uninstall (delete config files, or reconfigure them all) knetwork, network manager, etc..  

This latest ubuntu broke lots of things in my laptop... Wifi, sound (Broke with 8.04, I had sound on 7.10), bluetooth.... and the desktop effects...SO SLOW!!!! I had to disable it... It seams that to the new ubuntu a laptop of Dual Core 2 2.5GhHz, 2 GB RAM, and a Nvidia 8700GTM 512MB RAM not shared is an OLD n' SLOW laptop like a truck with 4 flat tires.... I'll have to go back to 7.10, but compiling and installing everything again, installing new libraries to support new software nad breaking and fixing installed software.... I rather ask here and see if somebody can help us solve this issue....

So, can someone help us? Please?
Thanks
Serpentus

P.S.: I know this is NOT the place to ask...but does somebody know how to auto hide the task bar in kde4???..it's driving me CRAZY!!!!! XP :lolflag:

---

### Post by daropl on 2008-11-19
I have also the same issue, but I have other WiFi card.

---

### Post by cleentrax on 2008-12-09
exactly the same problem as the original post, with an Aspire One running Intrepid 8.10. I had the wireless card up and running fine, but after a resume, wlan0 will not activate. I can enable and disable wireless, but cannot select a network.

iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by IQRules on 2008-12-09
Try search ath5k, modprobe, rmmod. Make sure the router can accept your NEW wireless Mac address. You need to pass '#iwlist eth1 scan", eth1 is the NIC card.

---

