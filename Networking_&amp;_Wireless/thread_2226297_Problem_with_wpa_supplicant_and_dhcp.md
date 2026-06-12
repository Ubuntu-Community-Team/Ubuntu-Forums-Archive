---
title: "Problem with wpa_supplicant and dhcp"
date: 2014-05-26
forum: Networking &amp; Wireless
---

### Post by quentin3 on 2014-05-26
Hello,
I'm trying to connect to wireless networks using wpa_supplicant.

Here is my [FONT=courier new]/etc/network/interfaces[/FONT]
```
auto wlan0
iface wlan0 inet dhcp
  wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```

And the [FONT=courier new]/etc/wpa_supplicant/wpa_supplicant.conf[/FONT]
```
ap_scan=1
fast_reauth=1

network={
ssid="SSID1"     
psk="passphrase1"     
priority=10 
id_str="network1" 
} 

network={ 
ssid="SSID2" 
psk="passphrase2"     
priority=1     
id_str="network2" 
}
```

It works at system start, but when it switch from a wireless network to another, no dhcp request is send, and ip address is still the same.
I have to do ```
sudo ifdown wlan0 && sudo ifup wlan0
```
to get the ip address.

---

