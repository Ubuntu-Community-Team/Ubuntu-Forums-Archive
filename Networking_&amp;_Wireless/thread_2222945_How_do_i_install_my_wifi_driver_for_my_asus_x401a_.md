---
title: "How do i install my wifi driver for my asus x401a (.bz2.bz2 file)?"
date: 2014-05-08
forum: Networking &amp; Wireless
---

### Post by willzhigaylo on 2014-05-08
I need to install my wifi driver on my ASUS X401A, here is the file name: 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_v2.bz2.bz2, How would I do so?

---

### Post by chili555 on 2014-05-08
I am quite confident that you'd find the circa 2011 driver file will not compile on any recent Ubuntu version. If you are not using a more recent version, I suggest that you should. There has been considerable progress made in drivers in the last 3 1/2 years.

Please start by telling is more information:```
lspci -nn | grep 0280
lsb_release -d
uname -r
```

---

### Post by willzhigaylo on 2014-05-08
```
 wzhigaylo@ASUSX401A1:~$ lspci -nn | grep 0280 02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390] wzhigaylo@ASUSX401A1:~$ lsb_release -d Description:    Ubuntu 14.04 LTS wzhigaylo@ASUSX401A1:~$ uname -r 3.13.0-24-generic
```

---

### Post by chili555 on 2014-05-08
Your device is covered by the native driver rt2800pci. Is it not working as expected? What are your symptoms?```
iwconfig
nm-tool
rfkill list all
```

---

### Post by willzhigaylo on 2014-05-08
```
wzhigaylo@ASUSX401A1:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"ZHOME"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 98:2C:BE:BD:0C:09   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:136  Invalid misc:27   Missed beacon:0



```
```
wzhigaylo@ASUSX401A1:~$ nm-tool

NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        50:46:5D:2F:88:17


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0  [ZHOME] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        08:3E:8E:36:29:DA


  Capabilities:
    Speed:           11 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *ZHOME:          Infra, 98:2C:BE:BD:0C:09, Freq 2452 MHz, Rate 54 Mb/s, Strength 61 WPA2
    2WIRE505:        Infra, AC:5D:10:70:0D:F9, Freq 2427 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.65
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254



```
```
wzhigaylo@ASUSX401A1:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```
My problems are that wifi on Ubuntu (compared to Win 8.1) is WAY slower, has a lower signal, and may disconnect.

---

### Post by willzhigaylo on 2014-05-08
In order for wifi on Ubuntu to work I have to get closer to the router whereas it will work fine with Windows in my room.

---

### Post by chili555 on 2014-05-08
Let's try a driver parameter:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y 
```If it helps, we'll write one quick file to make it permanent.

---

### Post by willzhigaylo on 2014-05-08
I tried that and now it won't connect, I'm using Ethernet now.

---

### Post by willzhigaylo on 2014-05-09
**Any help would be appreciated, thanks!**

---

### Post by Hadaka on 2014-05-09
hi, please do ..
```
sudo modprobe rt2800pci
```
did that bring it back to life?

---

