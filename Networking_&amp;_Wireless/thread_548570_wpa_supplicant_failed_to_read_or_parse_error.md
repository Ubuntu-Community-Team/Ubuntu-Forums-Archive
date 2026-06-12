---
title: "wpa supplicant failed to read or parse error"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by Cypfer on 2007-09-11
when i try to run wpa-supplicant and specify the configuration file i get the following error:

```
Failed to read or parse configuration /etc/wpa_supplicant/wpa_supplicant.conf
```

this is the command that i run
```
wpa_supplicant -Dmadwifi -iath0 -c/etc/wpa_supplicant/wpa_supplicant.conf
```

my config file is as shown here

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=usergroup
update_config=1

network={
                  ssid="myssid"
                  key_mgmt=WPA-EAP
                  pairwise=TKIP
                  eap=PEAP
                  identity="myusername"
                  password="mypasswd"
                  phase1="peaplabe=0"
                  phase2="auth=MSCHAPV2"
}
network={
                 key_mgmt=NONE
}

```

and my network is setup as follows

ssid broadcasting is turned off
wpa authentication
data encryption of TKIP
eap type= protected EAP (PEAP)
authentication method EAP-MSCHAPV2
predefined user name and password

any help fixing the parse error or on how to connect to this network in ubuntu 6.10 would be appreciated.  I have tried using network monitor to connect but it does not work it keeps connecting to another network in the area that happens to be unsecured and free access. it connects to this other network even when i try to manually setup a connection to my network.

---

