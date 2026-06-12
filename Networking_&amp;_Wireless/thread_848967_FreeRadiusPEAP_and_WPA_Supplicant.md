---
title: "FreeRadius/PEAP and WPA Supplicant"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by metallica1973 on 2008-07-04
I have setup a freeRADIUS/PEAP server and all of my windows clients can login fine. I have been trying to use wpa_supplicant and have my Linux machines login. I think my wpa_supplicant.conf is setup ok( I think) and I still cannot login. From what I understand PEAP only needs certificates on the server side of things and that make sense because my windows machines can login so why cant I login using Linux? Here is my wpa_supplicant.conf

[PHP]# IEEE 802.1X with dynamic WEP keys using EAP-PEAP/MSCHAPv2

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="example 802.1x network"
        key_mgmt=IEEE8021X
        eap=PEAP
        phase2="auth=MSCHAPV2"
        identity="user name"
        password="password"
        ca_cert="/etc/cert/ca.pem"
}
[/PHP]

Help

---

### Post by kevdog on 2008-07-04
Would this post help???

[http://ubuntuforums.org/showpost.php?p=5309964&postcount=597](http://ubuntuforums.org/showpost.php?p=5309964&postcount=597)

---

### Post by metallica1973 on 2008-07-04
Another point I wanted to add is that I am using an older Cisco AP 1200. Could there be a setting on that I am missing?

---

