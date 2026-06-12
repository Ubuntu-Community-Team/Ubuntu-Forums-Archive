---
title: "NetworkManager not showing wifi, device is recognised elsewhere."
date: 2017-03-07
forum: Networking &amp; Wireless
---

### Post by jakoid on 2017-03-07
Hi, 
I'm on a dell d630 with a 3945abg wireless network card, using the iwlwifi-3945-2.ucode driver. I've never been able to see any wireless devices in NetworkManager despite a lot of googling, but have been able to connect via WICD. I'd like to get NetworkManager working so that I can use the network-manager-gnome-openvpn package.

Here's the output of *iwconfig*:
```
lo        no wireless extensions.

enp9s0    no wireless extensions.


wlp12s0   IEEE 802.11abg  ESSID:"VM9671172"  
          Mode:Managed  Frequency:5.58 GHz  Access Point: C0:05:C2:D5:9D:97   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:12   Missed beacon:0

```

*nmcli networking connectivity check*:
```
none
```

*iwlist wlp12s0 scan* returns various networks, and I can view them in WICD but nothing in NM.
Any help is much appreciated.

---

### Post by jakoid on 2017-03-07
UPDATE:
I managed to get the wireless to show using [this]("http://askubuntu.com/questions/211347/networkmanager-refuses-to-manage-my-wlan-interface") guys method, which doesn't let me change any other network settings. It only shows when I first log in, and the disconnects whenever I click on my network.

---

