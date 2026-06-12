---
title: "Wireless on Dell Inspiron E1705 -- Can't Connect to Router"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by silver_arrow on 2006-11-11
Hi,

](*,) 

I would like to get some feedback from you in what concerns the wireless setup in Edgy.
Here's the situation I am facing:

I installed Ndiswrapper from Edgy's install disk.
I setup my wireless card and it's up and working.
If I use Wifi-Radar I can see all available networks.

Unfortunately it seems I can't connect to my wireless router because it constantly fails in setting the encryption.

I used DHCP and also fix IP address but I couldn't get connected to the router.
My authetication method in Windows is: Open and I am using WEP.

Here's the most important data on my setup:

[17180346.536000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17180346.540000] 
ndiswrapper: driver bcmwl5 () loaded
[17180346.540000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 177
[17180346.540000] 
PCI: Setting latency timer of device 0000:0c:00.0 to 64
[17180346.548000] ndiswrapper: using irq 177
[17180347.224000] 
wlan0: vendor: ''
[17180347.224000] 
wlan0: ethernet device 00:14:a4:d2:69:5b using NDIS driver bcmwl5, 14E4:4311.5.conf
[17180347.224000] 
wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17180347.228000] 
ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[17180347.252000] 
ndiswrapper (add_wep_key:815): adding encryption key 1 failed (C0010015)
[17180347.280000] 
ADDRCONF(NETDEV_UP): eth1: link is not ready
[17180641.128000] 
ndiswrapper (add_wep_key:815): adding encryption key 1 failed (C0010015)
[17180641.156000] 
ADDRCONF(NETDEV_UP): eth1: link is not ready
[17180818.044000] 
ndiswrapper (add_wep_key:815): adding encryption key 1 failed (C0010015)
[17180818.084000] 
ADDRCONF(NETDEV_UP): eth1: link is not ready
[17180952.844000] 
ndiswrapper (add_wep_key:815): adding encryption key 1 failed (C0010015)
[17180952.880000] 
ADDRCONF(NETDEV_UP): eth1: link is not ready
[17181132.204000] 
ndiswrapper (iw_set_wep:926): key 1 is not set
[17181132.204000] 
ndiswrapper (add_wep_key:815): adding encryption key 1 failed (C0010015)
[17181132.236000] 
ADDRCONF(NETDEV_UP): eth1: link is not ready


................


auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid XXXXXXX
wireless-enc open
wireless-key s:00000000000
wireless-channel 11
wireless-mode    managed

...........................

eth1      
2 key sizes : 40, 104bits
4 keys available :
[1]: off
[2]: off
[3]: off
[4]: off
Current Transmit Key: [1]
Security mode:restricted
Authentication capabilities :
WPA
WPA2
CIPHER TKIP
CIPHER CCMP
Current key_mgmt:0x0
Current cipher_pairwise:0x0
Current cipher_group:0x0

.............

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
Mode:Managed  
Frequency:2.462 GHz  Access Point: Not-Associated 
Bit Rate:54 Mb/s   Tx-Power:32 dBm
RTS thr:2347 B   Fragment thr:2346 B
Power Management:off
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by nadp on 2006-11-11
i always have that problem
wen i install a new copy of ubuntu, i cant access or connect to my wireless router, so i use my "neighbors wifi" and install wifi-radar, then connect to my router through there =S

---

