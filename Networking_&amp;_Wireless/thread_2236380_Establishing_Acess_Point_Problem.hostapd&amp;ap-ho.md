---
title: "Establishing Acess Point Problem.hostapd&amp;ap-hotspot&amp;dnsmasq didn't work today"
date: 2014-07-26
forum: Networking &amp; Wireless
---

### Post by Yaufook_Chan on 2014-07-26
Putting this question on this/other forum is the last approach I can think of to solve the problem. The problem has annoyed me for a whole day.:mad:I can hear my heart broken....

Now, introduce my problem.
1. I set up the ap-hotspot about 7 days ago, and it had been working awesomely for a week, untill yesterday. (ap-hotspot+hostapd+dnsmasq) My eth0 is connecting to the internet and wlan0 is for LAN. I shared the internet from my laptop to my cell phone.
2. The hostapd version I used for ap-hotspot is the version for Ubuntu saucy-updates(Ubuntu 13.10?), "hostapd (1:1.0-3ubuntu2.1) universe"
3. My laptop has been held on for 7 days and the network worked very well. But in the last day I kept a huge amount of pages opened in my browser and it was lagging so I reboot my laptop.
4. Then things went bad.
5. The symptoms are:
  (1) It's my first time to reboot after I finished the WAP setting. I found that ap-hotspot didn't start with the PC boot.(maybe it's normal. I don't know)
  (2) When I commanded: sudo ap-hotspot debug
