---
title: "Wireless icon missing and cant connect to wireless"
date: 2014-08-23
forum: Networking &amp; Wireless
---

### Post by alastair3 on 2014-08-23
Hi there, im running 64 bit ubuntu 14.04 LTS on a hp laptop. My wireless can  pick up the signal from the the hub but when I go to click 'connect' it  does nothing and just sits idle,but the laptop runs fine through  ethernet. Output:

NetworkManager Tool

State: connected (global)

- Device: EC:35:86:5F:50:EA ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:21:00:84:53:21

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    PlusnetWireless940D0D: Infra, 9C:97:26:94:0D:0D, Freq 2452 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    TALKTALK-729A90: Infra, 40:CB:A8:72:9A:92, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    WIGGINS:         Infra, A4:B1:E9:36:19:A5, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    BTWifi-X:        Infra, 22:FE:F4:2C:DB:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2 Enterprise
    NETGEAR:         Infra, E0:91:F5:4F:67:BA, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    TNCAP8F2D57:     Infra, 9C:97:26:8F:2D:57, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    BTHub3-KTT7:     Infra, 00:FE:F4:2C:DB:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    BTHomeHub-60EB:  Infra, 00:18:F6:97:FD:6F, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WEP
    BTWiFi:          Infra, 02:18:F6:97:FD:70, Freq 2462 MHz, Rate 54 Mb/s, Strength 37
    BTWifi-with-FON: Infra, 02:FE:F4:2C:DB:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 22


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:22:64:67:C8:7D

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.69
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254




I am new to ubuntu and would like to learn and understand how to fix it, your help will be much appreciated as it is annoying having to sit by the router via the ethernet cable!

---

### Post by varunendra on 2014-08-23
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

**PS:**
I see that your last post in June about the same issue got unanswered. You can always bump your thread every 24 hours or more if it doesn't get answers.

**PPS:**
As a purely blind shot, please try this fix -
```
sudo apt-get purge bcmwl-kernel-source
```
Reboot and see if your wifi works now. If not, just run the script suggested above and post back its report.

---

