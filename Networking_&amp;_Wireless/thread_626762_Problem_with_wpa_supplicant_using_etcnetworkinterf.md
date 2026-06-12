---
title: "Problem with wpa_supplicant using /etc/network/interfaces file"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by snakeyes30 on 2007-11-29
Hi,

When I am trying to connect to my wireless network. It is protected using WPA. I have a wireless card with the Broadcom BCM4306 chipset and I have installed ndiswrapped.

I have configured wpa in my /etc/network/interfaces file.
```


shastrs5-~-) cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid BeBox
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk MYPSK

```

When I try to run "sudo ifup eth1" I am unable to get an ip address using DHCP.

However when I run "sudo wpa_supplicant -ieth1 -Dwext -c/etc/wpa_supplicant/wpa_supplicant.conf" followed by "sudo dhclient eth1" it connects.

I am wondering why I need to run wpa_supplicant separately. I thought that wpa_supplicant should be started by the interfaces file.

My wpa_supplicant.conf file looks like this: 
```

shastrs5-~-) cat /etc/wpa_supplicant/wpa_supplicant.conf
network={
    ssid="BeBox"
    scan_ssid=1
    key_mgmt=WPA-PSK
    psk="MYKEY"
}


```

Please help.

Thanks.
Sam

---

### Post by kevdog on 2007-11-29
Try removing the address and netmask entries under the lo entries in the /etc/network/interfaces.

afterwards, what happens if you do

sudo ifup -a

---

