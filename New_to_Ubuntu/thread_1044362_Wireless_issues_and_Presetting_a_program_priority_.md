---
title: "Wireless issues and Presetting a program priority (ubuntu 8.10)"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Lunami on 2009-01-19
Well, I posted this elsewhere before, and still no luck. The thread was seemingly ignored altogether. At least I posted on the wireless issue.

I've noticed that I can connect to the router, but my connection continues to die off without warning. The icon on the top says I'm still connected, but nothing happens and I just lose the net altogether. I'd love to know a way to fix this, other than my current way of having to unplug my netgear wg111v2 (if that's even the correct version) USB adapter. This computer is mostly used for gaming and internet features, and the constant drop is very unhelpful.

Secondly, my last question is on program priority. A certain program on this computer requires me to start it in high priority, then after I'm in game having logged in and such, it goes back to a more normal one. On top of that, the game has a loading screen, and an auto patching screen it MUST go through for the game to work correctly. Is there a way I can perhaps change the priority as needed while the game is loaded? I'd be fine with it staying in high priority.

Any help is greatly appreciated. Thanks in advance. For the wireless issue, if you need me to input a command via terminal, such as lsusb and the like, tell me and I shall place up results.

Lunami

---

### Post by compiledkernel on 2009-01-19
on the wireless issue Lunami, if your connection is dying youll see something in /var/log/syslog and/or /var/log/messages at the time the connection drops. 

Get connected. 
tail -f /var/log/syslog (in a terminal window)
and wait for a drop. 

When the connection drops, im sure something will get tossed to syslog as to why.

---

### Post by Lunami on 2009-01-19
Anything I should keep an eye out for?

---

### Post by Lunami on 2009-01-19
This is everything from the time I lost connection to when I unplugged the usb, and plugged it back in, regaining my connection

