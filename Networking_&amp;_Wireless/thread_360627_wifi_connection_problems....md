---
title: "wifi connection problems..."
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by marshall.robert on 2007-02-13
hi, im wondering if anyone cal help.

im having trouble connecting to my router...

here is my interfaces entry:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
wireless-essid BTVOYAGER2100-76
wireless-key s:<correct wpa key>
auto wlan0

here is my iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     802.11b/g NIC  ESSID:""  
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=24/100  Signal level=58/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:13
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

i have followed the instructions shown on [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?a%20ction=show](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?a%20ction=show) to the letter.

can anyone point me in the right direction as to what is going on, and how to solve this issue?

many thanks

-rob

---

### Post by spd106 on 2007-02-13
If you are trying to connect with a WPA key then it won't work, that's for WEP only.

For WPA you need to use wpa_supplicant. There's a sticky about WPA types that you might want to have a read through.

The easiest way is to install [Network Manager]("https://help.ubuntu.com/community/WifiDocs/NetworkManager")

---

### Post by marshall.robert on 2007-02-13
thanks for the reply, but that doesnt really explain why the iwconfig is basically empty and the interfaces is not..

-rob

---

