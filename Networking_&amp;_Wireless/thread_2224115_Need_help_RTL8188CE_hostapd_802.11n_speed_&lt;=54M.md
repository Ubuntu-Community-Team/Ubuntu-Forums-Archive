---
title: "Need help RTL8188CE hostapd 802.11n speed &lt;=54Mbps"
date: 2014-05-14
forum: Networking &amp; Wireless
---

### Post by david144 on 2014-05-14
Hi I'm trying to configure hostapd and I think I'm in over my head now that I'm down to the ht_capab section.


I have a clean 12.04.04 LTS with only a few packages installed (hostapd, vlan, bridge-utils, vim, udhcpd)


I'm running two vlans and bridging them to separate wifi adapters so I can have an SSID for my inside network (VLAN 192) and one for my DMZ (VLAN 10) for guests that I don't have to worry about adding MAC addresses and giving them my WPA2-PSK


My wireless cards are:
VLAN10: Cisco by Linksys USB WUSB54GC (wlan1<->br10<->eth0.10)
    Bus 001 Device 002: ID 1737:0077 Linksys WUSB54GC v3 802.11g Adapter [Ralink RT2070L]


VLAN192: NETIS WF2113 PCIe (wlan0<->br192<->eth0.192) {It shows up as 8188CE, but has 8192CE printed on the chip)
    01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)


I went with the default drivers so I'm suspecting I might need to build new drivers, but was hoping I could get a better understanding of the ht_capab options first.


Here's the output of my "iw list"
wlan0
```

Wiphy phy0
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
        HT TX/RX MCS rate indexes supported: 0-15, 32
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
            * 2467 MHz [12] (20.0 dBm)
            * 2472 MHz [13] (20.0 dBm)
            * 2484 MHz [14] (disabled)
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
    max # scan SSIDs: 4
    max scan IEs length: 2257 bytes
    RTS threshold: 2347
    Coverage class: 0 (up to 0m)
    Supported Ciphers:
        * WEP40 (00-0f-ac:1)
        * WEP104 (00-0f-ac:5)
        * TKIP (00-0f-ac:2)
        * CCMP (00-0f-ac:4)
        * CMAC (00-0f-ac:6)
    Available Antennas: TX 0 RX 0
    Supported interface modes:
         * IBSS
         * managed
         * AP
         * AP/VLAN
         * monitor
         * mesh point
         * P2P-client
         * P2P-GO
    software interface modes (can always be added):
         * AP/VLAN
         * monitor
    interface combinations are not supported
    Supported commands:
         * new_interface
         * set_interface
         * new_key
         * new_beacon
         * new_station
         * new_mpath
         * set_mesh_params
         * set_bss
         * authenticate
         * associate
         * deauthenticate
         * disassociate
         * join_ibss
         * join_mesh
         * set_tx_bitrate_mask
         * action
         * frame_wait_cancel
         * set_wiphy_netns
         * set_channel
         * set_wds_peer
         * Unknown command (84)
         * Unknown command (87)
         * Unknown command (85)
         * Unknown command (89)
         * Unknown command (92)
         * testmode
         * connect
         * disconnect
    Supported TX frame types:
         * IBSS: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * managed: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * AP: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * AP/VLAN: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * mesh point: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * P2P-client: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * P2P-GO: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * Unknown mode (10): 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
    Supported RX frame types:
         * IBSS: 0x0040 0x00b0 0x00c0 0x00d0
         * managed: 0x0040 0x00d0
         * AP: 0x0000 0x0020 0x0040 0x00a0 0x00b0 0x00c0 0x00d0
         * AP/VLAN: 0x0000 0x0020 0x0040 0x00a0 0x00b0 0x00c0 0x00d0
         * mesh point: 0x00b0 0x00c0 0x00d0
         * P2P-client: 0x0040 0x00d0
         * P2P-GO: 0x0000 0x0020 0x0040 0x00a0 0x00b0 0x00c0 0x00d0
         * Unknown mode (10): 0x0040 0x00d0
    Device supports RSN-IBSS.

```


