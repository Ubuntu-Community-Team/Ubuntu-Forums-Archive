---
title: "Can't connect to home wireless network"
date: 2014-02-23
forum: Networking &amp; Wireless
---

### Post by David_Radcliffe on 2014-02-23
I have just installed Ubuntu 12.04.4 LTS (64 bit) on my notebook, and I am unable to connect to my home wireless network, although I am able to connect to other Wi-fi networks. My computer is a Lenovo IdeaPad P500, and my wireless card is Intel Corporation Centrino Wireless-N 2230 (rev c4). The wireless router is using WPA2-PSK network authentication and AES encryption. I do not wish to change the settings on the router since it is being used by other devices. Please let me know what other information I should include to resolve this issue.

---

### Post by praseodym on 2014-02-23
Deactivate the N-mode of the driver (bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by David_Radcliffe on 2014-02-23
When I enter the second line, I get the following error message:

```

$ sudo modprobe -rfv iwlwifi
FATAL: Module iwlwifi is in use.

```

---

### Post by praseodym on 2014-02-23
Reboot.

---

### Post by David_Radcliffe on 2014-02-23
Problem persists.:( Also tried removing iwldvm first, which allowed me to execute the suggested fix, but this did not resolve the issue.

---

### Post by praseodym on 2014-02-24
Please check the following router settings:
[LIST]
[*]Network not "hidden"
[*]Firmware up to date?
[*]Channel "fixed", not "auto"
[*]Encryption to pure "WPA2-AES (CCMP), not mixed mode
[*]Settings to a/b/g (or (b/g) instead of anything with "n"
[*]MAC address filter off
[/LIST]
Check the manual.

---

### Post by David_Radcliffe on 2014-02-24
Thanks for your help. I am now able to connect to my home wireless network, but I consider the issue still unresolved, since I need to be able to access other Wi-fi networks when I am away from home.  

EDIT: Problem was resolved by upgrading to Ubuntu 13.10 and installing all available updates.

---

