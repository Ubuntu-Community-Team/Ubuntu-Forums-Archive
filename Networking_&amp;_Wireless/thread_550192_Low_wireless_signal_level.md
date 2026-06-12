---
title: "Low wireless signal level"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by matrix_83 on 2007-09-13
Hi,
I have a problem with my wireless network on Ubuntu 7.04. Signal level is very low, but on Windows Xp I don't have any problem. I post some command output:

```

franz@Franz-Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"FRANZ_WiFi"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:C1:18:94:04   
          Bit Rate=54 Mb/s   
          Link Quality=98/100  Signal level=29/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

franz@Franz-Ubuntu:~$ sudo iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:14:C1:18:94:04
                    ESSID:"FRANZ_WiFi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=100/100  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 304ms ago

```

...how you can see, signal level is low (29/100), so also network speed is too low. My network is protected by WPA2 encryption. My wireless card is an "Asus Wl-159g" (I'm using a notebook) and driver is "zd1211 rw". This i s my configuration:

```

**/etc/network/interfaces**

auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet static
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1
network 192.168.1.1
wireless-essid FRANZ_WiFi
wireless-mode managed
wireless-channel 1
wireless-rate 54M
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf
auto eth1

**/etc/wpa_supplicant.conf**
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=1000
update_config=1

network={
ssid="FRANZ_WiFi"
psk="my_key"
key_mgmt=WPA-EAP WPA-PSK
proto=RSN WPA
pairwise=CCMP TKIP
}

```

..how I can do? When i do
```
franz@Franz-Ubuntu:~$ sudo /etc/init.d/networking restart
```
I have the following error:
```

franz@Franz-Ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Operation not permitted.

```

Thanks.

---

### Post by NullHead on 2007-09-13
Did you use[this]("http://ubuntuforums.org/showthread.php?t=405990") HOW-TO?

---

### Post by matrix_83 on 2007-09-14
...but I don't have a Broadcom 43xx based wireless card...I have a zydas chipset with zd1211rw drivers...

---

### Post by NullHead on 2007-09-14
> **matrix_83 said:**
> ...but I don't have a Broadcom 43xx based wireless card...I have a zydas chipset with zd1211rw drivers...

Oh :oops: ... I didn't catch that. I'm sorry I really don't know.

---

