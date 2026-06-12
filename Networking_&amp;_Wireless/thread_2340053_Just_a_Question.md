---
title: "Just a Question"
date: 2016-10-15
forum: Networking &amp; Wireless
---

### Post by mistcloud-misty on 2016-10-15
Yesterday, our Internet went down (in the area, not just for us) and came back up this morning. However, when I tried to get on my computer, I had an endless connection loop that never worked. I deleted the network info and re-connected and was able to connect to the network, but I had no actual connection (server not found, or error.hostname.notresolved) depending on the browser. Everyone else (not using Ubuntu, even using phones) connected just fine. Why couldn't I?

I had to reboot the modem just so I had connection again. 

Is there a reason for this or is it just an 'Ubuntu Quirk'?

---

### Post by RobGoss on 2016-10-15
Is your machine still connecting to your home network? if your power when out then that means your network devices / router just needed to be reset once that is done then everything should run as before as long as you did not make any changes to the configuration of your router

---

### Post by mistcloud-misty on 2016-10-15
It is connecting now, but required me to delete and re-add the network as well as restart the modem. Rebooting the computer (twice) didn't do anything. 

Prior to that it wouldn't connect at all to the network (until forgetting the network and starting over) and then wouldn't connect to the Internet, until rebooting the modem.

---

### Post by RobGoss on 2016-10-15
Do you have a steady connection now?

And if this a single installation or dual boot, The reason I was asking you is if it was in fact a dual boot with Windows, I was going to tell you to boot in to Windows and see if it stays connected to your network

---

### Post by ajgreeny on 2016-10-15
I suspect this was not related to your Ubuntu OS but entirely down to the router needing the reboot/reset.

I have had exactly the same happen here when, for no obvious reason, the web connection has disappeared, but I can still ping the router with no problem.  A power-down of the router, leave it 30 seconds, though I'm not sure if that is really needed, and  a power-up again has solved the connection problem.

---

### Post by mistcloud-misty on 2016-10-15
Unfortunately I'm having problems again - Internet stopped working altogether (hostname again) and I had to disconnect and reconnect several times. The graphical interface has crashed and it shows I'm disconnected when I am, but it's working (temporarily). Oddly enough both the nameservers I use with my ISP are pinging just fine, but I can't connect to the internet without using google's servers.

I suspect maybe there are till issues on the ISP's end and will give them a call.

---

### Post by lisati on 2016-10-15
> **ajgreeny said:**
> I suspect this was not related to your Ubuntu OS but entirely down to the router needing the reboot/reset.

I'm inclined to agree. 
I've occasionally had issues which required me to check the settings in my router, which had mysteriously reset themselves to out-of-the-box settings that are less than ideal for my connection. 

Restarting your router is a good place to start, followed by checking that everything is as it should be, such as the router's username and password for your internet connection.

---

### Post by mistcloud-misty on 2016-10-15
Another thought occurred to me. I am running a completely new kernel than I was prior to this. I found this in my kernel log at the time I lost connection (after having connection) and when the graphical interface for network manager crashed (still broken).

It looks like my USB network device 'disconnected' which isn't entirely abnormal:

 ```
Oct 15 12:48:56 arcane-X555LB kernel: [12544.620650] usb 1-2: USB disconnect, device number 2
Oct 15 12:48:56 arcane-X555LB kernel: [12544.637319] wlxf4f26d17b7ea: deauthenticating from 54:35:30:24:c5:ef by local choice (Reason: 3=DEAUTH_LEAVING)
Oct 15 12:48:56 arcane-X555LB NetworkManager[883]: <warn>  [1476550136.7741] sup-iface[0x126f2c0,wlxf4f26d17b7ea]: connection disconnected (reason -3)
Oct 15 12:48:56 arcane-X555LB kernel: [12544.737780] ath: phy0: Chip reset failed
Oct 15 12:48:56 arcane-X555LB kernel: [12544.737785] ath: phy0: Unable to reset channel (2437 Mhz) reset status -22
Oct 15 12:48:56 arcane-X555LB kernel: [12544.737787] ath: phy0: Unable to set channel
Oct 15 12:48:56 arcane-X555LB kernel: [12544.948379] ath: phy0: Failed to wakeup in 500us
Oct 15 12:48:57 arcane-X555LB NetworkManager[883]: <info>  [1476550137.1938] device (wlxf4f26d17b7ea): state change: activated -> unmanaged (reason 'removed') [100 10 36]

```

