---
title: "Unable to Set Monitor Mode RTL8192CU"
date: 2015-04-10
forum: Networking &amp; Wireless
---

### Post by xExekut3x on 2015-04-10
It's a TP-LINK TL-WN821N v4.2.

```
ifconfig

wlan0     Link encap:Ethernet  HWaddr 14:cc:20:1c:b4:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
```
sudo lshw -C network

*-network
       description: Wireless interface
       physical id: 1
       bus info: usb@3:4
       logical name: wlan0
       serial: 14:cc:20:1c:b4:56
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu multicast=yes wireless=unassociated

```
```
lsusb

Bus 003 Device 003: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter

```

```
iwconfig wlan0

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

For whatever reason, iw is no longer recognizing the device, but it recognizes my other D-LINK wireless adapter fine. Running iw phy1 info does nothing.

```
iw wlan0 info

command failed: No such device (-19)

```

When trying to set monitor mode, I get this.

```
sudo iwconfig wlan0 mode monitor

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

```
Why doesn't iw recognize my device? And why can't I set it to monitor mode? It allows it, because when iw was working, it showed monitor as available. I remember a long time ago while using Kismet, I had to create another interface, something like mon0, to be able to set it to monitor mode. Anyone have a link to a guide for how to do that?

---

### Post by xExekut3x on 2015-04-10
Here's some proof that iw recognizes my other adapter. Don't understand why it's not recognizing the other. I'm betting it has something to do with trying to airmon-ng to set it to monitor mode.

```
ifconfig

wlan0     Link encap:Ethernet  HWaddr 14:cc:20:1c:b4:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:15 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan1     Link encap:Ethernet  HWaddr ec:22:80:72:6d:80  
          inet addr:192.168.1.238  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ee22:80ff:fe72:6d80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11756 errors:0 dropped:6 overruns:0 frame:0
          TX packets:7684 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14182166 (14.1 MB)  TX bytes:1167132 (1.1 MB)

```

```
lsusb

Bus 003 Device 005: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 003 Device 004: ID 2001:3314 D-Link Corp. 

```

```
sudo lshw -C network

*-network:0
       description: Wireless interface
       physical id: 1
       bus info: usb@3:4
       logical name: wlan0
       serial: 14:cc:20:1c:b4:56
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu multicast=yes wireless=unassociated
  *-network:1
       description: Wireless interface
       physical id: 2
       bus info: usb@3:3
       logical name: wlan1
       serial: ec:22:80:72:6d:80
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8812au driverversion=3.16.0-34-generic firmware=N/A ip=192.168.1.238 link=yes multicast=yes wireless=IEEE 802.11an

```




```
iwconfig

eth0      no wireless extensions.


wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.


wlan1     IEEE 802.11an  ESSID:"daynet_5g"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:5.805 GHz  Access Point: D8:50:E6:92:EB:BC   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

```
iw list

