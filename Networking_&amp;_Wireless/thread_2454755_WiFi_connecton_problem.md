---
title: "WiFi connecton problem"
date: 2020-12-05
forum: Networking &amp; Wireless
---

### Post by scpecialist on 2020-12-05
Hi;

I have WLAN connection problem on my Nvidia Jetson Nano 2Gb. 
I'm connectted my Nvidia Jetson Nano 2Gb on serial port to installation and configuration.

During configuration I provide to WiFi’s WPA/PSK key but WiFi not configuring.
It give me " Failure of key exchange and association"
I’m double check every thing but I recive this error again and again.!

[IMG]https://i.postimg.cc/0QHbrwW5/config-error.png[/IMG]

I'm pass this step, after the finishing setup I can tyr to wpa_passphrase command to add a line to wpa_supplicant.conf but recived a permission denied message.

```

sudo wpa_passphrase WIFISSID WPA2/PSKPASSWORD > /etc/wpa_supplicant.conf 

```

I was try to use nmcli command to make wifi connection this time I recived this error:

Error: Connection activation failed: (7) Secrets were required, but not provided.

```

mcnano@mc2gbnano:~$ sudo nmcli de wifi rescan
mcnano@mc2gbnano:~$ sudo nmcli de wifi
IN-USE  SSID                  MODE   CHAN  RATE        SIGNAL  BARS  SECURITY
        INIGMA                Infra  10    130 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2
        Emircan               Infra  4     270 Mbit/s  37      &#9602;&#9604;__  WPA2
        PiXEL_PLUS            Infra  7     130 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2
        Emircan               Infra  36    270 Mbit/s  37      &#9602;&#9604;__  WPA2
        FiberHGW_TP4AF2_5GHz  Infra  52    270 Mbit/s  34      &#9602;&#9604;__  WPA1 WPA2
        ibbWiFi               Infra  56    130 Mbit/s  27      &#9602;___  --
mcnano@mc2gbnano:~$ sudo nmcli device wifi connect WIFISSID password WPA/PSKPASSWORD

Error: Connection activation failed: (7) Secrets were required, but not provided.

```

[IMG]https://i.postimg.cc/tJZ764w3/error2.jpg[/IMG]

I was double check my router’s security settings (mac filter, mac authen etc.) everything is ok but still not connect.

I need to help to fix this problem.


PS: Sorry about my English.

---

### Post by mattis13 on 2020-12-05
I would try using nano and edit /etc/wpa_supplicant.conf (use: sudo nano) directly  
edit

  network={
    ssid="your_ssid_name"
    psk="your_password"
}

---

### Post by scpecialist on 2020-12-06
I solved this problem. Thank for your hep.
```

N='SSID'       #Your Wi-fi's SSID 
P='WPA/PSKPassword'   #Your Wi-fi's WPA/PSK Password 
D=$(LENG=C nmcli -t d | awk -F: '/wifi/{print $1}' | head -1)
(nmcli -f NAME -t c | grep -q "^$N") && nmcli con del "$N"

sudo systemctl restart NetworkManager

sudo nmcli con add con-name "$N" ifname "$D" type wifi autoconnect yes ssid "$N"

sudo nmcli con modify "$N" wifi-sec.key-mgmt wpa-psk
sudo nmcli con modify "$N" wifi-sec.psk "$P"
sudo nmcli connection up "$N"


```

connection check
```

nmcli d

DEVICE  TYPE      STATE        CONNECTION
wlan0   wifi      connected    SSID
l4tbr0  bridge    connected    l4tbr0
eth0    ethernet  unavailable  --

```

---