Then a little later: 
```
Oct 15 12:48:57 arcane-X555LB NetworkManager[883]: <info>  [1476550137.2263] dhcp4 (wlxf4f26d17b7ea): canceled DHCP transaction, DHCP client pid 9681
Oct 15 12:48:57 arcane-X555LB NetworkManager[883]: <info>  [1476550137.2264] dhcp4 (wlxf4f26d17b7ea): state changed bound -> done
Oct 15 12:48:57 arcane-X555LB NetworkManager[883]: <error> [1476550137.2373] platform-linux: do-change-link[3]: failure changing link: failure 19 (No such device)
Oct 15 12:48:57 arcane-X555LB NetworkManager[883]: <error> [1476550137.2374] platform-linux: do-change-link[3]: failure changing link: failure 19 (No such device)
Oct 15 12:48:57 arcane-X555LB NetworkManager[883]: <info>  [1476550137.2377] dns-mgr: Writing DNS information to /sbin/resolvconf
Oct 15 12:48:57 arcane-X555LB kernel: [12545.201365] usb 1-2: ath9k_htc: USB layer deinitialized
Oct 15 12:48:57 arcane-X555LB NetworkManager[883]: <info>  [1476550137.2473] manager: NetworkManager state is now CONNECTED_LOCAL
Oct 15 12:48:57 arcane-X555LB NetworkManager[883]: <info>  [1476550137.2475] manager: NetworkManager state is now DISCONNECTED
Oct 15 12:48:57 arcane-X555LB NetworkManager[883]: <error> [1476550137.3455] platform-linux: do-change-link[3]: failure changing link: failure 19 (No such device)
Oct 15 12:48:57 arcane-X555LB NetworkManager[883]: <warn>  [1476550137.3455] device (wlxf4f26d17b7ea): failed to disable userspace IPv6LL address handling
Oct 15 12:48:57 arcane-X555LB NetworkManager[883]: <info>  [1476550137.3456] radio killswitch /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/ieee80211/phy0/rfkill2 disappeared
Oct 15 12:48:57 arcane-X555LB NetworkManager[883]: <info>  [1476550137.3461] devices removed (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/wlxf4f26d17b7ea, iface: wlxf4f26d17b7ea)
Oct 15 12:48:59 arcane-X555LB kernel: [12547.673415] usb 1-2: new high-speed USB device number 6 using xhci_hcd
Oct 15 12:48:59 arcane-X555LB kernel: [12547.873889] usb 1-2: New USB device found, idVendor=0cf3, idProduct=9271
Oct 15 12:48:59 arcane-X555LB kernel: [12547.873892] usb 1-2: New USB device strings: Mfr=16, Product=32, SerialNumber=48
Oct 15 12:48:59 arcane-X555LB kernel: [12547.873893] usb 1-2: Product: USB2.0 WLAN
Oct 15 12:48:59 arcane-X555LB kernel: [12547.873895] usb 1-2: Manufacturer: ATHEROS
Oct 15 12:48:59 arcane-X555LB kernel: [12547.873896] usb 1-2: SerialNumber: 12345
Oct 15 12:48:59 arcane-X555LB kernel: [12547.874373] usb 1-2: ath9k_htc: Firmware ath9k_htc/htc_9271-1.4.0.fw requested
Oct 15 12:49:00 arcane-X555LB kernel: [12548.156044] usb 1-2: ath9k_htc: Transferred FW: ath9k_htc/htc_9271-1.4.0.fw, size: 51008
Oct 15 12:49:00 arcane-X555LB kernel: [12548.407703] ath9k_htc 1-2:1.0: ath9k_htc: HTC initialized with 33 credits
Oct 15 12:49:00 arcane-X555LB kernel: [12548.671082] ath9k_htc 1-2:1.0: ath9k_htc: FW Version: 1.4
Oct 15 12:49:00 arcane-X555LB kernel: [12548.671090] ath9k_htc 1-2:1.0: FW RMW support: On
Oct 15 12:49:00 arcane-X555LB kernel: [12548.671095] ath: EEPROM regdomain: 0x809c
Oct 15 12:49:00 arcane-X555LB kernel: [12548.671097] ath: EEPROM indicates we should expect a country code
Oct 15 12:49:00 arcane-X555LB kernel: [12548.671100] ath: doing EEPROM country->regdmn map search
Oct 15 12:49:00 arcane-X555LB kernel: [12548.671103] ath: country maps to regdmn code: 0x52
Oct 15 12:49:00 arcane-X555LB kernel: [12548.671105] ath: Country alpha2 being used: CN
Oct 15 12:49:00 arcane-X555LB kernel: [12548.671108] ath: Regpair used: 0x52
Oct 15 12:49:00 arcane-X555LB NetworkManager[883]: <info>  [1476550140.7115] (wlan0): using nl80211 for WiFi device control
Oct 15 12:49:00 arcane-X555LB NetworkManager[883]: <info>  [1476550140.7117] device (wlan0): driver supports Access Point (AP) mode
Oct 15 12:49:00 arcane-X555LB kernel: [12548.675769] ieee80211 phy1: Atheros AR9271 Rev:1
Oct 15 12:49:00 arcane-X555LB NetworkManager[883]: <info>  [1476550140.7128] manager: (wlan0): new 802.11 WiFi device (/org/freedesktop/NetworkManager/Devices/3)
Oct 15 12:49:00 arcane-X555LB kernel: [12548.681289] cfg80211: Current regulatory domain intersected:
Oct 15 12:49:00 arcane-X555LB kernel: [12548.681292] cfg80211:  DFS Master region: FCC
Oct 15 12:49:00 arcane-X555LB kernel: [12548.681293] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Oct 15 12:49:00 arcane-X555LB kernel: [12548.681294] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Oct 15 12:49:00 arcane-X555LB kernel: [12548.681296] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 1700 mBm), (N/A)
Oct 15 12:49:00 arcane-X555LB kernel: [12548.681297] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
Oct 15 12:49:00 arcane-X555LB kernel: [12548.681298] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
Oct 15 12:49:00 arcane-X555LB kernel: [12548.681299] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
Oct 15 12:49:00 arcane-X555LB kernel: [12548.681300] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Oct 15 12:49:00 arcane-X555LB kernel: [12548.883422] ath9k_htc 1-2:1.0 wlxf4f26d17b7ea: renamed from wlan0
Oct 15 12:49:00 arcane-X555LB NetworkManager[883]: <info>  [1476550140.9239] rfkill3: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/ieee80211/phy1/rfkill3) (driver ath9k_htc)
Oct 15 12:49:00 arcane-X555LB NetworkManager[883]: <info>  [1476550140.9331] device (wlan0): interface index 4 renamed iface from 'wlan0' to 'wlxf4f26d17b7ea'
Oct 15 12:49:00 arcane-X555LB NetworkManager[883]: <info>  [1476550140.9368] devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/wlxf4f26d17b7ea, iface: wlxf4f26d17b7ea)
Oct 15 12:49:00 arcane-X555LB NetworkManager[883]: <info>  [1476550140.9368] device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/wlxf4f26d17b7ea, iface: wlxf4f26d17b7ea): no ifupdown configuration found.
Oct 15 12:49:00 arcane-X555LB NetworkManager[883]: <info>  [1476550140.9369] device (wlxf4f26d17b7ea): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct 15 12:49:00 arcane-X555LB kernel: [12548.901740] IPv6: ADDRCONF(NETDEV_UP): wlxf4f26d17b7ea: link is not ready
Oct 15 12:49:01 arcane-X555LB kernel: [12549.087507] IPv6: ADDRCONF(NETDEV_UP): wlxf4f26d17b7ea: link is not ready
Oct 15 12:49:01 arcane-X555LB NetworkManager[883]: <info>  [1476550141.1537] device (wlxf4f26d17b7ea): supplicant interface state: starting -> ready
Oct 15 12:49:01 arcane-X555LB NetworkManager[883]: <info>  [1476550141.1538] device (wlxf4f26d17b7ea): state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Oct 15 12:49:01 arcane-X555LB kernel: [12549.118613] IPv6: ADDRCONF(NETDEV_UP): wlxf4f26d17b7ea: link is not ready
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.3396] device (wlxf4f26d17b7ea): supplicant interface state: ready -> inactive
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.3399] policy: auto-activating connection 'DDW365CB'
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.3410] device (wlxf4f26d17b7ea): Activation: starting connection 'DDW365CB' (9687368a-d5ca-4ce4-be6f-170c23c8d1ac)
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.3411] device (wlxf4f26d17b7ea): state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.3413] manager: NetworkManager state is now CONNECTING
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.3418] device (wlxf4f26d17b7ea): state change: prepare -> config (reason 'none') [40 50 0]
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.3423] device (wlxf4f26d17b7ea): Activation: (wifi) access point 'DDW365CB' has security, but secrets are required.
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.3424] device (wlxf4f26d17b7ea): state change: config -> need-auth (reason 'none') [50 60 0]
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.3466] device (wlxf4f26d17b7ea): state change: need-auth -> prepare (reason 'none') [60 40 0]
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.3474] device (wlxf4f26d17b7ea): state change: prepare -> config (reason 'none') [40 50 0]
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.3476] device (wlxf4f26d17b7ea): Activation: (wifi) connection 'DDW365CB' has security, and secrets exist.  No new secrets needed.
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.3476] Config: added 'ssid' value 'DDW365CB'
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.3476] Config: added 'scan_ssid' value '1'
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.3477] Config: added 'key_mgmt' value 'WPA-PSK'
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.3477] Config: added 'psk' value '<omitted>'
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.3521] sup-iface[0x12a7620,wlxf4f26d17b7ea]: config: set interface ap_scan to 1
Oct 15 12:49:02 arcane-X555LB kernel: [12550.323992] wlxf4f26d17b7ea: authenticate with 54:35:30:24:c5:ef
Oct 15 12:49:02 arcane-X555LB kernel: [12550.565195] wlxf4f26d17b7ea: send auth to 54:35:30:24:c5:ef (try 1/3)
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.6010] device (wlxf4f26d17b7ea): supplicant interface state: inactive -> authenticating
Oct 15 12:49:02 arcane-X555LB kernel: [12550.566901] wlxf4f26d17b7ea: authenticated
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.6079] device (wlxf4f26d17b7ea): supplicant interface state: authenticating -> associating
Oct 15 12:49:02 arcane-X555LB kernel: [12550.569521] wlxf4f26d17b7ea: associate with 54:35:30:24:c5:ef (try 1/3)
Oct 15 12:49:02 arcane-X555LB kernel: [12550.573335] wlxf4f26d17b7ea: RX AssocResp from 54:35:30:24:c5:ef (capab=0x411 status=0 aid=4)
Oct 15 12:49:02 arcane-X555LB kernel: [12550.581785] wlxf4f26d17b7ea: associated
Oct 15 12:49:02 arcane-X555LB kernel: [12550.581824] IPv6: ADDRCONF(NETDEV_CHANGE): wlxf4f26d17b7ea: link becomes ready
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.6231] device (wlxf4f26d17b7ea): supplicant interface state: associating -> 4-way handshake
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.6422] device (wlxf4f26d17b7ea): supplicant interface state: 4-way handshake -> completed
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.6423] device (wlxf4f26d17b7ea): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'DDW365CB'.
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.6424] device (wlxf4f26d17b7ea): state change: config -> ip-config (reason 'none') [50 70 0]
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.6428] dhcp4 (wlxf4f26d17b7ea): activation: beginning transaction (timeout in 45 seconds)
Oct 15 12:49:02 arcane-X555LB NetworkManager[883]: <info>  [1476550142.6441] dhcp4 (wlxf4f26d17b7ea): dhclient started with pid 9835
Oct 15 12:49:03 arcane-X555LB NetworkManager[883]: <info>  [1476550143.1219] audit: op="connection-activate" uuid="9687368a-d5ca-4ce4-be6f-170c23c8d1ac" name="DDW365CB" result="fail" reason="Device not found"
Oct 15 12:49:09 arcane-X555LB kernel: [12557.798156] wlxf4f26d17b7ea: deauthenticated from 54:35:30:24:c5:ef (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
Oct 15 12:49:09 arcane-X555LB NetworkManager[883]: <warn>  [1476550149.9800] sup-iface[0x12a7620,wlxf4f26d17b7ea]: connection disconnected (reason 15)
Oct 15 12:49:10 arcane-X555LB NetworkManager[883]: <info>  [1476550150.0039] device (wlxf4f26d17b7ea): supplicant interface state: completed -> disconnected

```

