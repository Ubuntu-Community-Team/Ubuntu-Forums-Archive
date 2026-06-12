---
title: "Install wi-fi USB Adapter TEW-648UB in Ubuntu 14.04."
date: 2015-04-07
forum: Networking &amp; Wireless
---

### Post by leptodon on 2015-04-07
Hi I've done all what told in this [topic]("http://ubuntuforums.org/showthread.php?t=2174290") but wifi still doesn't work.


All steps my config

```
[COLOR=#000000][FONT=Ubuntu Mono]lsmod | grep r8712u
[/FONT][/COLOR]r8712u                158706  0

```

```
[COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep r8712u[/FONT][/COLOR][   13.848482] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   13.851035] r8712u: Staging version
[   13.851105] r8712u: register rtl8712_netdev_ops to netdev_ops
[   13.851120] usb 1-4: r8712u: USB_SPEED_HIGH with 4 endpoints
[   13.851768] usb 1-4: r8712u: Boot from EFUSE: Autoload OK
[   14.534771] usb 1-4: r8712u: CustomerID = 0x0000
[   14.534788] usb 1-4: r8712u: MAC Address from efuse = d8:eb:97:28:08:bd
[   14.534798] usb 1-4: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   14.535163] usbcore: registered new interface driver r8712u
[   18.672520] r8712u 1-4:1.0 wlan0: 1 RCR=0x153f00e
[   18.673253] r8712u 1-4:1.0 wlan0: 2 RCR=0x553f00e

```
```
[COLOR=#000000][FONT=Ubuntu Mono]iwconfig[/FONT][/COLOR]

wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.



```
> [COLOR=#000000]Does it scan and see networks?[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]sudo iwlist wlan0 scan[/FONT][/COLOR]
```
Yes it searched all wifi network in range.


```

nano /etc/network/interfaces

auto lo eth0
iface lo inet loopback


iface eth0 inet static
address 192.168.1.20
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1


iface wlan0 inet static
address 192.168.1.25
gateway 192.168.1.1
dns-nameservers 192.168.1.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid leptodon
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 997b19c1b890e9398788eb91f8c139a2cbad21c7ef88f07a640009672deff820
auto wlan0

```


My problem is: 
- USB wi-fi don't start automaticly (only after [COLOR=#000000][FONT=dejavu sans mono]ifconfig wlan0 up )[/FONT][/COLOR]
- When system booting type that network configured more then 60sec...
- when start wlan0 "ifconfig wlan0 up" wifi still not connect to point

---

### Post by chili555 on 2015-04-07
Man, oh man! That is one busy interfaces file you have there! Wow! 

I suggest you amend it to:```
auto lo 
iface lo inet loopback


iface eth0 inet static
address 192.168.1.20
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1

auto wlan0
iface wlan0 inet static
address 192.168.1.25
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1
wpa-ssid leptodon
wpa-psk <your_key_in_clear_text>
```Then restart the interface:```
sudo ifdown wlan0 && sudo ifup wlan0
```And test:```
ping -c3 www.ubuntu.com
```

---

### Post by leptodon on 2015-04-07
Thx a lot. Everything is fine!:p

---

### Post by chili555 on 2015-04-07
> **leptodon said:**
> Thx a lot. Everything is fine!:pGlad it's working! Please mark the thread Solved. The searchers will appreciate it.

---

### Post by leptodon on 2015-04-11
One more qustion. How to do usb wi-fi adapter unique? Because when i instert other usb device, wi-fi not work.

---

### Post by chili555 on 2015-04-11
The other USB probably is set up in the system as wlan[COLOR="#FF0000"]1[/COLOR] as it's an entirely different device. Your interfaces file has no declaration for wlan1.

---

