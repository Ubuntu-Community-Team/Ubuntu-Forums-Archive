---
title: "Configuring Hardy Wifi to prefer a particular BSSID"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by mishad on 2008-08-31
Have a Lenovo Thinkpad z60m with Intel 2915 802.11 a/b/g, with Hardy Heron 8.04 installed. Wifi works fine using Network Manager (0.6.6)

My home wifi has 3 APs all on the same (non-hidden) SSID

x.x.x.1: ADSL Modem/Router 11g WPA TKIP

x.x.x.2: Extender (wireless bridge) 11g WPA TKIP/AES

x.x.x.3: Extender (wireless bridge) 11g WPA TKIP/AES

The .2 and .3 APs are DD-WRT running in wireless bridge mode. So .2 is a client of .1, and .2 also acts as an AP to "re-broadcast" the connection using the same SSID. Similarly .3 is a client of .2 and also re-broadcasts the wifi again with the same SSID. All the APs have different BSSIDs, and clients correctly roam between them.

Obviously there's a compromise with this set up, as the available bandwidth is dropped by a factor of 4 or so due to contention as the extenders relay packets back to the main modem/router, but it works for me[1]. The bandwidth loss is not a real problem for internet access, but it is noticable for file transfers between wireless clients and wired fileservers connected directly to the .1 router.

Ideally, clients in range of .1 would connect directly to it, rather than to .2 (or .3). Unfortunately, a combination of geography, walls, and the higher-power of the Buffalo, means that clients in the main house usually connect to .2.

Is it possible to configure my Ubuntu machine to prefer .1 to .2/.3 even when .2/.3 has higher strength -- e.g. falling back to .2/.3 only where .1 cannot connect at 18Mbps or more and .2/.3 has at least 10% higher signal strength? (We have 3 Heron-based laptops, actually: second one is an eeebuntu, the other an old laptop with Ralink RT2500 PCMCIA, so if I can fix this for mine I can roll it out to those too.)

How/could I configure this:

i) with the command line?
ii) with Network Manager 0.6.x?
iii) with Network Manager 0.7.x?
iv) with some other tool (e.g. wicd or wifi-radar)?

Thanks in advance

Misha

[1] The .1 modem/router is ISP-provided; .2 and .3 are Buffalo WHR-HP-54 units; the combination of the daisy chaining and the higher power enables the signal to reach all the property. .3 cannot connect directly to .1 wirelessly, and running cable is too much effort.

---

