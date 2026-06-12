---
title: "Ubuntu router/AP Wireless speed download much slower than upload"
date: 2018-01-01
forum: Networking &amp; Wireless
---

### Post by beachmountain on 2018-01-01
Happy New Years all! I'm starting my new year with my first post here. I'm no Ubuntu export, so please be gentle :D

I recently got a 100/100Mbps fiber connection and my old router/ap (TP-LINK) only gave me only about 35Mbps wireless down but close to 100 up. I thought it might be due to the router being old (tried disabling WMM as suggested on forums but no success) so I have now tried building a router/AP on a [mini-PC]("https://www.amazon.com/gp/product/B00U3LIRYW/ref=od_aui_detailpages00?ie=UTF8&psc=1") with Ubuntu (16.04) by following guides on the Internet ([this]("https://killtacknine.com/building-an-ubuntu-16-04-router-part-1-network-interfaces/") and [this]("https://help.ubuntu.com/community/Router")) but the problem persists.

When I use a cable I always get close to 100/100 in the online speed tests I have done (both to Internet and when downloading files directly from the router which is even faster). The wireless speed seems now to always be around 45Mbps, which makes me suspect I somehow only get 54Mbps in the download direction. For uploading I get close to 100mbps. The wireless adapter should be able to do 802.11n 300mbps according to the spec. I get the same result from all wireless clients (pc's and phones) and the distance between clients and router when testing is under 1 meter with no obstacles.

There are no close neighbours, so no interfering other wifis. I have tried all different available channels, but performance is the same or a little bit slower on all channels.

I have found other threads about this problem on different forums on the Internet but had no success with the solutions suggested. Most common suggestion is to turn off wmm or set "ht_capab=[SHORT-GI-40][HT40+][HT40-][DSSS_CCK-40]" which I have tried and did not make a difference.

My basic setup is:

[Mini-PC Intel Celeron Dual Core 1.8ghz Cpu Media Box]("https://www.amazon.com/gp/product/B00U3LIRYW/ref=od_aui_detailpages00?ie=UTF8&psc=1")
Ubuntu 16.04 with 4.10 kernel
1 wireless adapter (RTL8192CE PCIe Wireless Network Adapter), two ethernet adapters.
hostapd for wireless
DHCP: isc-dhcp-server (using bridge interface with the wireless and one of the ethernet adapters)
Firewall: UFW
NAT via UFW
DNS: bind9

Here are my configurations, if something is missing, please just let me know and I will provide it.

My hostapd.conf:


```
# /etc/hostapd/hostapd.conf


# The interface to run the access point on
interface=wlp2s0


# Bridge with LAN interface on br0
bridge=br0


# The wireless network name
ssid="Svinternet"


# Sets up the regulatory domain of the network. This sets
# up things like available channels, transmit power, etc.
# based on the country the network is operating in.
country_code=SE


# Enable IEEE 802.11d which actually enforces the policies
# mandated by the country_code.
ieee80211d=1


# WiFi mode to use (a, b or g). The g mode does n too, don't
# panic.
hw_mode=g


# Enable n mode as well.
ieee80211n=1


ht_capab=[SHORT-GI-40][HT40+][HT40-][DSSS_CCK-40]


# The wireless channel to use. Use a WiFi scanner app on
# your phone to find a channel without to much interference
# and choose that one.
channel=3


# Some sort of protocol detail. I dunno, you just need it.
wmm_enabled=1


# Use shared key authentication
auth_algs=1


# Enable WPA2 for authentication and configure the key
# management and encryption types.
wpa=2
wpa_key_mgmt=WPA-PSK
rsn_pairwise=CCMP


# Set the password for the network
wpa_passphrase=*****

```


Result from "iw dev wlp2s0 station dump" (used it to see if wmm was on/off, dont know if it is usefull)


```
Station e0:06:e6:52:2d:f9 (on wlp2s0)
        inactive time:  4 ms
        rx bytes:       120541806
        rx packets:     132350
        tx bytes:       120569658
        tx packets:     125982
        tx retries:     0
        tx failed:      0
        signal:         -52 dBm
        signal avg:     -42 dBm
        tx bitrate:     130.0 MBit/s MCS 15
        rx bitrate:     1.0 MBit/s 40MHz
        authorized:     yes
        authenticated:  yes
        preamble:       short
        WMM/WME:        yes
        MFP:            no
        TDLS peer:      no

```


Result from "iw list":


```
Wiphy phy0
        max # scan SSIDs: 4
        max scan IEs length: 2257 bytes
        RTS threshold: 2347
        Retry short limit: 7
        Retry long limit: 4
        Coverage class: 0 (up to 0m)
        Device supports RSN-IBSS.
        Supported Ciphers:
                * WEP40 (00-0f-ac:1)
                * WEP104 (00-0f-ac:5)
                * TKIP (00-0f-ac:2)
                * CCMP (00-0f-ac:4)
                * 00-0f-ac:10
                * GCMP (00-0f-ac:8)
                * 00-0f-ac:9
                * CMAC (00-0f-ac:6)
                * 00-0f-ac:13
                * 00-0f-ac:11
                * 00-0f-ac:12
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
        Band 1:
                Capabilities: 0x186e
                        HT20/HT40
                        SM Power Save disabled
                        RX HT20 SGI
                        RX HT40 SGI
                        No RX STBC
                        Max AMSDU length: 7935 bytes
                        DSSS/CCK HT40
                Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
                Minimum RX AMPDU time spacing: 16 usec (0x07)
                HT TX/RX MCS rate indexes supported: 0-15, 32
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
                        * 2467 MHz [12] (20.0 dBm)
                        * 2472 MHz [13] (20.0 dBm)
                        * 2484 MHz [14] (disabled)
        Supported commands:
                 * new_interface
                 * set_interface
                 * new_key
                 * start_ap
                 * new_station
                 * new_mpath
                 * set_mesh_config
                 * set_bss
                 * authenticate
                 * associate
                 * deauthenticate
                 * disassociate
                 * join_ibss
                 * join_mesh
                 * remain_on_channel
                 * set_tx_bitrate_mask
                 * frame
                 * frame_wait_cancel
                 * set_wiphy_netns
                 * set_channel
                 * set_wds_peer
                 * probe_client
                 * set_noack_map
                 * register_beacons
                 * start_p2p_device
                 * set_mcast_rate
                 * connect
                 * disconnect
                 * Unknown command (104)
        Supported TX frame types:
                 * IBSS: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * managed: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * AP: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * AP/VLAN: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * mesh point: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * P2P-client: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * P2P-GO: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * P2P-device: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
        Supported RX frame types:
                 * IBSS: 0x40 0xb0 0xc0 0xd0
                 * managed: 0x40 0xd0
                 * AP: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
                 * AP/VLAN: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
                 * mesh point: 0xb0 0xc0 0xd0
                 * P2P-client: 0x40 0xd0
                 * P2P-GO: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
                 * P2P-device: 0x40 0xd0
        software interface modes (can always be added):
                 * AP/VLAN
                 * monitor
        interface combinations are not supported
        HT Capability overrides:
                 * MCS: ff ff ff ff ff ff ff ff ff ff
                 * maximum A-MSDU length
                 * supported channel width
                 * short GI for 40 MHz
                 * max A-MPDU length exponent
                 * min MPDU start spacing
        Device supports TX status socket option.
        Device supports HT-IBSS.
        Device supports SAE with AUTHENTICATE command
        Device supports low priority scan.
        Device supports scan flush.
        Device supports AP scan.
        Device supports per-vif TX power setting
        Driver supports full state transitions for AP/GO clients
        Driver supports a userspace MPM

```


Result from wireless-info here: [https://paste.ubuntu.com/26299040/](https://paste.ubuntu.com/26299040/)

See attached images for result from wifi analyser and result from bandwith speed test (Swedish bredbandskollen.se, the standard site for testing in my Country).

[ATTACH=CONFIG]277991[/ATTACH][ATTACH=CONFIG]277992[/ATTACH]

I really appreciate some help with this, I'm quite a few hours into this now without any progress. Thanks! /Fredrik

---

### Post by TheFu on 2018-01-01
Probably not the answer you want or that you can use right now.  Just passing on my experience.

Lots of people have issues with Realtek network adapters.  I find it best to simply avoid them to avoid the issues.  For wired ethernet, I go with an Intel PRO/1000 (family) NIC.  This has the added niceness of offloading much of the work that a CPU might do to the ASIC in the NIC, saving the CPU for work only a CPU can perform, not network stuff.

For wifi stuff, especially on a router, I recommend Ubiquiti APs to solve any sorts of connection or performance issues.  The are good.  They have fixed issues with tp-link, netgear, linksys, cisco, and other wifi-routers.  For me, it simply isn't worth the time/effort to troubleshoot wifi issues on a router when I can spend $80, get a nice Ubiquiti AC access point and have no issues.

I have a $150-ish AMD router (an APU2) that doesn't have any wifi capability.  For that, an AP is connected which uses PoE. That solves 2 issues.  The router location is seldom the best location for a wifi-AP and getting a power socket to the ceiling at the center of the house.  PoE injectors can be placed near the router-AP connection, then run up through the attic and into a tiny mounting hole in the ceiling for beautiful coverage.  If you have a difficult-for-wifi building, you can have multiple ubiquiti APs in a staggered configuration using the same SSIDs.  All of them can be managed centrally with an understanding of the other APs.  For a single-AP setup, an Android app can be used for management.  The solution scales to hotels with hundreds of APs, if you need it.

IMHO, better than spending "a few hours" on bad hardware.

Also, I'd like to say "congratulations" to moving to a maintainable router setup.  Your setup, minus the wifi, should serve you for at least a decade.
If you want another, well-regarded, how-to - [https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/) - I spoke with Jim at a conference after his presentation about building your own router. At the time, I wasn't convinced that using Linux with a server distro was the best move.  The more stuff there is on the router, the more likely there will be security-impacting bugs.  I was a BSD snob for routers.  He convinced me about the importance of available patches and that having wifi as a separate device was highly desirable.

Hope this is helpful in some way.

---

### Post by beachmountain on 2018-01-04
Thank you so much for your answer, it was both helpful and educating!

I read up about the Ubiquiti AP's and they seem very highly regarded. I have now ordered a Ubiquiti AC LR and will separate the router from the AP. I really like the idea of POE and look forward to testing it. As a bonus, in my opinion, the Ubiquiti also looks better than "a box with antennas".

Finally I read Jims article which was very interesting and gave me lots of more good configuration ideas for the router. Thanks!

Best Regards
Fredrik

---

### Post by TheFu on 2018-01-04
In your original post, when you said "cable", I hope you meant ethernet and not COAX.

Happy you found it useful.  Probably a little late now, but unless you want to cover an estate, the LR models are overkill.  There's a youtube video of a guy riding a 4-wheeler to the edge of his property checking wifi signal the entire way with an LR ubiquiti. Looked like he had about 4 acres of land.  The inside was well covered too. ;)

And if the clients aren't using AC wifi protocols, then getting 300Mbps is highly, highly, unlikely.  Just 1 older wifi adapter connected can bring the entire wifi network down to 54Mbps tops.  If you aren't certain which client is causing the issue, connect them 1 at a time.

Also, know there are only 3 non-overlapping 2.4Ghz channels, those are 1, 6, and 11.  If you are in Japan, there's another (13 or is it 14?), which I always use in Japan, but it is illegal everywhere else in the world.  Only people in very high density locations with lots of other APs should use any 2.4Ghz channels besides 1, 6, 11.  There are handy android apps which will help you determine which channels you should be using, but the rule is to pick the one of those three that has the least signal and fewest other devices.  So if your neighbors are on 1 and 6, then you should use 11.  If your neighbors are on 3 and 7, you should still use 11, since 3 overlaps with 1 and 7 overlaps with 6.

With "AC" ( a newer wifi standard ), things get a little better, but only when all the clients talk the same standard.

Also, be aware that the 802.11n standard allows for all sorts of different connections and performance.  A cheap wifi-N device might only be able to connect at 72Mbps at the most.  Early models wouldn't do 150-300Mbps connections. The chips simply didn't support those speeds.  I have a Dell laptop from 2011 like that.

I've designed over 1200 wifi deployments in my career.  I avoid wifi whenever possible. It isn't very stable. If you look at the actual throughput supported, it goes up and down all the time, even if you are 20 miles in the middle of nowhere.  Atmospheric conditions drastically impact wifi performance, even indoors.  I use a powerline setup to bridge my router to another floor.  It only provides 60Mbps, but that is still better than most wifi connections.  For moving multi-gigabyte files, this is important.  Also for streaming video media.  Audio streaming really doesn't care, since even the worst wifi would be more than sufficient.  Wire CAT5e ethernet is always the most stable.  Consistent, 900Mbps+ throughput.  Well worth it.

I use a USB GigE adapter instead of wifi on a chromebook, just to get a better, faster, consistent connection.

Of course, if you are just checking email or surfing, then wifi is probably more than fast enough.  Anything over 128Kbps is fast enough for most of that stuff, assuming you block ads.  Wifi is very useful.

---