Device can't be found (but it was still powered on, as it was flashing green and I had networks listed).

It repeated once, and after that I was able to power it back on. 

If it happens again I will try and boot into the previous kernel to determine if there is a problem with the kernel and my adapter.

---

### Post by ajgreeny on 2016-10-15
What kernel are you using at the moment?

Use command **uname -a** to see; there seem to have been problems on some hardware with the 4.4.0-42 and maybe -43 kernels, so perhaps try booting to an earlier version if you have one and see if that fixes the problem for you, for now at least.

---

### Post by RobGoss on 2016-10-15
As **Ajgreeny **mentioned, Try holding down the **shift key** while your machine is booting this will also display the Grub menu, you should be able to choose a older kernel version, if you don't see a list of older kernel versions click on **advanced options** there should be a list for you to choose from. Hope this helps

---

### Post by mistcloud-misty on 2016-10-15
I'm using 4.4.0-43 right now. The earlier kernel worked fine for me.

---

### Post by howefield on 2016-10-15
> **mistcloud-misty said:**
> I'm using 4.4.0-43 right now. The earlier kernel worked fine for me.

The newest kernel is 4.4.0-44 so you probably want to update. As ajrenny mentioned -43 has been giving a few people some issues, particularly with wireless networking.

---

### Post by RobGoss on 2016-10-15
Yes** Howefield **I've seen a number of post with this same problem I'm sure they will release a fix for this in the next update or so

