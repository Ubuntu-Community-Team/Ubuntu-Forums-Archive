---
title: "using wireless with password"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by Shantesh on 2007-05-04
Guys,

I am using Ubuntu 6.06 and i am unable to make my home network work for me as its password protected. I tried entering my password  using the ASCII as the hex value but it doesnt work. I just typed my password in words in both the cases. I dont know how to convert  it into ASCII or HEX , do i really need to? if yes then how? also i want an order of selection of networks, like at home i want to use my password protected network and at work it should connect to pubnet.pdx.edu. I have provided a copy of my interfaces file below. 

[PHP]
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid pubnet.pdx.edu

auto wlan0
iface wlan0 inet dhcp
[/PHP]

Please help me !
Thanks in advance :)

---

### Post by chriscando on 2007-05-04
How about just using the gui in System > Administration > Network. You can setup a wep key there. My interfaces file looks like this
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
```

---

### Post by Shantesh on 2007-05-05
doesnt work

need help !!!

---

### Post by Floppyjoe on 2007-05-05
> **Shantesh said:**
> Guys,

I am using Ubuntu 6.06 and i am unable to make my home network work for me as its password protected. I tried entering my password  using the ASCII as the hex value but it doesnt work. I just typed my password in words in both the cases. I dont know how to convert  it into ASCII or HEX , do i really need to? if yes then how? also i want an order of selection of networks, like at home i want to use my password protected network and at work it should connect to pubnet.pdx.edu. I have provided a copy of my interfaces file below. 

[PHP]
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid pubnet.pdx.edu

auto wlan0
iface wlan0 inet dhcp
[/PHP]

Please help me !
Thanks in advance :)

If you are using a laptop and roaming around with it I would install network-manager and network-manager-gnome.  For network-manager to work in Ubuntu 6.06 you need to comment out all but the lo interface in your /etc/network/interfaces file, like this:
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp
#wireless-essid pubnet.pdx.edu

#auto wlan0
#iface wlan0 inet dhcp
```
This would work if you are using wep encryption.
If you are using WPA encryption you need to also install wpa-supplicant and set that config file up.
This is a guide to WPA encryption:
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

Good Luck!

---

