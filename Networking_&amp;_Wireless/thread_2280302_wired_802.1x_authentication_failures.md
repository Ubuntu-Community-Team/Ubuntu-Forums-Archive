---
title: "wired 802.1x authentication failures"
date: 2015-05-29
forum: Networking &amp; Wireless
---

### Post by Will_White on 2015-05-29
I have a desktop running 14.04 that is connected via ethernet to an enterprise 802.1x network. The connection was functional until today, when I had to change my domain password. I updated the password in wpa_supplicant.conf and rebooted. After restart, I was prompted for the 802.1x password, but the connection does not successfully authenticate and I get an endless loop of pop-up authentication requests. The password is entered correctly and I can connect to the same network on both Windows and Mac OS devices.

This error is reminiscent of the problem I had encountered when initially setting up this device, and that other [users have encountered]("http://ubuntuforums.org/showthread.php?t=2168015"), that was solved by deleting the line system-ca-certs=true from the config file in /etc/NetworkManager/system-connections. However, that can't be the problem now.

Here is the (redacted) contents of wpa_supplicant.conf:

```

[FONT=lucida console]ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
ap_scan=0
network={
key_mgmt=WPA-EAP
eap=PEAP
pairwise=CCMP TKIP
identity='[username]'
password='[password]'
phase2="auth=mschap2"
priority=2
}[/FONT]

```

And here is the contents of /etc/NetworkManager/system-connections/Wired connection 1:

```

[FONT=lucida console][802-3-ethernet]
duplex=full
mac-address=[redacted]

[connection]
id=Wired connection 1
uuid=[redacted]
type=802-3-ethernet
timestamp=1432224990

[ipv6]
method=auto

[802-1x]
eap=peap;
identity=[username]
ca-cert=[path_to_certificate]
phase2-auth=mschapv2
password-flags=1

[ipv4]
method=auto[/FONT]

```

Any suggestions?

Thanks,
Will

---

