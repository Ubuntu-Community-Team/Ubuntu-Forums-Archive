---
title: "wpa_supplicant settings for secureW2"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by RottenBananas on 2008-08-24
Hey guys,

Im trying to get on my University's wireless network. They use secureW2
I've tried making a wpa_supplicant according to this site:
[http://ubuntuforums.org/showthread.php?t=869935&highlight=secureW2](http://ubuntuforums.org/showthread.php?t=869935&highlight=secureW2)

My wpa_supplicant.conf
```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
fast_reauth=1
network={
ssid="universitySSID"
key_mgmt=WPA-EAP
eap=TTLS
identity="myuserid"
password="mypassword"
priority=2
phase2="auth=PAP"
}

```

And then I run the following command after making sure my device is down
```
sudo wpa_supplicant -c /etc/wpa_supplicant.conf -i eth1 -D wext
```

When I try the command it associates and says```

CTRL-EVENT-EAP authentication started
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-METHOD EAP vendor 0 method 21 (TTLS) selected
CTRL-EVENT-EAP-FAILURE EAP authentication failed
```

Any Suggestions? Let me know if you need more info.

Thanks

---

### Post by RottenBananas on 2008-08-25
Anybody? Im gonna have to switch back to windows :(

---

### Post by RottenBananas on 2008-08-25
bump

---

