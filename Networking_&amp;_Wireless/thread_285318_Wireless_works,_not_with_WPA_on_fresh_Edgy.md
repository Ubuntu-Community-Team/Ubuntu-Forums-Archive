---
title: "Wireless works, not with WPA on fresh Edgy"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by Migalicious on 2006-10-26
I did a fresh install of Edgy today at school, and was able to connect to my school wireless no problem, but when I took it home to my network with WPA, it doesn't work.

```

```root@fenrir:/home/john# iwconfig eth1
eth1      unassociated  ESSID:"valhalla"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:16:B6:45:59:B1   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:XXXXXX   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

root@fenrir:/home/john# 

When I set the SSID in Network Monitor applet and set the key to ASCII and type in the ASCII key, it won't connect.  I tried bringing the interface down and up and it won't connect.

I tried installing network-manager-gnome, but I'm not sure what it is or what it's for, cause it's not an applet or a program as far as I can see (doesn't show up as a command).

---

### Post by Migalicious on 2006-10-26
Tried doing the wpa_supplicant way

wpa_sup.conf
```

```ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="your_ssid"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk=d37dce9fb2b57019c35da56ad8d02855d5e6cda322f2a85bd3951e5be8cd2535
}

I use the ```
wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf -dd
``` in /etc/network/interfaces or to try to start it from commmand line, but still nothing.  I also tried using -Dipw2200, as that's the driver thats loaded for my Intel PRO/Wireless 2200BG card.

---

### Post by Migalicious on 2006-10-26
Stupid, stupid, stupid

dhclient eth1 gets me my IP address.

However, will I have to kill this to get my wifi working at school (different ssid, no encryption)

---

