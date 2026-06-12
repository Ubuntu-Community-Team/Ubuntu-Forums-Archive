---
title: "Can't turn on wifi Dell latitude|E5430"
date: 2015-01-05
forum: Networking &amp; Wireless
---

### Post by peter170 on 2015-01-05
Hello,

I'm using a Dell latitude|E5430 and have just installed UBUNTU 14.04. And i cant get the WIFI to work, wired conection is fine, but no wifi.

When i run
[PHP]nm-tool[/PHP] I get
[PHP]- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        3C:A9:F4:51:6B:EC

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

[/PHP]

I ran [PHP]lspci -nnk[/PHP] not really sure if it helps but it gave me
[PHP]02:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:422b] (rev 35)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN [8086:1121]
    Kernel driver in use: iwlwifi

[/PHP]


Any ideas?

---

### Post by jeremy31 on 2015-01-05
```
rfkill list
```

---

### Post by peter170 on 2015-01-05
ok

---

### Post by peter170 on 2015-01-05
Thank you [**[COLOR=#000000]jeremy31[/COLOR]**]("http://ubuntuforums.org/member.php?u=1924242") i used the code [PHP]rfkill list[/PHP]

and got
[PHP]
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes[/PHP]

Should i unblock some how?

---

### Post by jeremy31 on 2015-01-05
Is there a switch for wifi other than the FN key combo?  If not post the result of ```
lsmod | grep dell
```

---

### Post by peter170 on 2015-01-05
Thanks [**[COLOR=#000000]jeremy31[/COLOR]**]("http://ubuntuforums.org/member.php?u=1924242")
Had been looking for a switch but to no avail.

results of the code are [PHP]dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
wmi                    19177  1 dell_wmi
[/PHP]

---

### Post by chili555 on 2015-01-05
Is it here? [http://cdn.cnetcontent.com/7a/73/7a734861-520c-4d9d-9021-4d2f5e744df4.jpg](http://cdn.cnetcontent.com/7a/73/7a734861-520c-4d9d-9021-4d2f5e744df4.jpg)

---

### Post by peter170 on 2015-01-05
O my word... never felt so silly... although anyone else finding selves down this rabbit hole i fount the wifi slid on the front below the mouse pad part of the laptop.

Thank you all very much Truly Solved

---

