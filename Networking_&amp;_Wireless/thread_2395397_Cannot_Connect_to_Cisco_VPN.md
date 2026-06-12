---
title: "Cannot Connect to Cisco VPN"
date: 2018-07-01
forum: Networking &amp; Wireless
---

### Post by albinary on 2018-07-01
Hello,
I am trying to connect to some CISCO VPN from Ubuntu 18.04 (which I connect ok from Windows). This is not anyConnect.
I installed using:
```

apt install vpnc network-manager-vpnc network-manager-vpnc-gnome


```
Now  I am able to configure the VPN connection(gateway, user/pass,  group/pass), even import the profile (.pcf) directly but I am not able  to connect to any of them. I try to turn them on and it turns off  automatically. No log, no error message, nothing at all.

Is there any client we can install as in Windows? 


Can you please give some idea how to troubleshoot/resolve.

---

### Post by raynermp on 2018-08-28
Have you tried openconnect?

```
sudo apt-get install --reinstall network-manager-openconnect network-manager-openconnect-gnome network-manager-vpnc network-manager-vpnc-gnome vpnc vpnc-scripts
```

---

