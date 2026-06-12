---
title: "DHCP server keeps reassigning me IP address"
date: 2024-10-07
forum: Networking &amp; Wireless
---

### Post by dmraven on 2024-10-07
Hi All,

My DHCP server on my router seems to be reassigning my IP address about every 10 minutes.
I have 30 or 40 other devices on my home network and this is the only one that seems to be getting this treatment.
On my DHCP server the lease time is set for 24 hour lease.

I have even used a different wifi adapter on my laptop, but that does not seem to make any difference.
Any idea what might be going on and how I can fix it?  Any long running network operation gets interrupted and fails.

Here is a sample from my network log:
```
Oct 07 14:22:36 ncc-1701-67 NetworkManager[1638]: <info>  [1728328956.7171] dhcp4 (wlo1): activation: beginning transaction (timeout in 45 seconds)
Oct 07 14:22:36 ncc-1701-67 NetworkManager[1638]: <info>  [1728328956.7171] dhcp4 (wlo1): state changed no lease
Oct 07 14:22:36 ncc-1701-67 NetworkManager[1638]: <info>  [1728328956.7171] dhcp4 (wlo1): activation: beginning transaction (timeout in 45 seconds)
Oct 07 14:22:36 ncc-1701-67 NetworkManager[1638]: <info>  [1728328956.7172] device (p2p-dev-wlo1): supplicant management interface state: 4way_handshake -> completed
Oct 07 14:22:39 ncc-1701-67 NetworkManager[1638]: <info>  [1728328959.0533] dhcp4 (wlo1): state changed new lease, address=10.0.0.29, acd pending
Oct 07 14:22:39 ncc-1701-67 NetworkManager[1638]: <info>  [1728328959.0534] dhcp4 (wlo1): state changed new lease, address=10.0.0.29
Oct 07 14:32:41 ncc-1701-67 NetworkManager[1638]: <info>  [1728329561.5024] device (wlo1): supplicant interface state: completed -> authenticating
Oct 07 14:32:41 ncc-1701-67 NetworkManager[1638]: <info>  [1728329561.5024] device (p2p-dev-wlo1): supplicant management interface state: completed -> authenticating
Oct 07 14:32:41 ncc-1701-67 NetworkManager[1638]: <info>  [1728329561.5408] device (wlo1): supplicant interface state: authenticating -> associating
Oct 07 14:32:41 ncc-1701-67 NetworkManager[1638]: <info>  [1728329561.5408] device (p2p-dev-wlo1): supplicant management interface state: authenticating -> associating
Oct 07 14:32:41 ncc-1701-67 NetworkManager[1638]: <info>  [1728329561.5444] device (wlo1): supplicant interface state: associating -> 4way_handshake
Oct 07 14:32:41 ncc-1701-67 NetworkManager[1638]: <info>  [1728329561.5445] device (p2p-dev-wlo1): supplicant management interface state: associating -> 4way_handshake
Oct 07 14:32:41 ncc-1701-67 NetworkManager[1638]: <info>  [1728329561.5570] device (wlo1): supplicant interface state: 4way_handshake -> completed
Oct 07 14:32:41 ncc-1701-67 NetworkManager[1638]: <info>  [1728329561.5576] device (wlo1): ip:dhcp4: restarting
Oct 07 14:32:41 ncc-1701-67 NetworkManager[1638]: <info>  [1728329561.5577] dhcp4 (wlo1): canceled DHCP transaction
Oct 07 14:32:41 ncc-1701-67 NetworkManager[1638]: <info>  [1728329561.5577] dhcp4 (wlo1): activation: beginning transaction (timeout in 45 seconds)
Oct 07 14:32:41 ncc-1701-67 NetworkManager[1638]: <info>  [1728329561.5577] dhcp4 (wlo1): state changed no lease
Oct 07 14:32:41 ncc-1701-67 NetworkManager[1638]: <info>  [1728329561.5577] dhcp4 (wlo1): activation: beginning transaction (timeout in 45 seconds)
Oct 07 14:32:41 ncc-1701-67 NetworkManager[1638]: <info>  [1728329561.5578] device (p2p-dev-wlo1): supplicant management interface state: 4way_handshake -> completed
Oct 07 14:32:44 ncc-1701-67 NetworkManager[1638]: <info>  [1728329564.1572] dhcp4 (wlo1): state changed new lease, address=10.0.0.30, acd pending
Oct 07 14:32:44 ncc-1701-67 NetworkManager[1638]: <info>  [1728329564.2931] dhcp4 (wlo1): state changed new lease, address=10.0.0.30
Oct 07 14:33:21 ncc-1701-67 NetworkManager[1638]: <info>  [1728329601.0974] device (wlo1): supplicant interface state: completed -> authenticating
Oct 07 14:33:21 ncc-1701-67 NetworkManager[1638]: <info>  [1728329601.0975] device (p2p-dev-wlo1): supplicant management interface state: completed -> authenticating
Oct 07 14:33:21 ncc-1701-67 NetworkManager[1638]: <info>  [1728329601.1331] device (wlo1): supplicant interface state: authenticating -> associating
Oct 07 14:33:21 ncc-1701-67 NetworkManager[1638]: <info>  [1728329601.1331] device (p2p-dev-wlo1): supplicant management interface state: authenticating -> associating
Oct 07 14:33:21 ncc-1701-67 NetworkManager[1638]: <info>  [1728329601.1402] device (wlo1): supplicant interface state: associating -> associated
Oct 07 14:33:21 ncc-1701-67 NetworkManager[1638]: <info>  [1728329601.1402] device (p2p-dev-wlo1): supplicant management interface state: associating -> associated
Oct 07 14:33:21 ncc-1701-67 NetworkManager[1638]: <info>  [1728329601.1459] device (wlo1): supplicant interface state: associated -> 4way_handshake
Oct 07 14:33:21 ncc-1701-67 NetworkManager[1638]: <info>  [1728329601.1459] device (p2p-dev-wlo1): supplicant management interface state: associated -> 4way_handshake
Oct 07 14:33:21 ncc-1701-67 NetworkManager[1638]: <info>  [1728329601.2254] device (wlo1): supplicant interface state: 4way_handshake -> completed
Oct 07 14:33:21 ncc-1701-67 NetworkManager[1638]: <info>  [1728329601.2261] device (wlo1): ip:dhcp4: restarting
Oct 07 14:33:21 ncc-1701-67 NetworkManager[1638]: <info>  [1728329601.2261] dhcp4 (wlo1): canceled DHCP transaction
Oct 07 14:33:21 ncc-1701-67 NetworkManager[1638]: <info>  [1728329601.2261] dhcp4 (wlo1): activation: beginning transaction (timeout in 45 seconds)
Oct 07 14:33:21 ncc-1701-67 NetworkManager[1638]: <info>  [1728329601.2261] dhcp4 (wlo1): state changed no lease
Oct 07 14:33:21 ncc-1701-67 NetworkManager[1638]: <info>  [1728329601.2261] dhcp4 (wlo1): activation: beginning transaction (timeout in 45 seconds)
Oct 07 14:33:21 ncc-1701-67 NetworkManager[1638]: <info>  [1728329601.2262] device (p2p-dev-wlo1): supplicant management interface state: 4way_handshake -> completed
Oct 07 14:33:23 ncc-1701-67 NetworkManager[1638]: <info>  [1728329603.8394] dhcp4 (wlo1): state changed new lease, address=10.0.0.31, acd pending
Oct 07 14:33:23 ncc-1701-67 NetworkManager[1638]: <info>  [1728329603.9752] dhcp4 (wlo1): state changed new lease, address=10.0.0.31



```

Thanks.

---

### Post by prcowley on 2024-10-30
I am also having a problem with random failures to reconnect the WiFi after a lease expiry with the activation message which results in a dialog box asking for the password.
 I share a WiFi router with quite a few others and don't have access to it's management config. It renews the lease every 5 minutes.

I improved, but didn't totally eliminate, the issue by making the WiFi usable to all users on the computer which means the WiFi password is stored in plain text rather than encrypted.
I would like to know what is causing this and is it fixable?
It issue only started once I upgraded Ubuntu from 24.04 to 24.10  Before that it was rock solid.

Cheers
Pete

---