Wiphy phy0
    max # scan SSIDs: 9
    max scan IEs length: 2304 bytes
    Coverage class: 0 (up to 0m)
    Supported Ciphers:
        * WEP40 (00-0f-ac:1)
        * WEP104 (00-0f-ac:5)
        * TKIP (00-0f-ac:2)
        * CCMP (00-0f-ac:4)
    Available Antennas: TX 0 RX 0
    Supported interface modes:
         * IBSS
         * managed
         * AP
         * monitor
         * P2P-client
         * P2P-GO
    Band 1:
        Capabilities: 0x1862
            HT20/HT40
            Static SM Power Save
            RX HT20 SGI
            RX HT40 SGI
            No RX STBC
            Max AMSDU length: 7935 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 16 usec (0x07)
        HT TX/RX MCS rate indexes supported: 0-7, 32
        Bitrates (non-HT):
            * 1.0 Mbps
            * 2.0 Mbps
            * 5.5 Mbps
            * 11.0 Mbps
            * 6.0 Mbps
            * 9.0 Mbps
            * 12.0 Mbps
            * 18.0 Mbps
            * 24.0 Mbps
            * 36.0 Mbps
            * 48.0 Mbps
            * 54.0 Mbps
        Frequencies:
            * 2412 MHz [1] (20.0 dBm)
            * 2417 MHz [2] (20.0 dBm)
            * 2422 MHz [3] (20.0 dBm)
            * 2427 MHz [4] (20.0 dBm)
            * 2432 MHz [5] (20.0 dBm)
            * 2437 MHz [6] (20.0 dBm)
            * 2442 MHz [7] (20.0 dBm)
            * 2447 MHz [8] (20.0 dBm)
            * 2452 MHz [9] (20.0 dBm)
            * 2457 MHz [10] (20.0 dBm)
            * 2462 MHz [11] (20.0 dBm)
            * 2467 MHz [12] (20.0 dBm) (no IR)
            * 2472 MHz [13] (20.0 dBm) (no IR)
            * 2484 MHz [14] (20.0 dBm) (no IR)
    Band 2:
        Capabilities: 0x1862
            HT20/HT40
            Static SM Power Save
            RX HT20 SGI
            RX HT40 SGI
            No RX STBC
            Max AMSDU length: 7935 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 16 usec (0x07)
        HT TX/RX MCS rate indexes supported: 0-7, 32
        Bitrates (non-HT):
            * 6.0 Mbps
            * 9.0 Mbps
            * 12.0 Mbps
            * 18.0 Mbps
            * 24.0 Mbps
            * 36.0 Mbps
            * 48.0 Mbps
            * 54.0 Mbps
        Frequencies:
            * 5170 MHz [34] (disabled)
            * 5180 MHz [36] (20.0 dBm)
            * 5190 MHz [38] (20.0 dBm) (no IR)
            * 5200 MHz [40] (20.0 dBm) (no IR)
            * 5210 MHz [42] (20.0 dBm) (no IR)
            * 5220 MHz [44] (20.0 dBm) (no IR)
            * 5230 MHz [46] (20.0 dBm) (no IR)
            * 5240 MHz [48] (20.0 dBm) (no IR)
            * 5260 MHz [52] (disabled)
            * 5280 MHz [56] (disabled)
            * 5300 MHz [60] (disabled)
            * 5320 MHz [64] (disabled)
            * 5500 MHz [100] (disabled)
            * 5520 MHz [104] (disabled)
            * 5540 MHz [108] (disabled)
            * 5560 MHz [112] (disabled)
            * 5580 MHz [116] (disabled)
            * 5600 MHz [120] (disabled)
            * 5620 MHz [124] (disabled)
            * 5640 MHz [128] (disabled)
            * 5660 MHz [132] (disabled)
            * 5680 MHz [136] (disabled)
            * 5700 MHz [140] (disabled)
            * 5745 MHz [149] (20.0 dBm) (no IR)
            * 5765 MHz [153] (20.0 dBm) (no IR)
            * 5785 MHz [157] (20.0 dBm) (no IR)
            * 5805 MHz [161] (20.0 dBm)
            * 5825 MHz [165] (20.0 dBm) (no IR)
            * 5920 MHz [184] (disabled)
            * 5940 MHz [188] (disabled)
            * 5960 MHz [192] (disabled)
            * 5980 MHz [196] (disabled)
            * 6000 MHz [200] (disabled)
            * 6020 MHz [204] (disabled)
            * 6040 MHz [208] (disabled)
            * 6060 MHz [212] (disabled)
            * 6080 MHz [216] (disabled)
    Supported commands:
         * new_interface
         * set_interface
         * new_key
         * start_ap
         * new_station
         * set_bss
         * join_ibss
         * set_pmksa
         * del_pmksa
         * flush_pmksa
         * remain_on_channel
         * frame
         * set_channel
         * connect
         * disconnect
    Supported TX frame types:
         * IBSS: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * managed: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * AP: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * AP/VLAN: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * P2P-client: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * P2P-GO: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
    Supported RX frame types:
         * IBSS: 0xd0
         * managed: 0x40 0xd0
         * AP: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
         * AP/VLAN: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
         * P2P-client: 0x40 0xd0
         * P2P-GO: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
    software interface modes (can always be added):
         * monitor
    interface combinations are not supported
    Device supports scan flush.

```

---

### Post by wildmanne39 on 2015-04-10
Hi, we do not support airmon-ng or any from of hacking or cracking on the forum, we know that you may have well intentions but some one else can use this thread to get their device working in monitor mode and do illegal things with it so that is the reason it is not allowed. You can try aircracks or Kali's forum.
> Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.
Thread closed!

---

