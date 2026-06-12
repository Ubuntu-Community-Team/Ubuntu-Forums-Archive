---
title: "Atheros 5008/5418 driver detects networks, but does not connect"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by oab on 2008-08-27
I'm having a problem that searching through the forums (I used search before I posted) and I cannot find a solution for it.

I have a Thinkpad T60 (8744-5BU sku if that matters), with the "Thinkpad a/b/g/n wireless" card (Atheros chip 5008, detected as 5418 in linux, shows as using the 5416 driver in windows).

I have followed the ndiswrapper guide, it installed ndiswrapper off the 8.04 cd without error, I was able to find the correct windows XP driver, load it, and have it detect networks. That all works perfectly.

The problem is: it does not connect. I can have the popup screen say "please enter your passkey", I type it in (correctly), the connecting spinning wheel thing spins, and then asks me to re-enter my password again 30 seconds later or so.

It's a WPA-Personal network. I do have special characters in the passkey (although I do not imagine it would matter) and the actual network name.

What I have tried[LIST=1]
[*]I have blacklisted the modules as listed in the ndiswrapper wiki guide (and blacklisted and unblacklisted ath_pci/ath_hal) with re-boots in-between.
[*]I have tried two different versions of the driver (the one that works in my windows installation, and a d-link one due to the chipset being the same)
[*]configuring ndiswrapper graphically, and using the command-line config.
[/LIST]: 


I've run these command line checks, and as far as I can tell, it is working perfectly (yes, the switch on the laptop itself is turned on, and the little flashing radio light does blink):

```
robert@robert-T60:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
robert@robert-T60:~$ ndiswrapper -l
netathw : driver installed
	device (168C:0024) present
```

```
robert@robert-T60:~$ lsrobert@robert-T60:~$ sudo lshw -C Network
[sudo] password for robert: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
  *-network
       description: Wireless interface
       product: AR5418 802.11abgn Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:af:c4:6e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netathw driverversion=1.52+,01/17/2008,7.4.2.75 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

```
lspci | grep Network
03:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
```

```
robert@robert-T60:~$ tail -f /var/log/syslog
Aug 27 18:34:22 robert-T60 NetworkManager: <info>  Supplicant state changed: 0 
Aug 27 18:34:35 robert-T60 last message repeated 5 times
Aug 27 18:34:42 robert-T60 NetworkManager: <info>  wlan0: link timed out. 
Aug 27 18:34:42 robert-T60 NetworkManager: <info>  Activation (wlan0) New wireless user key request for network '[H]ome' was canceled. 
Aug 27 18:34:42 robert-T60 NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Aug 27 18:34:42 robert-T60 NetworkManager: <info>  Activation (wlan0) failed for access point ([H]ome) 
Aug 27 18:34:42 robert-T60 NetworkManager: <info>  Activation (wlan0) failed. 
Aug 27 18:34:42 robert-T60 NetworkManager: <info>  Deactivating device wlan0. 
Aug 27 18:34:42 robert-T60 avahi-daemon[5057]: Withdrawing address record for fe80::216:cfff:feaf:c46e on wlan0.
Aug 27 18:34:42 robert-T60 NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
```

While it is actually trying to connect to the network itself, here is what it looks like:
```
robert@robert-T60:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"[H]ome"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:9A:DC:70:F3   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Any ideas? Did I miss something totally obvious?

I am a novice at the nuts and bolts of linux, but I know my way around a [*nix] command line, and am not afraid to build packages myself (however the laptop I'm trying this on has no internet connection [hence me trying to get the wireless to work] so I cannot use any repositories easily on my windows PC).

---

### Post by oab on 2008-08-28
/been 24 hours
//bump
///sorry
////I hate doing that

---

### Post by DapperMe17 on 2008-08-28
Try installing Wicd from the repositories...if you have access via an ethernet cord.

Make sure that your wireless setting in "preferences" is "ath0". "ath0" is for Atheros cards.

You might choose to disable Network Manager.

Make sure ndiswrapper loads at startup.

Wicd can do wonders!

---

### Post by bigrob301 on 2009-11-16
try switching router security to wpa2  tkip + aes router needs to be wireless N compatible I've seen similar problem on the net

---

