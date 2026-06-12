---
title: "Problem with SAE encrypted mesh"
date: 2016-07-14
forum: Networking &amp; Wireless
---

### Post by write-more-code on 2016-07-14
I am trying to create a secure wifi mesh network using wpa_supplicant 2.6 and atheros 9462 card, ubuntu 16.04 with 4.4 kernel. I pulled the 2.6 version of wpa_supplicant and recompiled with CONFIG_MESH=y and CONFIG_SAE=y, Using the wpa_supplicant.conf file below, my machines will connect and create an open mesh. The machines establish a mesh configuration. Assigning static addresses to the wlan interfaces allows the machines to work together. I can ping between machines and ssh between them. Everything works well, but I need to encrypt the communication.

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
        ssid="mynetwork"
        frequency=2412
        mode=5
        key_mgmt=NONE
#       key_mgmt=SAE
        psk="some password"
}

To enable encryption, I uncommented key_mgmt=SAE and commenting key_mgmt=NONE. Restarting wpa_supplicant creates the mesh network. Each station shows up as MESH-PEER-CONNECTED. SAE negotiation takes place and appears to complete successfully. Final messages from a detailed dump by wpa_supplicant show:

wlan0: MESH-PEER-CONNECTED 44:c3:06:30:46:97
nl80211: Event message available
nl80211: Drv Event 60 (NL80211_CMD_FRAME_TX_STATUS) received for wlan0
nl80211: MLME event 60 (NL80211_CMD_FRAME_TX_STATUS) on wlan0(44:c3:06:30:46:07) A1=44:c3:06:30:46:97 A2=44:c3:06:30:46:07
nl80211: MLME event frame - hexdump(len=199): d0 00 00 00 44 c3 06 30 46 97 44 c3 06 30 46 07 44 c3 06 30 46 07 00 00 0f 02 10 00 01 00 01 08 82 84 8b 96 8c 12 98 24 32 04 b0 48 60 6c 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 08 00 00 72 08 6d 61 73 6c 6f 63 6f 32 71 07 01 01 00 01 01 00 09 75 16 01 00 33 20 13 fd f3 68 c7 03 c5 b6 78 fd 79 5c 82 88 9d 43 da f8 8c 10 db 09 f9 4c 35 9b 07 c6 1f 59 84 54 7c 8f d2 16 9a d1 91 dd d1 4d 65 c3 da 40 0a 2b fc a4 e8 c6 b9 5b aa a4 bc 39 94 b3 fa 7d a3 c7 1e 7d 52 94 d3 d5 54 da b1 95 6a 6b 29 e4 6a 19 76 92 35 26 3a 5b d1 53 97 e0 79 07 6a be 64 d8 49 35 7a 57 16 2c 49 3a ba 07
nl80211: Frame TX status event
nl80211: Action TX status: cookie=011 (match) (ack=1)
wlan0: Event TX_STATUS (17) received
wlan0: EVENT_TX_STATUS dst=44:c3:06:30:46:97 type=0 stype=13
RTM_NEWLINK: ifi_index=3 ifname=wlan0 operstate=6 linkmode=1 ifi_family=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])


Things get strange from there. Pinging from box A (192.168.2.100) to box B (192.168.2.101) returns Destination Host Unreachable. Running tcpdump on box A shows the following ARP requests:

20:34:32.860250 ARP, Request who-has 192.168.2.101 tell 192.168.2.100, length 28
20:34:33.860237 ARP, Request who-has 192.168.2.101 tell 192.168.2.100, length 28
20:34:34.860356 ARP, Request who-has 192.168.2.101 tell 192.168.2.100, length 28
20:34:35.860227 ARP, Request who-has 192.168.2.101 tell 192.168.2.100, length 28
20:34:36.860249 ARP, Request who-has 192.168.2.101 tell 192.168.2.100, length 28
20:34:37.860370 ARP, Request who-has 192.168.2.101 tell 192.168.2.100, length 28
20:34:38.860249 ARP, Request who-has 192.168.2.101 tell 192.168.2.100, length 28
20:34:39.860237 ARP, Request who-has 192.168.2.101 tell 192.168.2.100, length 28

Running tcpdump on box B shows the request is received and a reply is sent; however, the reply is never received on box A. Since the ARP cache is not getting updated, no other traffic can go across the network. Box A had an incomplete ARP cache entry for box B, but box B had a good entry for box A.

I manually populated the ARP cache on box A for box B. At this point tcp on box A shows:

20:51:22.214402 IP 192.168.2.100 > 192.168.2.101: ICMP echo request, id 1886, seq 1801, length 64
20:51:23.222395 IP 192.168.2.100 > 192.168.2.101: ICMP echo request, id 1886, seq 1802, length 64
20:51:24.230407 IP 192.168.2.100 > 192.168.2.101: ICMP echo request, id 1886, seq 1803, length 64
20:51:25.238399 IP 192.168.2.100 > 192.168.2.101: ICMP echo request, id 1886, seq 1804, length 64
20:51:26.246407 IP 192.168.2.100 > 192.168.2.101: ICMP echo request, id 1886, seq 1805, length 64

Tcpdump on box B does not show any packets coming through.

If I reverse roles between boxes A and B, the results are the exact opposive. Box B sends ARP requests to box A, which receives them and replies. Box B never gets the reply.

This seems to be related to encryption, but not where to look next or if ARP is encrypted. ARP works fine without encryption enabled. The ARP request goes through fine, but responses fail. The results seem like the atheros card is receiving broadcast traffic, but not directed traffic.

Any pointers on where to look next would be fantastic. Thanks

---

### Post by zanlik on 2016-10-28
Hi, 
I have the same problem as above. 
Have you found a solution ?

---

### Post by write-more-code on 2016-10-28
I was not able to get wpa_supplicant to run a mesh, but was able to get a mesh environment running using just authsae to associate the devices. Then added babeld to handle routing and DHCP for address assignment to get the network completely set up. Try that route and let me know if you have any issues.

---

