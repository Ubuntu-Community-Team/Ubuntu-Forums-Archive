---
title: "interfaces file."
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by solaceinsilence9 on 2008-10-21
I've done some googling and I have turned up no answers. So I hope someone can help me here. My wireless network will not connect automatically when I bootup. I've checked my settings and I have the correct SSID as well as the correct passphrase and other settings as well. I think the problem might be with my interfaces file, however, Im not exactly sure how to read the interfaces file and see if it is messed up in anyway. Here is my interfaces file:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback










iface wlan0 inet dhcp
wpa-psk 6e598fc8e0c20e173f9092faf80b6690f3801c13184fda6547d3c72bc81b09a6
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid 4719_Home_WIFI

auto wlan0
```


please be aware that I added wpa-proto WPA. WIFI was not working BEFORE and still is not working. Also, I can get the WIFI to work, I just have to activate roaming mode, deactivate it, then manually configure the WIFI connection. Can someone give me a hand?

---

### Post by solaceinsilence9 on 2008-10-21
bump

---