```
Starting Wireless Hotspot...
* Stopping DNS forwarder and DHCP server dnsmasq
* (not running)
update-rc.d: warning:  start runlevel arguments (none) do not match hostapd Default-Start values (2 3 4 5)
update-rc.d: warning:  stop runlevel arguments (none) do not match hostapd Default-Stop values (0 1 6)
Disabling system startup links for /etc/init.d/hostapd ...
Removing any system startup links for /etc/init.d/hostapd ...
/etc/rc0.d/K20hostapd
/etc/rc1.d/K20hostapd
/etc/rc2.d/K80hostapd
/etc/rc3.d/K80hostapd
/etc/rc4.d/K80hostapd
/etc/rc5.d/K80hostapd
/etc/rc6.d/K20hostapd
Adding system startup for /etc/init.d/hostapd ...
/etc/rc0.d/K20hostapd -> ../init.d/hostapd
/etc/rc1.d/K20hostapd -> ../init.d/hostapd
/etc/rc6.d/K20hostapd -> ../init.d/hostapd
/etc/rc2.d/K80hostapd -> ../init.d/hostapd
/etc/rc3.d/K80hostapd -> ../init.d/hostapd
/etc/rc4.d/K80hostapd -> ../init.d/hostapd
/etc/rc5.d/K80hostapd -> ../init.d/hostapd
update-rc.d: warning:  start runlevel arguments (none) do not match dnsmasq Default-Start values (2 3 4 5)
update-rc.d: warning:  stop runlevel arguments (none) do not match dnsmasq Default-Stop values (0 1 6)
Disabling system startup links for /etc/init.d/dnsmasq ...
Removing any system startup links for /etc/init.d/dnsmasq ...
/etc/rc0.d/K85dnsmasq
/etc/rc1.d/K85dnsmasq
/etc/rc2.d/K85dnsmasq
/etc/rc3.d/K85dnsmasq
/etc/rc4.d/K85dnsmasq
/etc/rc5.d/K85dnsmasq
/etc/rc6.d/K85dnsmasq
Adding system startup for /etc/init.d/dnsmasq ...
/etc/rc0.d/K85dnsmasq -> ../init.d/dnsmasq
/etc/rc1.d/K85dnsmasq -> ../init.d/dnsmasq
/etc/rc6.d/K85dnsmasq -> ../init.d/dnsmasq
/etc/rc2.d/K85dnsmasq -> ../init.d/dnsmasq
/etc/rc3.d/K85dnsmasq -> ../init.d/dnsmasq
/etc/rc4.d/K85dnsmasq -> ../init.d/dnsmasq
/etc/rc5.d/K85dnsmasq -> ../init.d/dnsmasq
* Restarting DNS forwarder and DHCP server dnsmasq
...done.
net.ipv4.ip_forward = 1
Wireless Hotspot active

```
  (3) Everythings seem OK but when my mobile connected to the WAP, the status can change to "Connecting..." only, and then "Saved, secured with WPA/WPA2":(:(](*,)
(4) cat /etc/ap-hotspot.conf
```

# WiFi Hotspot
interface=wlan0
driver=nl80211
#Access Point
ssid=myhotspot
hw_mode=g
# WiFi Channel:
channel=1
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=qwerty0987
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP

```

My Clues&Test Details:
1. I remember there was an update for my Ubuntu.(not sure?)
2. My wireless card is OK. Because I tested Connectify on Win7, which worked.
3. I've tried other versions of hostapd
4. I ran hostapd alone/with ap-hotspot with -d argument.
```
random: Trying to read entropy from /dev/random
Configuration file: /etc/hostapd/hostapd.conf
nl80211: interface wlan0 in phy phy0
rfkill: initial event: idx=0 type=1 op=0 soft=0 hard=0
nl80211: Using driver-based off-channel TX
nl80211: Register frame command failed (type=208): ret=-114 (Operation already in progress)
nl80211: Register frame match - hexdump(len=2): 04 0a
nl80211: Failed to register Action frame processing - ignore for now
nl80211: Add own interface ifindex 3
nl80211: Set mode ifindex 3 iftype 3 (AP)
nl80211: Create interface iftype 6 (MONITOR)
nl80211: New interface mon.wlan0 created: ifindex=5
nl80211: Add own interface ifindex 5
BSS count 1, BSSID mask 00:00:00:00:00:00 (0 bits)
nl80211: Regulatory information - country=00
nl80211: 2402-2472 @ 40 MHz
nl80211: 2457-2482 @ 40 MHz
nl80211: 2474-2494 @ 20 MHz
nl80211: 5170-5250 @ 40 MHz
nl80211: 5735-5835 @ 40 MHz
nl80211: Added 802.11b mode based on 802.11g information
Completing interface initialization
Mode: IEEE 802.11g  Channel: 1  Frequency: 2412 MHz
nl80211: Set freq 2412 (ht_enabled=0 sec_channel_offset=0)
Failed to update rate sets in kernel module
RATE[0] rate=10 flags=0x1
RATE[1] rate=20 flags=0x1
RATE[2] rate=55 flags=0x1
RATE[3] rate=110 flags=0x1
RATE[4] rate=60 flags=0x0
RATE[5] rate=90 flags=0x0
RATE[6] rate=120 flags=0x0
RATE[7] rate=180 flags=0x0
RATE[8] rate=240 flags=0x0
RATE[9] rate=360 flags=0x0
RATE[10] rate=480 flags=0x0
RATE[11] rate=540 flags=0x0
Flushing old station entries
Deauthenticate all stations
wpa_driver_nl80211_set_key: ifindex=3 alg=0 addr=(nil) key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=3 alg=0 addr=(nil) key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=3 alg=0 addr=(nil) key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=3 alg=0 addr=(nil) key_idx=3 set_tx=0 seq_len=0 key_len=0
Using interface wlan0 with hwaddr 70:f1:a1:a7:a4:ba and ssid 'myhotspot'
Deriving WPA PSK based on passphrase
SSID - hexdump_ascii(len=9):
     6d 79 68 6f 74 73 70 6f 74                        myhotspot       
PSK (ASCII passphrase) - hexdump_ascii(len=10): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
random: Got 20/20 bytes from /dev/random
GMK - hexdump(len=32): [REMOVED]
Key Counter - hexdump(len=32): [REMOVED]
WPA: Delay group state machine start until Beacon frames have been configured
VLAN: vlan_set_name_type(name_type=2)
nl80211: Set beacon (beacon_set=0)
WPA: Start group state machine to set initial keys
WPA: group state machine entering state GTK_INIT (VLAN-ID 0)
GTK - hexdump(len=32): [REMOVED]
WPA: group state machine entering state SETKEYSDONE (VLAN-ID 0)
wpa_driver_nl80211_set_key: ifindex=3 alg=2 addr=0x48df92 key_idx=1 set_tx=1 seq_len=0 key_len=32
   broadcast key
wpa_driver_nl80211_set_operstate: operstate 0->1 (UP)
netlink: Operstate: linkmode=-1, operstate=6
wlan0: Setup of interface done.
RTM_NEWLINK: operstate=1 ifi_flags=0x1002 ()
nl80211: Ignore interface down event since interface wlan0 is up
RTM_NEWLINK: operstate=1 ifi_flags=0x1002 ()
nl80211: Ignore interface down event since interface mon.wlan0 is up
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'mon.wlan0' added
Unknown event 5
RTM_NEWLINK: operstate=1 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
nl80211: if_removed already cleared - ignore event
RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP])
netlink: Operstate: linkmode=-1, operstate=6
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
nl80211: if_removed already cleared - ignore event
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
nl80211: if_removed already cleared - ignore event
nl80211: Event message available
nl80211: Scan trigger
VLAN: vlan_newlink(wlan0)
VLAN: vlan_newlink(wlan0)
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
nl80211: if_removed already cleared - ignore event
nl80211: Event message available
nl80211: New scan results available
VLAN: vlan_newlink(wlan0)

```
 When my mobile tried to connected to the wireless access point, the terminal display:
```

mgmt::auth
authentication: STA=f8:a9:d0:xx:yy:zz auth_alg=0 auth_transaction=1 status_code=0 wep=0
  New STA
wlan0: STA f8:a9:d0:xx:yy:zz IEEE 802.11: authentication OK (open system)
wlan0: STA f8:a9:d0:xx:yy:zz MLME: MLME-AUTHENTICATE.indication(f8:a9:d0:xx:yy:zz, OPEN_SYSTEM)
wlan0: STA f8:a9:d0:xx:yy:zz MLME: MLME-DELETEKEYS.request(f8:a9:d0:xx:yy:zz)
authentication reply: STA=f8:a9:d0:xx:yy:zz auth_alg=0 auth_transaction=2 resp=0 (IE len=0)
mgmt::auth
authentication: STA=f8:a9:d0:xx:yy:zz auth_alg=0 auth_transaction=1 status_code=0 wep=0
wlan0: STA f8:a9:d0:xx:yy:zz IEEE 802.11: authentication OK (open system)
wlan0: STA f8:a9:d0:xx:yy:zz MLME: MLME-AUTHENTICATE.indication(f8:a9:d0:xx:yy:zz, OPEN_SYSTEM)
wlan0: STA f8:a9:d0:xx:yy:zz MLME: MLME-DELETEKEYS.request(f8:a9:d0:xx:yy:zz)
authentication reply: STA=f8:a9:d0:xx:yy:zz auth_alg=0 auth_transaction=2 resp=0 (IE len=0)
mgmt::auth
authentication: STA=f8:a9:d0:xx:yy:zz auth_alg=0 auth_transaction=1 status_code=0 wep=0
wlan0: STA f8:a9:d0:xx:yy:zz IEEE 802.11: authentication OK (open system)
wlan0: STA f8:a9:d0:xx:yy:zz MLME: MLME-AUTHENTICATE.indication(f8:a9:d0:xx:yy:zz, OPEN_SYSTEM)
wlan0: STA f8:a9:d0:xx:yy:zz MLME: MLME-DELETEKEYS.request(f8:a9:d0:xx:yy:zz)
authentication reply: STA=f8:a9:d0:xx:yy:zz auth_alg=0 auth_transaction=2 resp=0 (IE len=0)

```
5. I configured the hostapd, modified /etc/network/interfaces and used dhcpd to set up a WAP mannually, things went the same.
6. ifconfig information after my starting ap-hotspot
```

eth0      Link encap:Ethernet  HWaddr c8:0a:a9:xx:yy:zz  
          inet addr:172.20.xxx.yyy  Bcast:172.20.xxx.255  Mask:255.255.252.0
          inet6 addr: fe80::ca0a:a9ff:xxxx:yyyy/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:571261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20204 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:55607543 (55.6 MB)  TX bytes:3574074 (3.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:662078 (662.0 KB)  TX bytes:662078 (662.0 KB)

mon.wlan0 Link encap:UNSPEC  HWaddr 70-F1-A1-A7-XX-YY-ZZ-QQ-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3690 (3.6 KB)  TX bytes:0 (0.0 B)

virbr0    Link encap:Ethernet  HWaddr 82:75:1e:70:76:2b  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:a7:a4:ba  
          inet addr:192.168.150.1  Bcast:192.168.150.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:XXXX:YYYY/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:28873 (28.8 KB)

```
7. When my mobile tried to connect to the WAP, the value "RX bytes" of "mon.wlan0" increased

Any Information?
Tell me to collect other information if you want to help. I will appreciate all your efforts!:KS:KS

I am dying T_T
Post your situation if you faced the same problem! Help if you know anything about it!

Thanks a lot!

---

### Post by Yaufook_Chan on 2014-07-27
Is that really no body help?..

I reinstall my Xubuntu today but the problem still exists:(

I can run the router function with connectify in WIN7. But it's incovenience to do so.

Is that a bug in 14.04?

---

### Post by Bucky Ball on 2014-07-27
Welcome. Please be patient. We are an international forum and sometimes it takes time for the right person to arrive to help you. Good luck. ;)

---

### Post by Yaufook_Chan on 2014-07-27
Thanks for your support~

As I know, Ubuntu 14.04 support the function to create WIFI hotspot with NetworkManager by modifying /etc/NetworkManager/system-connections/yourwifi.conf and set the mode as AP. I've tried this way but my Nexus5 failed to scan the hotspot.

I think this problem is rather bigger than I thought. Maybe it's the version pain we should suffer~ I should try to maintain a stable version of Linux for me:P.

---

### Post by Bucky Ball on 2014-07-27
Well, I've tethered a minimal install on a netbook to a phone as access point, but never the other way around, sorry. That was a bit more straightforward than your issues by the sounds of it, though. :-k

---

### Post by Yaufook_Chan on 2014-07-27
I think I should post my wireless-info.txt for this.

Maybe my driver,my hardware can affect this.

Anyway, i'm GMT+8, gotta sleep[-o

---

