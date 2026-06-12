---
title: "Problems WPA static IP on Kubuntu 6.10"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by kracheck on 2006-11-14
Hi there,

as a kubuntu 6.10 Edgy Eft newbie I was wondering if someone could help me out in making my static wireless network with WPA-PSK enabled function properly.
The set-up is as follows :

*Router : Linksys WRT54G configured with static ip adresses, no DHCP
*Wireless settings : 
-SSID:Jupiter
-Wireless security WPA Personal TKIP algorithms with a WPA Shared key.
-Wireless Mac Filter enabled, only pc's listed can access the wireless network.  In this case the wireless
card has 00:13:02:96:d8:e3 as mac adress and is in the list of wireless clients on the router.
-PCI-KInfoCenter gives the following information about the wireless card :
Network controller : Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
-Wpa_supplicant version :
foo@bar:~$ dpkg -l|grep "wpa"
ii  wpagui                                     0.5.4-5                       GUI for wpa_supplicant
ii  wpasupplicant                              0.5.4-5                       Client support for WPA and WPA2 (IEEE 802.11
-Installed driver
foo@bar:~$ lsmod|grep ipw3945
ipw3945               124576  1
ieee80211              35272  1 ipw3945


Looking at the output below i'd say the card detects the AP correctly.  For this I had to use the wext driver instead of the ipw.  I can't however browse the internet since i'm unable to ping my router (see below, 192.168.0.1).  The card works correctly under windows.

Judging from the information below, does anyone have a clue what could be the issue here ?
Any help is welcome.

Thanks in advance


1. etc/wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=2
fast_reauth=1

network={
        ssid="jupiter"
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        psk=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
}

2. etc/network/interfaces

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.0.7
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
iface eth1 inet static
address 192.168.0.6
netmask 255.255.255.0
wireless-essid jupiter
gateway 192.168.0.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

3. starting wpa_supplicant

foo@bar:~$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D wext -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=2
fast_reauth=1
Line: 8 - start of a new network block
ssid - hexdump_ascii(len=7):
     6a 75 70 69 74 65 72                              jupiter
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
group: 0x8
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='jupiter'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=20 WE(source)=16 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:13:02:96:d8:e3
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth1
Daemonize..

4. iwconfig

foo@bar:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"jupiter"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:17:D7:AD:C3
          Bit Rate:54 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=-30 dBm  Noise level=-31 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:110   Missed beacon:0

sit0      no wireless extensions.

5. ifconfig

foo@bar:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D4:34:F3:E9
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:13:02:96:D8:E3
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe96:d8e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2644 errors:35 dropped:145 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:142632 (139.2 KiB)  TX bytes:5063 (4.9 KiB)
          Interrupt:185 Base address:0xa000 Memory:52000000-52000fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4143 (4.0 KiB)  TX bytes:4143 (4.0 KiB)

6. Pinging

foo@bar:~$ ping 192.168.0.6
PING 192.168.0.6 (192.168.0.6) 56(84) bytes of data.
64 bytes from 192.168.0.6: icmp_seq=1 ttl=64 time=0.041 ms
64 bytes from 192.168.0.6: icmp_seq=2 ttl=64 time=0.037 ms
64 bytes from 192.168.0.6: icmp_seq=3 ttl=64 time=0.039 ms
64 bytes from 192.168.0.6: icmp_seq=4 ttl=64 time=0.038 ms

--- 192.168.0.6 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.037/0.038/0.041/0.007 ms

foo@bar:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.7 icmp_seq=1 Destination Host Unreachable
From 192.168.0.7 icmp_seq=2 Destination Host Unreachable
From 192.168.0.7 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5018ms
, pipe 3
foo@bar:~$

---

### Post by bjd on 2006-11-14
This looks like a routing mixup..
Since eth0 and eth1 are on the same subnet, linux picks the first matching interface to send packets to 192.168.0.x and in this case it's eth0.
You can also see this in the ping responses, eth0 reports it can't reach the address. 
Try taking down eth0:  *sudo ifdown eth0*
Also do a *route* and check if the default route to 192.168.0.1 goes through eth1.

---

### Post by kracheck on 2006-11-14
Thank you very much !!!!
Bringing down eth0 solved the problem.  What can I do to avoid this in the future ?

---