```
Jan 19 12:46:20 desktop NetworkManager: <debug> [1232387180.011108] periodic_update(): Roamed from BSSID 00:22:15:1D:97:62 (moms) to (none) ((none)) 
Jan 19 12:46:26 desktop NetworkManager: <debug> [1232387186.015624] periodic_update(): Roamed from BSSID (none) ((none)) to 00:22:15:1D:97:62 (moms) 
Jan 19 12:47:57 desktop dhclient: receive_packet failed on wlan0: Network is down
Jan 19 12:47:58 desktop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Jan 19 12:47:58 desktop avahi-daemon[4258]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan 19 12:47:58 desktop avahi-daemon[4258]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.10.
Jan 19 12:47:58 desktop avahi-daemon[4258]: Withdrawing address record for fe80::21b:2fff:feaa:f321 on wlan0.
Jan 19 12:47:58 desktop avahi-daemon[4258]: Withdrawing address record for 192.168.0.10 on wlan0.
Jan 19 12:47:58 desktop kernel: [ 8711.928407] usb 2-1.4: USB disconnect, address 9
Jan 19 12:47:59 desktop NetworkManager: <info>  (wlan0): now unmanaged 
Jan 19 12:47:59 desktop NetworkManager: <info>  (wlan0): device state change: 8 -> 1 
Jan 19 12:47:59 desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 36). 
Jan 19 12:47:59 desktop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 7501 
Jan 19 12:48:00 desktop nm-system-settings:    SCPlugin-Ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_00_1b_2f_aa_f3_21_0)
Jan 19 12:48:01 desktop NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Jan 19 12:48:01 desktop NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Jan 19 12:48:01 desktop kernel: [ 8715.469728] usb 2-1.4: new full speed USB device using uhci_hcd and address 10
Jan 19 12:48:01 desktop kernel: [ 8715.604038] usb 2-1.4: configuration #1 chosen from 1 choice
Jan 19 12:48:01 desktop NetworkManager: <info>  (wlan0): cleaning up... 
Jan 19 12:48:02 desktop kernel: [ 8717.280480] phy5: Selected rate control algorithm 'pid'
Jan 19 12:48:03 desktop kernel: [ 8717.290740] phy5: hwaddr 00:1b:2f:aa:f3:21, RTL8187vB (default) V1 + rtl8225z2
Jan 19 12:48:04 desktop nm-system-settings:    SCPlugin-Ifupdown: devices added (udi: /org/freedesktop/Hal/devices/net_00_1b_2f_aa_f3_21_0, iface: wlan0)
Jan 19 12:48:04 desktop NetworkManager: <info>  wlan0: driver is 'rtl8187'. 
Jan 19 12:48:04 desktop NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Jan 19 12:48:04 desktop NetworkManager: <info>  Found new 802.11 WiFi device 'wlan0'. 
Jan 19 12:48:04 desktop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_1b_2f_aa_f3_21_0 
Jan 19 12:48:08 desktop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Jan 19 12:48:08 desktop NetworkManager: <info>  (wlan0): bringing up device. 
Jan 19 12:48:20 desktop kernel: [ 8735.238835] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 19 12:48:20 desktop NetworkManager: <info>  (wlan0): preparing device. 
Jan 19 12:48:20 desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Jan 19 12:48:20 desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Jan 19 12:48:21 desktop NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2. 
Jan 19 12:48:24 desktop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto moms' 
Jan 19 12:48:24 desktop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Jan 19 12:48:24 desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 19 12:48:24 desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jan 19 12:48:24 desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 19 12:48:24 desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jan 19 12:48:24 desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jan 19 12:48:24 desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Jan 19 12:48:24 desktop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto moms' has security, and secrets exist.  No new secrets needed. 
Jan 19 12:48:24 desktop NetworkManager: <info>  Config: added 'ssid' value 'moms' 
Jan 19 12:48:24 desktop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jan 19 12:48:24 desktop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Jan 19 12:48:24 desktop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Jan 19 12:48:24 desktop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Jan 19 12:48:24 desktop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Jan 19 12:48:24 desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jan 19 12:48:24 desktop NetworkManager: <info>  Config: set interface ap_scan to 1 
Jan 19 12:48:29 desktop NetworkManager: <info>  (wlan0): supplicant connection state change: 1 -> 2 
Jan 19 12:48:32 desktop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Jan 19 12:48:33 desktop kernel: [ 8747.520368] wlan0: authenticate with AP 00:22:15:1d:97:62
Jan 19 12:48:33 desktop kernel: [ 8747.523087] wlan0: authenticated
Jan 19 12:48:33 desktop kernel: [ 8747.523150] wlan0: associate with AP 00:22:15:1d:97:62
Jan 19 12:48:33 desktop kernel: [ 8747.526510] wlan0: RX AssocResp from 00:22:15:1d:97:62 (capab=0x411 status=0 aid=1)
Jan 19 12:48:33 desktop kernel: [ 8747.526546] wlan0: associated
Jan 19 12:48:33 desktop kernel: [ 8747.529181] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan 19 12:48:33 desktop NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Jan 19 12:48:33 desktop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Jan 19 12:48:33 desktop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'moms'. 
Jan 19 12:48:33 desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 19 12:48:33 desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Jan 19 12:48:33 desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Jan 19 12:48:33 desktop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Jan 19 12:48:33 desktop NetworkManager: <info>  dhclient started with pid 9738 
Jan 19 12:48:33 desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Jan 19 12:48:33 desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Jan 19 12:48:33 desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan 19 12:48:33 desktop dhclient: All rights reserved.
Jan 19 12:48:33 desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan 19 12:48:33 desktop dhclient: 
Jan 19 12:48:33 desktop dhclient: wmaster0: unknown hardware address type 801
Jan 19 12:48:33 desktop dhclient: wmaster0: unknown hardware address type 801
Jan 19 12:48:33 desktop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Jan 19 12:48:33 desktop dhclient: Listening on LPF/wlan0/00:1b:2f:aa:f3:21
Jan 19 12:48:33 desktop dhclient: Sending on   LPF/wlan0/00:1b:2f:aa:f3:21
Jan 19 12:48:33 desktop dhclient: Sending on   Socket/fallback
Jan 19 12:48:34 desktop avahi-daemon[4258]: Registering new address record for fe80::21b:2fff:feaa:f321 on wlan0.*.
Jan 19 12:48:36 desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jan 19 12:48:36 desktop dhclient: DHCPOFFER of 192.168.0.10 from 192.168.0.1
Jan 19 12:48:36 desktop dhclient: DHCPREQUEST of 192.168.0.10 on wlan0 to 255.255.255.255 port 67
Jan 19 12:48:37 desktop dhclient: DHCPACK of 192.168.0.10 from 192.168.0.1
Jan 19 12:48:37 desktop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Jan 19 12:48:37 desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Jan 19 12:48:37 desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Jan 19 12:48:37 desktop NetworkManager: <info>    address 192.168.0.10 
Jan 19 12:48:37 desktop NetworkManager: <info>    prefix 24 (255.255.255.0) 
Jan 19 12:48:37 desktop NetworkManager: <info>    gateway 192.168.0.1 
Jan 19 12:48:37 desktop NetworkManager: <info>    nameserver '24.197.160.17' 
Jan 19 12:48:37 desktop NetworkManager: <info>    nameserver '24.197.160.18' 
Jan 19 12:48:37 desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jan 19 12:48:37 desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Jan 19 12:48:37 desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Jan 19 12:48:37 desktop avahi-daemon[4258]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.10.
Jan 19 12:48:37 desktop avahi-daemon[4258]: New relevant interface wlan0.IPv4 for mDNS.
Jan 19 12:48:37 desktop avahi-daemon[4258]: Registering new address record for 192.168.0.10 on wlan0.IPv4.
Jan 19 12:48:37 desktop dhclient: bound to 192.168.0.10 -- renewal in 1686 seconds.
Jan 19 12:48:38 desktop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Jan 19 12:48:38 desktop NetworkManager: <info>  Policy set 'Auto moms' (wlan0) as default for routing and DNS. 
Jan 19 12:48:38 desktop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Jan 19 12:48:38 desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Jan 19 12:48:43 desktop kernel: [ 8758.086426] wlan0: no IPv6 routers present
Jan 19 12:48:44 desktop NetworkManager: <debug> [1232387324.867576] periodic_update(): Roamed from BSSID 00:22:15:1D:97:62 (moms) to (none) ((none)) 
Jan 19 12:48:45 desktop ntpdate[9799]: no server suitable for synchronization found
Jan 19 12:48:50 desktop NetworkManager: <debug> [1232387330.872170] periodic_update(): Roamed from BSSID (none) ((none)) to 00:22:15:1D:97:62 (moms) 
Jan 19 12:48:59 desktop dhclient: DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 7
```