---

### Post by ajgreeny on 2016-10-16
Interestingly, I have not yet seen 4.4.0-44 in upgrades, nor have I had any problems personally with the 42 or 43 versions, but I am sure that is just hardware based; some works, some doesn't.

---

### Post by jeremy31 on 2016-10-16
This may not be a kernel issue, the package network-manager was changed recently.  Post results for ```
iwconfig
```

---

### Post by mistcloud-misty on 2016-10-16
Hello. I don't yet have any updates available by the update manager but right now the internet is working, even though Ubuntu is saying my networking is disabled and there are no networks available (I am able to browse the Internet, I believe the interface is simply crashed).

This is the results for iwconfig:

```
arcane@arcane-X555LB:~$ iwconfig
enp2s0    no wireless extensions.

lo        no wireless extensions.

wlxf4f26d17b7ea  IEEE 802.11bgn  ESSID:"DDW365CB"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 54:35:30:24:C5:EF   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0


```

---

### Post by RobGoss on 2016-10-16
It may sound silly just out of curiosity have you tried updating your wireless drivers?,** Software & updates** , **Additional drivers, **see what's available for your system

---

### Post by mistcloud-misty on 2016-10-16
None for my system. The USB adapter I use uses atheros communications (or ath9k).

---

### Post by mistcloud-misty on 2016-10-16
I had to reboot due to a suspend bug so I selected kernel -42 which I was using previously and everything is working perfectly so far. Had no issue connecting and the network manager in the taskbar is functioning as it should.

Hopefully the next kernel works fine with my hardware.

---

### Post by QLee on 2016-10-16
> **ajgreeny said:**
> Interestingly, I have not yet seen 4.4.0-44 in upgrades, nor have I had any problems personally with the 42 or 43 versions, but I am sure that is just hardware based; some works, some doesn't.

Same here.

I can't find it in the mirror I use either.

Since RobGoss agreed with Howefield, perhaps it is a case of that "staggered rollout" , or whatever they call it.

I also can't find it in an Ubuntu package search. Only the 4.4.0-43. [http://packages.ubuntu.com/xenial-updates/linux-image-generic](http://packages.ubuntu.com/xenial-updates/linux-image-generic)


@mistcloud-misty, glad you had success when you went back to the previous kernel, that was smart troubleshooting on your part.

---

### Post by ajgreeny on 2016-10-16
Wonderful news! 

Please mark as SOLVED from the Thread Tools menu up-top if this really is now solved to your satisfaction. It is a great help to users searching the forum.

---

