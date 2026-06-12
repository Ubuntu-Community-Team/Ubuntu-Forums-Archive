---
title: "wrong wep/wpa password how do I change it Ubuntu 5.11"
date: 2021-11-29
forum: Networking &amp; Wireless
---

### Post by RayGo75 on 2021-11-29
I moved the laptop that I run Ubuntu on to a different room in the house and in connecting to new access point I typed in the wrong password. Now every time I select that access point it never gives me a chance to type in the correct password. 

Attached is the output from the wireless info script.

Any and all help is appreciated.

---

### Post by chili555 on 2021-11-30
```
RAYGONET-5G-pro-2.4G  <MAC 'RAYGONET-5G-pro-2.4G' [AC4]>  Infra  6     2437 MHz  270 Mbit/s  85      &#9602;&#9604;&#9606;&#9608;  WPA2      no             
RAYGONET_2GEXT        <MAC 'RAYGONET_2GEXT' [AC1]>  Infra  8     2447 MHz  130 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2      yes     *      
RAYGONET              <MAC 'RAYGONET' [AC2]>  Infra  8     2447 MHz  130 Mbit/s  35      &#9602;&#9604;__  WPA2      no             
RAYGONET-Guest        <MAC 'RAYGONET-Guest' [AC3]>  Infra  8     2447 MHz  130 Mbit/s  32      &#9602;&#9604;__  WPA2      no             
SBG6900AC-5A6EE       <MAC 'SBG6900AC-5A6EE' [AC5]>  Infra  11    2462 MHz  195 Mbit/s  9       &#9602;___  WPA2      no             
```I assume it is one of these. 

The details, including the passwords, are stored in /etc/NetworkManager/system-connections. List them:

```
cd /etc/NetworkManager/system-connections && sudo ls
```

Delete the connection with the faulty stored password:

```
sudo rm faulty.nmconnection
sudo service NetworkManager restart
```

Of course, substitute your exact details here.

---