---

### Post by compiledkernel on 2009-01-19
Looks like your losing connection with the AP/Router. 

How far away are you from it? 

What level of encrypt are you using? 

Jan 19 12:46:20 desktop NetworkManager: <debug> [1232387180.011108] periodic_update(): Roamed from BSSID 00:22:15:1D:97:62 (moms) to (none) ((none)) 
Jan 19 12:46:26 desktop NetworkManager: <debug> [1232387186.015624] periodic_update(): Roamed from BSSID (none) ((none)) to 00:22:15:1D:97:62 (moms) 
Jan 19 12:47:57 desktop dhclient: receive_packet failed on wlan0: Network is down

---

### Post by Lunami on 2009-01-19
The router is litereally in view. It's like... no more than 10 feet?
As for the encryption.I'm using a WEP 128

---

### Post by compiledkernel on 2009-01-19
Hmmmm, well it would certainly seem to be a connectivity issue. Can you try another form of encrypt? 

For the sake, even try it totally open to see if its how the router transmits its encryption data.

---

### Post by Lunami on 2009-01-19
You mean without an encryption key?
If that's so. I've tried. I can't seem to get it to work.

---

### Post by niteshifter on 2009-01-19
Hi,

Let's collect a bit more data on the connection before we begin messing (or petitioning to mess with ;) ) the family router:

Lunami, while you do have a connection enter this in a terminal and post the output:
```
iwconfig wlan0
```

Reason: Let's see what his signal levels and noise levels are.

---

### Post by compiledkernel on 2009-01-19
Hmmmm...do you have the same problems connecting to OTHER wireless networks?

---

### Post by Lunami on 2009-01-19
iwconfig
```
[B]wlan0     IEEE 802.11bg  ESSID:"moms"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:15:1D:97:62   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=14/100  Signal level:65/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/B]
```

As for other connections, I do not have access to any others but this one.

---

### Post by Lunami on 2009-01-19
Anything else?

---

### Post by niteshifter on 2009-01-19
Hi,

You've got a marginal signal there. As the adapter itself (it's a USB plugin device) can't have it's RF connections reseated you can check the router's:

If it sports external antennas with connectors, disconnect and reconnect them a couple times. Run that iwconfig wlan0 command again. What we're looking for is to get that quality higher than 14/100.

If possible try placing the laptop and router within a few feet of each other and run the command again. The quality number should improve. If it doesn't I'd say you've a flaky adapter.

You can try moving the router around some. RF at these frequencies can be downright weird at times. Like if the router is near a wall (within inches) move it a way (a foot or so) - power wiring in the wall can attenuate.

What I was hoping (against hope as it's a USB adapter type) is that iwconfig would give meaningful measurements as to receive and noise levels in dBm (like many mini-PCI cards do). Alas, it doesn't and that receive parameter of 65/65 is nonsensical without some experimentation.

Lastly, a comment on such devices (USB and PCMIA WiFi adapters): It's a physics problem - to get an efficient radiator / collector of RF energy requires antenna elements to be of the correct size and spatial relationship. The size and spatial relationship is dependent upon wavelength (frequency). The thing is such adapters don't have the space internally to do both in so their performance is lacking as a RF receiver / transmitter. One is better off using an internal card if the laptop is outfitted for it.

---

### Post by Lunami on 2009-01-19
For one, I'm using a PC with an external usb Netgear adapter. No laptop unfortunately.

Secondly, I'm not too good with the tech jargon. I got very little clue what you mentioned at all in this post.

---

### Post by niteshifter on 2009-01-20
Hi,

Sorry about the jargon ... let's try this: Your adapter is reporting the quality of the signal - a score, if you will - of 14 out of 100. Not good. Rather like a FM radio or a portable TV with an antenna trying to pick up a distant station - it's fading out and some noise creeps in, messing with the signal you want. 

Your problem is showing up as a "network problem" but the underlying cause is poor radio reception. Again, like a portable radio or TV moving things around can help, as can cleaning (by removing and re-inserting) any antenna connections the router may have. You could try an USB extender cable with the adapter to make moving it around easier.

---

### Post by Lunami on 2009-01-20
I've tried moving the router as close as possible, which as said is literally within viewing range. I can't get it to go past 16/100. I've also noticed that when I boot up my system, it gives me a var/lib/dhcp3/dhclient.lo.leases error. I was wondering if there was a way to fix it. 
Also, on the original post, I was curious about the priority settings. Any help there would be appreciated.

---

### Post by Lunami on 2009-01-21
I thought I'd give another comment here. This computer is dual boot. Win XP and Ubuntu 8.10. XP is on the master drive, while Ubuntu is on the slave. When I go to the windows side, I noticed that the internet doesn't flitter around like on here. Could that have anything to do with this?

As for the priority, I figured I'll just do renice.

---