wlan1
```

Wiphy phy1
    Band 1:
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
            * 2467 MHz [12] (20.0 dBm) (passive scanning, no IBSS)
            * 2472 MHz [13] (20.0 dBm) (passive scanning, no IBSS)
            * 2484 MHz [14] (20.0 dBm) (passive scanning, no IBSS)
        Bitrates (non-HT):
            * 1.0 Mbps
            * 2.0 Mbps (short preamble supported)
            * 5.5 Mbps (short preamble supported)
            * 11.0 Mbps (short preamble supported)
            * 6.0 Mbps
            * 9.0 Mbps
            * 12.0 Mbps
            * 18.0 Mbps
            * 24.0 Mbps
            * 36.0 Mbps
            * 48.0 Mbps
            * 54.0 Mbps
    max # scan SSIDs: 4
    max scan IEs length: 2285 bytes
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
         * AP/VLAN
         * WDS
         * monitor
         * mesh point
    software interface modes (can always be added):
         * AP/VLAN
         * monitor
    valid interface combinations:
         * #{ AP, mesh point } <= 8,
           total <= 8, #channels <= 1
    Supported commands:
         * new_interface
         * set_interface
         * new_key
         * new_beacon
         * new_station
         * new_mpath
         * set_mesh_params
         * set_bss
         * authenticate
         * associate
         * deauthenticate
         * disassociate
         * join_ibss
         * join_mesh
         * set_tx_bitrate_mask
         * action
         * frame_wait_cancel
         * set_wiphy_netns
         * set_channel
         * set_wds_peer
         * Unknown command (84)
         * Unknown command (87)
         * Unknown command (85)
         * Unknown command (89)
         * Unknown command (92)
         * testmode
         * connect
         * disconnect
    Supported TX frame types:
         * IBSS: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * managed: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * AP: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * AP/VLAN: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * mesh point: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * P2P-client: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * P2P-GO: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
         * Unknown mode (10): 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
    Supported RX frame types:
         * IBSS: 0x0040 0x00b0 0x00c0 0x00d0
         * managed: 0x0040 0x00d0
         * AP: 0x0000 0x0020 0x0040 0x00a0 0x00b0 0x00c0 0x00d0
         * AP/VLAN: 0x0000 0x0020 0x0040 0x00a0 0x00b0 0x00c0 0x00d0
         * mesh point: 0x00b0 0x00c0 0x00d0
         * P2P-client: 0x0040 0x00d0
         * P2P-GO: 0x0000 0x0020 0x0040 0x00a0 0x00b0 0x00c0 0x00d0
         * Unknown mode (10): 0x0040 0x00d0
    Device supports RSN-IBSS.

```


Here are my hostapd.conf files:
wlan0 -> br192 (VLAN 192)
```

interface=wlan0
bridge=br192
driver=nl80211
ssid=*redacted*
#ht_capab=[HT40+][HT40][HT20+][HT20][DSSS_CCK-40]
#commented for reasons explained below
ieee80211n=1
hw_mode=g
channel=8
macaddr_acl=1
accept_mac_file=/etc/hostapd/accept
ignore_broadcast_ssid=0
auth_algs=1
wpa=2 
wpa_passphrase=*redacted*
wpa_key_mgmt=WPA-PSK
wpa_pairwise=CCMP TKIP
rsn_pairwise=CCMP

```


wlan1 -> br10 (VLAN 10)
```

interface=wlan1
bridge=br10
driver=nl80211
ssid=*redacted*
hw_mode=b
channel=4
macaddr_acl=0
ignore_broadcast_ssid=0
auth_algs=1
wpa=2
wpa_passphrase=*redacted*
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP

```

iwconfig:
```

wlan0     IEEE 802.11bgn  Mode:Master  Tx-Power=20 dBm
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

wlan1     IEEE 802.11bg  Mode:Master  Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

iw reg get
```

country 00:
        (2402 - 2472 @ 40), (3, 20)
        (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
        (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
        (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
        (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

```

> 
Let me know if I need to add any other diagnostic information please, thanks :)

wlan1 and the bridging are all working fine, I only included the info in case anyone could point out some reason the two instances of hostapd might be causing problems for one another (like if because I'm limiting wlan1 to 802.11b operation or something) my vlans and bridges work fine, I'm running udhcpd on the VLAN 10 bridge only, and my sophos UTM firewall is running dhcp for VLAN 192.


The problem I'm having is when I try using varrying ht_capab options I have issues connecting one or more devices. For now I have the line commented out because it allows everything I have to connect. If I do anything with HT20 or HT40 my girlfriend's Inspiron 17 can't connect even though my HP Elitebook 8570 and both our droid phones will connect.


As it is now with ht_capab commented out every device connects and says 54Mbps although our actual speed is about 23Mbps running basic java/flash speed tests on the web.


with [HT40][DSSS_CCK-40] my laptop will connect and show 69Mbps sitting right next to the access point, but our phones will connect and only say 29Mbps. My laptop was getting 10Mbps on speed tests with these settings.


Does anyone know a page with simple definitions of what each ht_capab option should do?
I'm in over my head reading all the bug reports for details on this stuff and wish the hostapd wiki would have a section dedicated to this option.


If all else fails, I have a different adapter (TP-LINK TL-WN851ND, I believe is an Atheros 9k chip) in my bedroom htpc, which I'll try as a last resort.

---

### Post by david144 on 2014-05-14
[quote=david144]*Note to self*[/quote]
saving these to try later:
Possible driver: [http://ubuntuforums.org/showthread.php?t=2216871&p=12988016#post12988016](http://ubuntuforums.org/showthread.php?t=2216871&p=12988016#post12988016)
Black Opal: [http://ubuntuforums.org/showthread.php?t=2216871&p=13020616#post13020616](http://ubuntuforums.org/showthread.php?t=2216871&p=13020616#post13020616)

---

### Post by david144 on 2014-05-16
Uploading results from wireless script if they help.

Although I'm mostly looking for info regarding the ht_capab options I'm open to looking at it from other points of view as well like drivers etc.

I haven't tried the rtl8188ce git driver that everyone points to in other posts yet as I'm actually able to connect and everything works so long as I don't enable any ht_capab options, it's just not as fast as it should be (even though computers and phones will report connecting at 54Mbps they don't achieve nearly that even when in the same room with no LOS obstructions)

Thanks for any help anyone can suggest :)

---

