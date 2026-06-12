---
title: "hwaddreass and wpa"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by unregistr3d on 2007-07-01
hi,
i have an bcm4300 wirelesscard running with ndiswrapper and wpa_supplicant. I would like to change the MAC Address, but hwaddress does not work, the MAC is the same.

/etc/network/interfaces:
```
#The wireless network interface
auto eth0
iface eth0 inet static
hwaddress ether xx:xx:xx:xx:xx:xx
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```
/etc/wpa_supplicant/wpa_supplicant.conf:
```
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="gaWLAN"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        #psk="xxxxxxxxxxxxxxxx"
        psk=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
}

```
i tried lots of things, but nothing seams to work :(
plz help
wfg, unregistr3d

---

### Post by unregistr3d on 2007-07-01
so, i don't need it anymore i take the CableNetwork instead ;)
....this works with
```
unregistr3d@ubuntu-laptop1 ~ % sudo ifdown eth1
unregistr3d@ubuntu-laptop1 ~ % sudo ifconfig eth1 down          
unregistr3d@ubuntu-laptop1 ~ % sudo ifconfig eth1 hw ether 00:00:00:00:00:00  
unregistr3d@ubuntu-laptop1 ~ % sudo ifconfig eth1 up
unregistr3d@ubuntu-laptop1 ~ % sudo ifup eth1
```
thx

---

